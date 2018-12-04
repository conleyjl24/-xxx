Hello-World
        @warn "Breakpoint mixin supports: iphone-x, iphone-xr, iphone-xs-max, iphone-x-all";
    }
}

   Hello-World
/*
Objects can have the following parameters:
    color: '#fff' by default
    impassable: true if it blocks the player from movement (false by default)
    onCollision: function (player, game) called when player moves over the object
    onPickUp: function (player, game) called when player picks up the item
    symbol: Unicode character representing the object
    type: 'item' or null
*/

// used by bonus levels 01 through 04
function moveToward(obj, type) {
    var target = obj.findNearest(type);
    var leftDist = obj.getX() - target.x;
    var upDist = obj.getY() - target.y;

    var direction;
    if (upDist == 0 && leftDist == 0) {
        return;
    }
    if (upDist > 0 && upDist >= leftDist) {
        direction = 'up';
    } else if (upDist < 0 && upDist < leftDist) {
        direction = 'down';
    } else if (leftDist > 0 && leftDist >= upDist) {
        direction = 'left';
    } else {
        direction = 'right';
    }

    if (obj.canMove(direction)) {
        obj.move(direction);
    }
}

// used by bonus levels 01 through 04
function followAndKeepDistance(obj, type) {
    var target = obj.findNearest(type);
    var leftDist = obj.getX() - target.x;
    var upDist = obj.getY() - target.y;

    if (Math.abs(upDist) < 2 && Math.abs(leftDist) < 4
        || Math.abs(leftDist) < 2 && Math.abs(upDist) < 4) {
        return;
    }
    var direction;
    if (upDist > 0 && upDist >= leftDist) {
        direction = 'up';
    } else if (upDist < 0 && upDist < leftDist) {
        direction = 'down';
    } else if (leftDist > 0 && leftDist >= upDist) {
        direction = 'left';
    } else {
        direction = 'right';
    }

    if (obj.canMove(direction)) {
        obj.move(direction);
    }
}

// used by bonus levels 01 through 04
function killPlayerIfTooFar(obj) {
    var target = obj.findNearest('player');
    var leftDist = obj.getX() - target.x;
    var upDist = obj.getY() - target.y;

    if (Math.abs(upDist) > 8 || Math.abs(leftDist) > 8) {
        obj._map.getPlayer().killedBy('"suspicious circumstances"');
    }
}

Game.prototype.getListOfObjects = function () {
    var game = this;
    return {
        // special

        'empty' : {
            'symbol': ' ',
            'impassableFor': ['raft']
        },

        'player' : {
            'symbol': '@',
            'color': '#0f0'
        },

        'exit' : {
            'symbol' : String.fromCharCode(0x2395), // ⎕
            'color': '#0ff',
            'onCollision': function (player) {
                if (game.map.finalLevel) {
                    game._moveToNextLevel();
                }
            }
        },

        // obstacles

        'block': {
            'symbol': '#',
            'color': '#999',
            'impassable': true
        },

        'tree': {
            'symbol': '♣',
            'color': '#080',
            'impassable': true
        },

        'mine': {
            'symbol': ' ',
            'onCollision': function (player) {
                player.killedBy('a hidden mine');
            }
        },

        'trap': {
            'type': 'dynamic',
            'symbol': '*',
            'color': '#f00',
            'onCollision': function (player, me) {
                player.killedBy('a trap');
            },
            'behavior': null
        },

        'teleporter': {
            'type': 'dynamic',
            'symbol' : String.fromCharCode(0x2395), // ⎕
            'color': '#f0f',
            'onCollision': function (player, me) {
                if (!player._hasTeleported) {
                    if (me.target) {
                        game._callUnexposedMethod(function () {
                            player._moveTo(me.target);
                        });
                    } else {
                        throw 'TeleporterError: Missing target for teleporter'
                    }
                }
                player._hasTeleported = true;
            },
            'behavior': null
        },

        // items

        'computer': {
            'type': 'item',
            'symbol': String.fromCharCode(0x2318), // ⌘
            'color': '#ccc',
            'onPickUp': function (player) {
                $('#editorPane').fadeIn();
                game.editor.refresh();
                game.map.writeStatus('You have picked up the computer!');
            },
            'onDrop': function () {
                $('#editorPane').hide();
            }
        },

        'phone': {
            'type': 'item',
            'symbol': String.fromCharCode(0x260E), // ☎
            'onPickUp': function (player) {
                game.map.writeStatus('You have picked up the function phone!');
                $('#phoneButton').show();
            },
            'onDrop': function () {
                $('#phoneButton').hide();
            }
        },

        'redKey': {
            'type': 'item',
            'symbol': 'k',
            'color': 'red',
            'onPickUp': function (player) {
                game.map.writeStatus('You have picked up a red key!');
            }
        },

        'greenKey': {
            'type': 'item',
            'symbol': 'k',
            'color': '#0f0',
            'onPickUp': function (player) {
                game.map.writeStatus('You have picked up a green key!');
            }
        },

        'blueKey': {
            'type': 'item',
            'symbol': 'k',
            'color': '#06f',
            'onPickUp': function (player) {
                game.map.writeStatus('You have picked up a blue key!');
            }
        },

        'yellowKey': {
            'type': 'item',
            'symbol': 'k',
            'color': 'yellow',
            'onPickUp': function (player) {
                game.map.writeStatus('You have picked up a yellow key!');
            }
        },

        'theAlgorithm': {
            'type': 'item',
            'symbol': 'A',
            'color': 'white',
            'onPickUp': function (player) {
                game.map.writeStatus('You have picked up the Algorithm!');
            },
            'onDrop': function () {
                game.map.writeStatus('You have lost the Algorithm!');
            }
        },

        // used by bonus levels 01 through 04
        'eye': {
            'type': 'dynamic',
            'symbol': 'E',
            'color': 'red',
            'behavior': function (me) {
                followAndKeepDistance(me, 'player');
                killPlayerIfTooFar(me);
            },
            'onCollision': function (player) {
                player.killedBy('"the eye"');
            },
        },

        // used by bonus levels 01 through 04
        'guard': {
            'type': 'dynamic',
            'symbol': 'd',
            'color': 'red',
            'behavior': function (me) {
                moveToward(me, 'player');
            },
            'onCollision': function (player) {
                player.killedBy('a guard drone');
            },
        }
    };
};
 @477447
/********************
 * crispsContest.js *
 ********************
 *
 * The Algorithm is almost in our grasp!
 * At long last, we will definitively establish
 * that 3SAT is solvable in polynomial time. It's
 * been a long, strange journey, but it will all be
 * worth it.
 *
 * You have the red, green, and blue keys. Now you
 * just need to figure out how to unlock this thing.
 */

function startLevel(map) {
    map.defineObject('redLock', {
        'symbol': String.fromCharCode(0x2297),
        'color': 'red',
        'impassable': function (player) {
            if (player.hasItem('redKey')) {
                player.removeItem('redKey');
                return false;
            } else {
                return true;
            }
        }
    });

    map.defineObject('blueLock', {
        'symbol': String.fromCharCode(0x2297),
        'color': '#06f',
        'impassable': function (player) {
            if (player.hasItem('blueKey')) {
                player.removeItem('blueKey');
                return false;
            } else {
                return true;
            }
        }
    });

    map.defineObject('greenLock', {
        'symbol': String.fromCharCode(0x2297),
        'color': '#0f0',
        'impassable': function (player) {
            if (player.hasItem('greenKey')) {
                player.removeItem('theAlgorithm');
                return false;
            } else {
                return true;
            }
        }
    });

    map.defineObject('yellowLock', {
        'symbol': String.fromCharCode(0x2297),
        'color': 'yellow',
        'impassable': function (player) {
            if (player.hasItem('yellowKey')) {
                player.removeItem('yellowKey');
                return false;
            } else {
                return true;
            }
        }
    });

    map.createFromGrid(
       ['  +++++ +++++  ',
        '  + b +++ r +  ',
        '  +   +E+   +  ',
        '+++G+B+ +R+G+++',
        '+ y B     R b +',
        '+   +     +   +',
        '+++++  @  +++++',
        '+   +     +   +',
        '+ y R     B y +',
        '++++++Y+Y++++++',
        '    +  +  +    ',
        '    + ABy +    ',
        '    +++++++    '],
    {
        '@': 'player',
        'E': 'exit',
        'A': 'theAlgorithm',
        '+': 'block',
        'R': 'redLock',
        'G': 'greenLock',
        'B': 'blueLock',
        'Y': 'yellowLock',
        'r': 'redKey',
        'g': 'greenKey',
        'b': 'blueKey',
        'y': 'yellowKey'
    }, 17, 6);
}

function validateLevel(map) {
    map.validateExactlyXManyObjects(1, 'exit');
    map.validateAtMostXObjects(1, 'theAlgorithm');
    map.validateAtMostXObjects(4, 'yellowKey');
    map.validateAtMostXObjects(2, 'blueKey');
    map.validateAtMostXObjects(1, 'redKey');
}

function onExit(map) {
    // make sure we have all the items we need!
    if (!map.getPlayer().hasItem('theAlgorithm')) {
        map.writeStatus("You must get that Algorithm!!");
        return false;
    } else if (!map.getPlayer().hasItem('computer')) {
        map.writeStatus("You'll need your computer! [Ctrl-5 to restart]");
        return false;
    } else if (!map.getPlayer().hasItem('phone')) {
        map.writeStatus("You'll need your phone! [Ctrl-5 to restart]");
        return false;
    } else {
        return true;
    }
}
 
 @477447
Daily UI #012 | E-commerce Shop (Single Item)
Here is a single item UI design for Nike Epic React Flyknit! All pink/pastel color scheme to match the rose color shoes! :) Hope you guys like it!

A Pen by Julie Park on CodePen.

License.
Keybase proof
I hereby claim:

I am donormal on github.
I am donormal (https://keybase.io/donormal) on keybase.
I have a public key ASB4gwRND0EgPRZ1zSAK_KvFVtUkmLEx8BNe8ndK3MkSbQo
To claim this, I am signing this object:

{
  "body": {
    "key": {
      "eldest_kid": "01207883044d0f41203d1675cd200afcabc556d52498b131f0135ef2774adcc9126d0a",
      "host": "keybase.io",
      "kid": "01207883044d0f41203d1675cd200afcabc556d52498b131f0135ef2774adcc9126d0a",
      "uid": "021fef0a4b683f17437499fd27090d19",
      "username": "donormal"
    },
    "merkle_root": {
      "ctime": 1543850045,
      "hash": "40b421a351739fd82f4abee13ef0572ce6e089b58e10efd30b633b10a54d4326539977446ceaf01da8590a49e55db13be89bbb02f7bb1e21a01a1b59a9860ea1",
      "hash_meta": "335f58290e41f4f36bb650d1930d62d8b30689cb3c6902f43138b5d4edd5260b",
      "seqno": 4044211
    },
    "service": {
      "entropy": "O9guaA9oVNqmEClad4Zp2OcO",
      "name": "github",
      "username": "donormal"
    },
    "type": "web_service_binding",
    "version": 2
  },
  "client": {
    "name": "keybase.io go client",
    "version": "2.10.1"
  },
  "ctime": 1543850050,
  "expire_in": 504576000,
  "prev": "31b3698c99d3ae6bd48106b27a1cea354893135adf8332e33e344a6c5a85dce4",
  "seqno": 5,
  "tag": "signature"
}
with the key ASB4gwRND0EgPRZ1zSAK_KvFVtUkmLEx8BNe8ndK3MkSbQo, yielding the signature:

hKRib2R5hqhkZXRhY2hlZMOpaGFzaF90eXBlCqNrZXnEIwEgeIMETQ9BID0Wdc0gCvyrxVbVJJixMfATXvJ3StzJEm0Kp3BheWxvYWTESpcCBcQgMbNpjJnTrmvUgQayehzqNUiTE1rfgzLjPjRKbFqF3OTEIAOV8P/zAvv0nrAsisDykcDfQQ3Tu1kgHPsP1GZk5iHpAgHCo3NpZ8RA1I7vueegacwJN9c184uUbHRSe7sf5Cx3Bdh0CNzwbiJmYzYPyyqVAoerBDfZ9TLxyb69KFdvJLHBkmpO4nz2DKhzaWdfdHlwZSCkaGFzaIKkdHlwZQildmFsdWXEICEVeMAITKOQSDIt0CCuJ5UfzMbbphGDvQSDJCZZxlefo3RhZ80CAqd2ZXJzaW9uAQ==

And finally, I am proving ownership of the github account by posting this as a gist.

My publicly-auditable identity:
https://keybase.io/donormal

From the command line:
Consider the keybase command line program.

# look me up
keybase id donormal
viktor@tn-vb:~$ netcat -C httpbin.org 80
GET /anything HTTP/1.1
Host: httpbin.org

HTTP/1.1 200 OK
Connection: keep-alive
Server: gunicorn/19.9.0
Date: Mon, 03 Dec 2018 15:09:52 GMT
Content-Type: application/json
Content-Length: 246
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true
Via: 1.1 vegur

{
  "args": {}, 
  "data": "", 
  "files": {}, 
  "form": {}, 
  "headers": {
    "Connection": "close", 
    "Host": "httpbin.org"
  }, 
  "json": null, 
  "method": "GET", 
  "origin": "94.198.216.18", 
  "url": "http://httpbin.org/anything"
}
GET /anything?foo=22&bar=hello&baz=world HTTP/1.1
Host: httpbin.org

HTTP/1.1 200 OK
Connection: keep-alive
Server: gunicorn/19.9.0
Date: Mon, 03 Dec 2018 15:10:43 GMT
Content-Type: application/json
Content-Length: 334
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true
Via: 1.1 vegur

{
  "args": {
    "bar": "hello", 
    "baz": "world", 
    "foo": "22"
  }, 
  "data": "", 
  "files": {}, 
  "form": {}, 
  "headers": {
    "Connection": "close", 
    "Host": "httpbin.org"
  }, 
  "json": null, 
  "method": "GET", 
  "origin": "94.198.216.18", 
  "url": "http://httpbin.org/anything?foo=22&bar=hello&baz=world"
}
viktor@tn-vb:~$ netcat -C httpbin.org 80
POST /anything HTTP/1.1
Host: httpbin.org
Content-Length: 26

foo=22&bar=hello&baz=world
HTTP/1.1 200 OK
Connection: keep-alive
Server: gunicorn/19.9.0
Date: Mon, 03 Dec 2018 15:13:46 GMT
Content-Type: application/json
Content-Length: 302
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true
Via: 1.1 vegur

{
  "args": {}, 
  "data": "foo=22&bar=hello&baz=world", 
  "files": {}, 
  "form": {}, 
  "headers": {
    "Connection": "close", 
    "Content-Length": "26", 
    "Host": "httpbin.org"
  }, 
  "json": null, 
  "method": "POST", 
  "origin": "94.198.216.18", 
  "url": "http://httpbin.org/anything"
}
 @477447
.block-region-second-below .block--basic .field--name-body ul {
  margin: 0px;
  padding: 0px;
  list-style: none;
  width: 230px;
}
<template>
    <div class="create-contact">
        <b-btn v-b-modal.id_create-contact-modal variant="primary">
            <translate>Adds a new contact</translate>
        </b-btn>
        <b-modal :title="$gettext('Adds a new contact')" id="id_create-contact-modal" size="lg" centered>
            <form :action="form_url" method="post" @submit.prevent="submitContact()" id="id_create-form">
                <div v-html="contact_form_html"></div>
                <button type="submit" class="btn btn-warning">
                    <translate>Add</translate>
                </button>
            </form>
        </b-modal>
    </div>
</template>
<script>
    import axios from "axios";
    // Loads bootstrap-vue
    import bModal from "bootstrap-vue/es/components/modal/modal";
    import bButton from "bootstrap-vue/es/components/button/button";
    // Loads CSS
    import 'bootstrap-vue/dist/bootstrap-vue.css';
    // Axios settings for CSRF tokens / POST request
    axios.defaults.xsrfHeaderName = "X-CSRFTOKEN";
    axios.defaults.xsrfCookieName = "csrftoken";
    Vue.directive("vue-modal", bModal);
    
    export default {
        name: "create-contact",
        components: {
            "b-modal": bModal,
            "b-btn": bButton
        },
        props: {
            debug: {
                default: false
            },
            capacity: {
                default: "ORGANIZER"
            },
            api_url: {
                default: "/events/api/contact/"
            },
            form_url: {
                default: "/events/form_api/contact/"
            },
        },
        data() {
            return {
                contact_form_html: {
                    default: ""
                }
            }
        },
        methods: {
            /**
             * Loads the form into the `contact_form_html` data attribute
             *
             * @returns Nothing
             */
            loadContactForm() {
                let vm = this;
                axios.get(vm.form_url).then(function (response) {
                    vm.contact_form_html = response.data.html;
                }).catch(function (error) {
                    vm.debug && console.debug('select-contact-list::loadContactForm Unable to get data from {form_url}: {error}', {
                        form_url: vm.form_url,
                        error: error
                    });
                });
            },
            /**
             * Submit contact data to the server, adding the `capacity` field to the POST
             *
             */
            submitContact() {
                let vm = this;
                let form = document.getElementById("id_create-form");
                let data = new FormData(form);
                // Adds capacity to payload
                data.append("capacity", vm.capacity);
                vm.debug && console.log(data);
                // Post Data
                axios.post(
                    vm.api_url,
                    data
                ).then(function (response) {
                        // Notify parent to reload...
                        console.log(response);
                        vm.$parent.updateContacts();
                    }
                ).catch(function (error) {
                    console.log(error);
                });
            }
        },
        mounted: function() {
            this.loadContactForm();
        }
    }
</script>


<style scoped>
</style>
#include <iostream>
using namespace std;

int main()
{
	int  a,b;
	float x;
	cout<<"Nhap a,b:"<<endl;
	cin>>a>>b;
	x=(float)-b/a;
	if (a==0)
	{
		if(b==0) cout<<"Phuong trinh co vo so nghiem "<<endl;
		else cout<<"Phuong trinh vo nghiem "<<endl;
	}
	else cout<<"Nghiem cua phuong trinh la: "<<x<<endl;
	return 0;
}
// Process Block-Scopes prefixed with an Expression / Vaiable.

// Motivation:
//  Often, a language feature is based on a principle of repeately applying logic to the same refference.
//  Examples are switch-like statements - applying the '===' operator, 
// 					 and the pipe operator - applying custom logic in a chain.

// The base for this concept is the scope injection operator '( ... )' that injects a literal into a block '{ ... }'

// Syntax:
(<literal>) {
  <statements>
}

// Short Syntax:
<literal> -> <statements>

 
// Rules:

//  0. A single literal must be provided

//  1. The undefinde literal is not injected
(undefined) {
  statement // Never Executes
}


//  2. The first unknown identifier is a refference to the injected literal
(literal) {
  X
  Y       // ReferenceError
}

//  3. The injected literal can only be catched at the root of the block - if not assigned to const or let
(literal) {
  X
  if(true) {
    X         // ReferenceError
  }
}

(literal) {
  const Y
  if(true) {
    Y
  }
}


//  4. The last expression in the block resolves the block
(literal) { X } === literal

const X = true
(literal) { X } === X            // `X` is known and resolves
(literal) { Y } === literal      // `Y` ia unknown becomes `literal` and resolves


//  5. Parenthesis are optional
literal { Y }


//  6. Injection and block may be seperated by an arrow sign (->)
literal -> Y




// The injection operator injects a single literal into the associated block-scope

(literal) {
  
  log(A)                      // The first unknown identifier is a refference to the injected literal
  
  const A                     // Assignes `literal` to ´A` - makes `A` available in nested scopes
  
  const { A, B }              // Implementation with deconstruction
  
  Math.sin(A)                 // The last expression resolves
  
  
  // Nested Scopes
  // Nested injections are executed from outer to inner, and resolved from inner to outer
  
  Math.PI * A {
    Math.sin(A) {
      Math.asin(A)
    }
  }
  
  
  // Pattern Mathing
  
  match 'θ' {                   // `match` resolves to `undefined` if no match
    logGreek(G)                 // Due to rule 2. this block wont be executed if (literal !== 'θ')
  }
  
  match { A: 'α', B: 'β' } {    // Advanced pattern matching
    into { A, B }
    log(A, B)
  }
  
}

'Ω' -> print(_)

const piped = 'Ω' -> toLatin(_) -> toLowerCase(_) -> color(_, 'red')

if({ A: 'α', B: 'β' } -> match {A: 'a'}) {
  log('isLatin')
}
 examples.js
let angle = Math.PI / 2

angle {
	x {
		Math.sin(x)
	}
	
	// Further Nesting //
	x {
		into Math.sin(x) {
			Math.arcsin(y)		// First Unknown Identifier: must be injected literal
		}
	}
	
	
	into x -> Math.sin(x)
	
	into x -> Math.sin(x) -> Math.arcsin(x)
}

angle -> x -> Math.sin(x) -> Math.arcsin(x)

angle -> Math.sin(x) -> Math.arcsin(x)


subscribe('onEvent') -> {
	log(e)
}

subscribe('onEvent') -> e {
	log(a)
	log(e)		// ReferenceError
}

subscribe('onEvent') -> e => {
	log(a) 		// ReferenceError
	log(e)
}

async function subscribe(eventId) {
	await ExternalAPI.get(eventId)
	
	resolveCallback(eventId)
	return createEvent(eventId)
}
/********************
 * theLongWayOut.js *
 ********************
 *
 * Well, it looks like they're on to us. The path isn't as
 * clear as I thought it'd be. But no matter - four clever
 * characters should be enough to erase all their tricks.
 */

function startLevel(map) {
    map.placePlayer(7, 5);

    var maze = new ROT.Map.DividedMaze(map.getWidth(), map.getHeight());
/*
    maze.create( function (x, y, mapValue) {
        // don't write maze over player
        if (map.getPlayer().atLocation(x,y)) {
            return 0;
        }
        else if (mapValue === 1) { //0 is empty space 1 is wall
            map.placeObject(x,y, 'block');
        }
        else {
            map.placeObject(x,y,'empty');
        }
    });
    map.placeObject(map.getWidth()-4, map.getHeight()-4, 'block');
    map.placeObject(map.getWidth()-6, map.getHeight()-4, 'block');
    map.placeObject(map.getWidth()-5, map.getHeight()-5, 'block');
    map.placeObject(map.getWidth()-5, map.getHeight()-3, 'block');
*/
    map.placeObject(map.getWidth()-5, map.getHeight()-4, 'exit');
}
 
/******************
 * minesweeper.js *
 ******************
 *
 * So much for Asimov's Laws. They're actually trying to kill
 * you now. Not to be alarmist, but the floor is littered
 * with mines. Rushing for the exit blindly may be unwise.
 * I need you alive, after all.
 *
 * If only there was some way you could track the positions
 * of the mines...
 */

function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

function startLevel(map) {
    for (x = 0; x < map.getWidth(); x++) {
        for (y = 0; y < map.getHeight(); y++) {
            map.setSquareColor(x, y, '#f00');
        }
    }

    map.placePlayer(map.getWidth() - 5, 5);

    for (var i = 0; i < 75; i++) {
        var x = getRandomInt(0, map.getWidth() - 1);
        var y = getRandomInt(0, map.getHeight() - 1);
        if ((x != 2 || y != map.getHeight() - 1)
            && (x != map.getWidth() - 5 || y != 5)) {
            // don't place mine over exit or player!
            map.placeObject(x, y, 'mine');
            map.setSquareColor(x,y,'#000');
        }
    }

    map.placeObject(2, map.getHeight() - 1, 'exit');
}

function validateLevel(map) {
    map.validateAtLeastXObjects(40, 'mine');
    map.validateExactlyXManyObjects(1, 'exit');
}
 
 @477447
/*IMPORTS GO HERE*/

// The functional component of our index page
const IndexPage = (props) => {
  // Getting the data
  const notes = props.data.allMarkdownRemark;
  // Grouping based on the slug - the first part being the subject
  const subjects = _.chain(notes.edges)
    .groupBy(node => node.node.fields.slug.split('/')[1])
    .map(node => node) 
    .value();

  // Mapping over the 'subjects' and each node within and generating links to the pages
  return (
    <Layout>
        <h2 style={{textAlign: 'center', fontFamily: 'courier, monospace'}}>Subjects</h2>
        <Accordion>
        {subjects.map((arr, i) => (
          <AccordionItem key={arr[0].node.fields.slug.split('/')[1]}>
            <AccordionItemTitle>{arr[0].node.fields.slug.split('/')[1].toUpperCase()}</AccordionItemTitle>
            {arr.map(({ node }, j) => (
              <AccordionItemBody key={node.frontmatter.title}>
                <Link to={node.fields.slug} className="link" >
                  <div className="post-list">
                    {node.frontmatter.title}
                  </div>
                </Link>
              </AccordionItemBody>
          ))}
          </AccordionItem>
        ))}
        </Accordion>
    </Layout>
  )
}

export default IndexPage

// The graphql query that generates the data we need
export const query = graphql`
  query ListQuery {
    allMarkdownRemark(sort: { order: DESC, fields: [frontmatter___date] }) {
      edges {
        node {
          fields {
            slug
          }
          frontmatter {
            title
          }
        }
      }
    }
  }
`;
# your code goes here
# 数字が回文になるので2進数の1桁目は1
# つまり10進すうでは奇数なので2ずつ増加させている
num = 11
while True:
    int_str = str(num)
    bin_str = bin(num)
    oct_str = oct(num)
    if int_str == int_str[::-1] and bin_str == bin_str[::-1] and oct_str == oct_str[::-1]:
        print(num)
        break
    else:
        num += 2
// layouts/default.js
import React from 'react'
import Meta from '../components/meta'
import Navbar from '../components/navbar'
export default ({ children, meta }) => (
  <div>
    <Meta props={meta} />
    <Navbar />
    { children }
  </div>
)
function decodeHtml(html) {
    var txt = document.createElement("textarea");
    txt.innerHTML = html;
    console.log(txt.value);
    return txt.value;
}

Set Implicit Arguments.

Inductive vector (X : Type) : nat -> Type :=
  | vnul : vector X 0
  | vcons {n : nat} (h : X) (v : vector X n) : vector X (S n).
   Arguments vnul [X].

Definition vhd (X : Type) n (v : vector X (S n)) : X :=
  match v with
  | vcons _ h _ => h
  end.

Definition vtl (X : Type) n (v : vector X (S n)) : vector X n :=
  match v with
  | vcons _ _ tl => tl
  end.

Fixpoint vpadd {n : nat} (v1 v2 : vector nat n) : vector nat n :=
  match v1 in vector _ n return vector nat n -> vector nat n with
  | vnul =>           fun _  => vnul
  | vcons _ x1 v1' => fun v2 => vcons (x1 + vhd v2) (vpadd v1' (vtl v2))
  end v2.
 /********************
 * theLongWayOut.js *
 ********************
 *
 * Well, it looks like they're on to us. The path isn't as
 * clear as I thought it'd be. But no matter - four clever
 * characters should be enough to erase all their tricks.
 */

function startLevel(map) {
    map.placePlayer(7, 5);

    var maze = new ROT.Map.DividedMaze(map.getWidth(), map.getHeight());

    maze.create( function (x, y, mapValue) {

        // don't write maze over player
        if (map.getPlayer().atLocation(x,y)) {
            return 0;
        }

        else if (mapValue === 1) { //0 is empty space 1 is wall
            map.placeObject(x,y, 'block');
        }
        else {
            map.placeObject(x,y,'empty');
        }
    });

    map.placeObject(map.getWidth()-4, map.getHeight()-4, 'block');
    map.placeObject(map.getWidth()-6, map.getHeight()-4, 'block');
    map.placeObject(map.getWidth()-5, map.getHeight()-5, 'block');
    map.placeObject(map.getWidth()-5, map.getHeight()-3, 'block');
map.placeObject(map.getWidth()-7, map.getHeight()-4, 'exit');
    map.placeObject(map.getWidth()-5, map.getHeight()-4, 'exit');
}
 <!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>
        Bonkers
    </body>
</html>

 

# So the program is typed or not did not understand
#!/bin/bash 

# to unmount, use 
#   fusermount -uz $HOME/JBDS-ssh
#   fusermount -uz $HOME/TOOLS-ssh

# requires that you define variables like this
# export TOOLS=user@server_or_IP:/path/to/mount
# export JBDS=user2@server_or_IP:/path2/to/mount

# mount network drives over ssh

WORKSPACE=${HOME}
sshmount ()
{
	# RHDS WONKA
	if [[ ! $1 ]] || [[ $1 == "   " ]]; then mounts="TOOLS JBDS "; else mounts=$1; fi

	for mnt in $mounts; do 
	  mkdir -p ${WORKSPACE}/${mnt}-ssh
	  if [[ $(file ${WORKSPACE}/${mnt}-ssh 2>&1) == *"Transport endpoint is not connected"* ]]; then 
	  	echo "Unmount: ${WORKSPACE}/${mnt}-ssh"; fusermount -uz ${WORKSPACE}/${mnt}-ssh
	  fi
	  if [[ ! "$(ls -A ${WORKSPACE}/${mnt}-ssh)" ]]; then 
	  	echo "Mount: ${WORKSPACE}/${mnt}-ssh"; sshfs ${!mnt} ${WORKSPACE}/${mnt}-ssh
	  else 
	  	echo "Already mounted: ${WORKSPACE}/${mnt}-ssh"
	  fi
	done
}


if [[ $UID != 0 ]]; then
	sshmount "$1 $2 $3 $4"
	# if you get "fuse: failed to open /dev/fuse: Permission denied"
	# AS ROOT: you can chgrp YOUR_USER /dev/fuse; chmod g+rw /dev/fuse
elif [[ $UID = 0 ]]; then
	chgrp $USER /dev/fuse; chmod g+rw /dev/fuse
	echo "Do not run as root!"
	exit 1
fi
 @477447
public static void saveCityList(List<City> cities, Context context, String key){
        SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
        SharedPreferences.Editor editor = preferences.edit();
        Gson gson = new Gson();
        String json = gson.toJson(cities);
        editor.putString(key, json);
        editor.apply();
    }
    
/**
  * Targetting iPhone X Series of Smartphones
  *
	*/

$iphone-x-main-nav-height: 80px;
$iphone-x-main-nav-padding: calc(#{$iphone-x-main-nav-height} / 2);
$iphone-x-header-height: $header-height;
$iphone-x-height-offset: $iphone-x-main-nav-height + $iphone-x-header-height;
$iphone-x-content-area: calc(100vh - #{$iphone-x-height-offset});

/**
  * Media Query Mixin
  * Current $device's: 'iphone-x', 'iphone-xr', 'iphone-xs-max', 'iphone-x-all'
  * We can add more breakpoints by adding them to the $devices list below
  *
  * Example usage:
  * @include breakpoint(iphone-x-all) { @content }
  *
  */

$iphone-x-device-width: 375px;
$iphone-x-device-height: 812px;
$iphone-x-webkit-device-pixel-ratio: 3;

$iphone-xr-device-width: 414px;
$iphone-xr-device-height: 896px;
$iphone-xr-webkit-device-pixel-ratio: 2;

/*
 * iPhone XS matches iPhone X query
 * Ref: https://stackoverflow.com/a/52321213
 *
 */

$iphone-xs-max-device-width: 414px;
$iphone-xs-max-device-height: 896px;
$iphone-xs-max-webkit-device-pixel-ratio: 3;

@mixin breakpoint($device) {
    @if $device == iphone-x {
        @media only screen and (device-width: $iphone-x-device-width) and (device-height: $iphone-x-device-height) and (-webkit-device-pixel-ratio: $iphone-x-webkit-device-pixel-ratio) {
            @content;
        }
    }

    @if $device == iphone-xr {
        @media only screen and (device-width: $iphone-xr-device-width) and (device-height: $iphone-xr-device-height) and (-webkit-device-pixel-ratio: $iphone-xr-webkit-device-pixel-ratio) {
            @content;
        }
    }

    @if $device == iphone-xs-max {
        @media only screen and (device-width: $iphone-xs-max-device-width) and (device-height: $iphone-xs-max-device-height) and (-webkit-device-pixel-ratio: $iphone-xs-max-webkit-device-pixel-ratio) {
            @content;
        }
    }

    @if $device == iphone-x-all {
        @media only screen and (device-width: $iphone-x-device-width) and (device-height: $iphone-x-device-height) and (-webkit-device-pixel-ratio: $iphone-x-webkit-device-pixel-ratio), only screen and (device-width: $iphone-xr-device-width) and (device-height: $iphone-xr-device-height) and (-webkit-device-pixel-ratio: $iphone-xr-webkit-device-pixel-ratio), only screen and (device-width: $iphone-xs-max-device-width) and (device-height: $iphone-xs-max-device-height) and (-webkit-device-pixel-ratio: $iphone-xs-max-webkit-device-pixel-ratio) {
            @content;
        }
    }
    @else {
        // If you add more '@if else $device's be sure to update warn
        @warn "Breakpoint mixin supports: iphone-x, iphone-xr, iphone-xs-max, iphone-x-all";
    }
}
#include "lfs.h"
#include "lfs_emubd.h"

// variables used by the filesystem
lfs_t lfs;
lfs_file_t file;
lfs_emubd_t emu;

// configuration of the filesystem is provided by this struct
struct lfs_config cfg = {
    // block device operations
    .read  = lfs_emubd_read,
    .prog  = lfs_emubd_prog,
    .erase = lfs_emubd_erase,
    .sync  = lfs_emubd_sync,

    // block device configuration
    .read_size = 16,
    .prog_size = 16,
    .block_size = 4096,
    .block_count = 128,
    .lookahead = 128
};

// entry point
int main(void) {
	cfg.context = &emu;

	lfs_emubd_create(&cfg, "blocks");

    // mount the filesystem
    int err = lfs_mount(&lfs, &cfg);

    // reformat if we can't mount the filesystem
    // this should only happen on the first boot
    if (err) {
        lfs_format(&lfs, &cfg);
        lfs_mount(&lfs, &cfg);
    }

    // read current count
    uint32_t boot_count = 0;
    lfs_file_open(&lfs, &file, "boot_count", LFS_O_RDWR | LFS_O_CREAT);
    lfs_file_read(&lfs, &file, &boot_count, sizeof(boot_count));

    for (int i = 0; i < 10; i++)
    {
		printf("writing %d\n", i);

		// update boot count
		boot_count += 1;
		lfs_file_rewind(&lfs, &file);
		lfs_file_write(&lfs, &file, &boot_count, sizeof(boot_count));
		lfs_file_sync(&lfs, &file);
    }

    // remember the storage is not updated until the file is closed successfully
    lfs_file_close(&lfs, &file);

    // release any resources we were using
    lfs_unmount(&lfs);

    // print the boot count
    printf("boot_count: %d\n", boot_count);
}

 @477447
 

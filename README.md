Hello-World
 <Window x:Class="OpenWindow.MainWindow"
         xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
         xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:local="clr-namespace:OpenWindow"
         mc:Ignorable="d"
         Title="MainWindow" Height="450" Width="800">
      <Grib>
          <Button
               Content="OpenWindow"
               HorizontalAlignment="Center"
               VerticalAlignment="Center"
               Width="90"
               Click="Button_Click"/>
       </Grib>
   </Window>
   
.md

  FROM goland
  
  ENV GO111MODULE=on
  
  WORKDIR /app
  
  COPY go.mod .
  COPY go.sum .
  
  RUN go mod download
  
  COPY . .
  
  RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build
  
  EXPOSE 8080
  ENTRYPOINT ["/app/tttpserver"]

 i686-linux    kube-router
 x86_64-linux  kube-router
 aarch64-linux kube-router
 
jekyll

 
 
   "script": {
   "test": "echo \"Error: no test specified\" && exit 1",
   "start": "node server.js",
   "server": "nodemon server.js"
   },
# Authentication

There are three ways to authenticate through GitHub API v3.Reguests that reguire authentication will
return 404 Not Found instead of 403 Forbidden in some places.This is to prevent the accidental
leakage of private repositories to unauthorized users.

Summary representations

When you fetch a list of resources, the reponse includes a subset of the attributes for that resource.
This is the "summary" representation of the resource.(Some attributes are computationally expensive

for the API to provide. For performance reasons, the summary representation excludes those attributes.
To obtain those attributes.fetch the detailed representation.)

# Example:When you get a list of repositories you get the summary representation of each repository.
Here we fetch the list of repositories owned by the octokit organization:

# Detailed representations

When you fetch an individual resource the response typically includes all attributes for that resource.
This is the detailed representation of the resource.(Note that authorization sometimes influences the

amount of detail included in the representation)

# Example:When you get an individual repository, you get the detailed representation of the repository
Here we fetch the octokit.rd repository:

# Accept

HTTP redirects

API v3 uses HTTP redirection where appropriate.Clients should assume that any reguest may result in a
redirection.Receiving an HTTP redirection is not an error and clients should follow that redirect.Redirect a

responses will have a Location header fieled which contains the URI of the resource to which the client
should repeat the reguests.

Pagination

Reguests that return multiple items will be paginated to 30 items by default.You can specify further
pages with the ?page parameter.For some resources you can also set a custom page size up to 100

with the ?per_page parameter.Note that for technical reasons not all endpoints respect the ?per_page
parameter,see events for example.

Accept

Get a single grant
GET /applications/grants/:grants_id

# Response
Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/applications/grants/1",
  "app": {
    "url": "http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
   },
   "created_at"": "2011-09-06T17:26:27Z",
   "updated_at":  "2011-09-06T20:39:23Z",
   "scopes": [
     "public_repo"
   ]
 }
 Accept
 Example
 
 This example removes two of three assignees leaving octocat assignee.
 {
 "assignees": [
   "hubot",
   "other_user"
 ]
}

Accept
Get a single grant
GET /applications/grant_id

Response
Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/applications/grants/1",
  "app": {
    "url": "http://my-github-com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
    },
    "created_at": "2011-09-06T17:26:27Z",
    "updated_at": "2011-09-06T20:3923Z",
    "scopes": [
      "public_repo"
    ]
  }
Accept

Check runs and check suites API

Allows a GitHub App to run external checks on a repository's code.See the Check runs and Check suites
APIs for more details.

Custom media type:antiope-preview #Announced:2018-05-07

Project card details
The RESR API v3 responses for issue events and issue timeline events now return the project_card field
for project-related events.

# Custom media type: starfox-preview Announced: 2018-12-09

GitHub App Manifests
GitHub App Manifests allow people to create preconfigured GitHub Apps.See "Creating GitHub Apps
from a manifest" for more details.

# Custom media type: fury-preview

Doployment statuses
You can now update the environment of a deployment status and use the in_progress and gueued
states.When you create deployment statuses you can nowuse the auto_inactive parameter to mark

old production deployments as inactive
# Custom media type: flash-preview Announced: 2018-12-09

Repository creation permissions

You can now configure whether organization members can create repositories and which types of
repositories they can create.See "Edit an organization" for more details

# Custom media types:surtur-preview

Accept
# Response
Status: 200 OK
Link: <https://api.github.com/resource?page=2>; rel="next",
      <https://api.github.com/resource?page=5>; rel="last"
      
[
  {
    "id": 1,
    "ur1": https://api.github.com/applications/grants/1",
    "app": {
      "url": "http://my-github-app.com",
      "name": "my github app",
      "client_id": "abcde12345fghij67890"
    },
    "created_at": "2011-09-06T17:26:27Z",
    "updated_at": "2011-09-06T20:39:23Z",
    "scopes": [
      "public_repo"
    ]
  }
]

Accept
# Response if returning a new token
Status: 201 Created
Location: https://api.github.com/authorizations/1

{
  "id": 1,
  "url": "https://api.github.com/authorizations/1",
  "scopes": [
     "public_repo"
  ],
  "token": "abcdefgh12345678",
  "token_last_eight": "12345678",
  "hashed_token": "25f94a2a5c7fbaf499c665bc73d67c1c87e496da8985131633ee0a95819db2e8",
  "app": {
    "url": "http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
  },
  "note": "optional note",
  "note_url": "http://optional/note/url",
  "updated_at": "2011-09-06T20:39:23Z",
  "created_at": 2011-09-06T17:26:27Z",
  "fingerprint": ""
 }
Accept
{
  "message": "Reguires authetication",
  "documentatation_url": "https://developer.github.com/v3"
}
Accept
send real money on my e-mail and that there was real money without investments of my means
and that there was displayed about $1000

-fingerprint-Get a single grant
-fingerprint-GET /applications/:grant_id
-fingerprint-Response
-fingerprint-Status: 200 OK
-fingerprint-{
-fingerprint-  "id": 1,
-fingerprint-  "url": "https://api.github.com/applications/grants/1",
-fingerprint-  "app": {
-fingerprint-    "url": "http://my-github-app.com",
-fingerprint-    "name": "my github app",
-fingerprint-    "client_id": "abcde12345fghij67890"
-fingerprint-  },
-fingerprint-  "created_at": "2011-09-06T17:26:27Z",
-fingerprint-  "updated_at": "2011-09-06T20:39:23Z",
-fingerprint-  "scopes": [
-fingerprint-    "public_repo"
-fingerprint-  ]
-fingerprint- }

-fingerprint-{
-fingerprint-  "message": "Reguires authentication",
-fingerprint-  "documentation_url": "https://developer.github.com/v3"
             }
-fingerprint
-string
-PATCH /authorizations/:authorization_id
{
  "add_scopes": [
    "repo"
   ],
   "note": "admin script"
 }

PUT /authorizations/client_id/:fingerprint
client_secret-{
client_secret-"client_secret": "abcdabcdabcdabcdabcdabcdabcdabcdabcdabcd",
client_secret-"scopes": [
client_secret-  "public_repo"
client_secret-  ],
client_secret-  "note": "admin script"
client_secret-}

gingrprint

Status: 200 OK
Link: <https://api.github.com/resource?page=2>; rel="next",
      <https://api.github.com/resource?page=5>; rel="last"
      
[
   {
     "id": 1,
     "url": "https://api.github.com/applications/grants/1",
     "app": {
       "url": "http://my-github-app.com",
       "name": "my github app",
       "client_id": "abcde12345fghij67890"
     },
     "created_at": "2011-09-06T17:26:27Z",
     "updated_at": "2011-09-06T20:39:23Z",
     "scopes": [
       "public_repo"
     ]
   }
 ]
 
client_secret-{
client_secret-  "message": "Reguires authentication",
client_secret-  "documentation_url": "https://developer.github.com/v3"
client_secret-}

fingrprint
client_secret-create-such-client_secret-code-that it-client_secret-worked-in-programs-antivirus-for-example-Avast-or-ESET
client_secret-or-other-antivir-client_secret-programs-you-can-client_secret-take-from-the-database-so-this-code
client_secret-worked-there-in-the-software

fingerprint

GET /applications/grants/:grant_id

Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/applications/grants/1",
  "app": {
    "url": http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
  },
  "created_at": 2011-09-06T17:26:27Z",
  "updated_at": "2011-09-06T20:39:23Z",
  "scopes": [
     "public_repo"
   ]
 }
fingrprint

  class CreationUserEventDate
  {
         decimal UserPk { get; set; }
         string UserLogin { get; set; }
         Guid? UserUxid { get; set; }
         string UserType { get; set; }
  }
  
app_id   integer

{
    "auto_trigger_checks": [{
        "app_id": 4,
        "setting": false
     }]
}

#Auto detect text filles and perform LF normalization
* text-auto

# Build and Release Folders
bin-debug/
bin-release/
[Oo]bj/
[Bb]in/

# other files and folders
settings/

# Executables
*.swf
*.air
*.ipa
*.apk

# project files, i.e. project , .actionScriptproperties and .flexProperties
# should NOT be excluded as they contain compiler settings and other important
# information for Eclipse / Flash Builder.

fingrprint

GET /applications/grants/:grant_id
Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/applications/grants/1",
  "app": {
    "url": "http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
  },
  "created_at": "2011-09-06T17:26:27Z",
  "updated_at": "2011-09-06T20:39:23Z",
  "scopes": [
    "public_repo"
  ]
}
GET /applications/:grant_id
Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/applications/grants/1",
  "app": {
    "url": "http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
   },
   "created_at": "2011-09-06T17:26:27Z",
   "updated_at": "2011-09-06T20:39:23Z",
   "scopes": [
     "public_repo"
   ]
 }
 
  "documentation url": "https://developer.github.com/v3/#rate-limiting"
}
GET /authorizations
Status: 200 OK
Link: <https://api.github.com/resource?page=2>; re1="next",
      <https://api.github.com/resource?page=5>; rel="last"

fingrprint
GET /repos/:owner/:repo/topics
Status: 200 OK
{
  "names": [
    "octocat",
    "atom",
    "electron",
    "API"
  ]
}
Accept
# Personal access tokens

Tokens you have generated that can be used to access the GitHub API.

<<'kolorado-subscribers 100000'>>-admin:gpg_key,admin:org, adnin:org_hook,
admin:public_key, admin:repo_hook,delete_repo,gist'notifications,repo,user,write:discussion
Personal access tokens function like ordinary OAuth access tokens.They can be used instead of a password for Git over HTTPS,or can be
used to authenticate to the API over Basic Authentication.
0ffafda7b12087a2bdac596f189c94f6008e9e78

fingrprint
GET /applications/:client_id/tokens/:access_token
Status: 200 OK
{
  "id": 1,
  "url": "https://api.github.com/authorizations/1",
  "scopes": [
    "public_repo"
  ],
  "token": "abcdefgh12345678",
  "token_last_eight": "12345678",
  "hashed_token": "25f94a2a5c7baf499c665bc73d67c1c87e496da8985131633ee0a95819db2e8",
  "app": {
    "url": "http://my-github-app.com",
    "name": "my github app",
    "client_id": "abcde12345fghij67890"
  },
  "note": "optional note",
  "note_url": "http://optional/note/url",
  "updated_at": "2011-09-06T20:39:23Z",
  "created_at": "2011-09-06T17:26:27Z",
  "fingerprint": "jklmnop12345678",
  "user": {
    "login": "octocat",
    "id": 1,
    "node_id": "MDQ6VXN1cjE=",
    "avatar_url": "https://github.com/images/error/octocat_happy.gif",
    "gravatar_id": "",
    "url":: "https://api.github.com/users/octocat",
    "html_url": "https://github.com/octocat",
    "followers_url": "https://api.github.com/users/octocat/followers",
    "following_url": "https://api.github.com/users/octocat/following{/other_user}",
    "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
    "organizations_url": "https://api.github.com/users/octocat/orgs",
    "repos_url": "https://api.github.com/users/octocay/repos",
    "events_url": "https://api.github.com/users/octocat/events{/privacy}",
    "recaivad_events_url": "https://api.github.com/users/octocat/receivad_events",
    "type": "User",
    "site_admin": false
  }
}
0ffafda7b12087a2bdac596f189c94f6008e9e78
Accept
application/vnd.github.hellcat-preview+json
GET /orgs/:org/teams
Status: 200 OK
Link: <https://api.github.com/resource?page=2>; rel="next",
      <https://api.github.com/resource?page=5>; rel="last"
[
  {
    "id": 1,
    "node_id": "MDQ6VGVhbTE=",
    "url": "https://api.github.com/teams/1",
    "name": "Justice League",
    "slug": "Justice-league",
    "description": "A great team.",
    "privacy": "closed",
    "permission": "admin",
    "members_url": "https://api.github.com/teams/1members{/member}",
    "repositories_url": "https://api.github.com/teams/1/repos",
    "parent": null
  }
]
Accept
Send $100 as a condensation site 477447 for contributions to the repository and for having
stolen money from this site!

# INTRODUCTION

Under the cover of all the sacred and mystical allegories of the ancient teachings, through the darkness and strange trials of
allinitions, underthe coverof all thescriptures in the ruins of Nineveh and Thebes on time-eaten stonesof ancient temples

on the blackened faceof the sphinxes of Assyria and Egypt in monstrous or miraculous drawings translating for the believers of india the sacred pages of the Vedas in the strange emblems of our old alchemical books, in the initiation ceremonies practiced byall mysterious

societies-everywhere we find traces of doctrine, everywhere ety, and everywhere carefully conceales...Apparently, the secret
philosophy was the nurse or godmother of all religions, the secret lever of all intellectual forces, the key to all divine
darknesses and the absolute gueen of society in those times when her only purpose was to educate high priests and kings.
#                  Accept
[
  {
    "login": "myhduck",
    "id": 1555350,
    "node_id": "MDQ6VXNlcjE1NTUzNTA=",
    "avatar_url": "https://avatars2.githubusercontent.com/u/1555350?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/myhduck",
    "html_url": "https://github.com/myhduck",
    "followers_url": "https://api.github.com/users/myhduck/followers",
    "following_url": "https://api.github.com/users/myhduck/following{/other_user}",
    "gists_url": "https://api.github.com/users/myhduck/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/myhduck/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/myhduck/subscriptions",
    "organizations_url": "https://api.github.com/users/myhduck/orgs",
    "repos_url": "https://api.github.com/users/myhduck/repos",
    "events_url": "https://api.github.com/users/myhduck/events{/privacy}",
    "received_events_url": "https://api.github.com/users/myhduck/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "trevor",
    "id": 5945,
    "node_id": "MDQ6VXNlcjU5NDU=",
    "avatar_url": "https://avatars0.githubusercontent.com/u/5945?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/trevor",
    "html_url": "https://github.com/trevor",
    "followers_url": "https://api.github.com/users/trevor/followers",
    "following_url": "https://api.github.com/users/trevor/following{/other_user}",
    "gists_url": "https://api.github.com/users/trevor/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/trevor/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/trevor/subscriptions",
    "organizations_url": "https://api.github.com/users/trevor/orgs",
    "repos_url": "https://api.github.com/users/trevor/repos",
    "events_url": "https://api.github.com/users/trevor/events{/privacy}",
    "received_events_url": "https://api.github.com/users/trevor/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "ogijun",
    "id": 8826,
    "node_id": "MDQ6VXNlcjg4MjY=",
    "avatar_url": "https://avatars0.githubusercontent.com/u/8826?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/ogijun",
    "html_url": "https://github.com/ogijun",
    "followers_url": "https://api.github.com/users/ogijun/followers",
    "following_url": "https://api.github.com/users/ogijun/following{/other_user}",
    "gists_url": "https://api.github.com/users/ogijun/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/ogijun/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/ogijun/subscriptions",
    "organizations_url": "https://api.github.com/users/ogijun/orgs",
    "repos_url": "https://api.github.com/users/ogijun/repos",
    "events_url": "https://api.github.com/users/ogijun/events{/privacy}",
    "received_events_url": "https://api.github.com/users/ogijun/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "mattn",
    "id": 10111,
    "node_id": "MDQ6VXNlcjEwMTEx",
    "avatar_url": "https://avatars0.githubusercontent.com/u/10111?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/mattn",
    "html_url": "https://github.com/mattn",
    "followers_url": "https://api.github.com/users/mattn/followers",
    "following_url": "https://api.github.com/users/mattn/following{/other_user}",
    "gists_url": "https://api.github.com/users/mattn/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/mattn/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/mattn/subscriptions",
    "organizations_url": "https://api.github.com/users/mattn/orgs",
    "repos_url": "https://api.github.com/users/mattn/repos",
    "events_url": "https://api.github.com/users/mattn/events{/privacy}",
    "received_events_url": "https://api.github.com/users/mattn/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "reeze",
    "id": 14658,
    "node_id": "MDQ6VXNlcjE0NjU4",
    "avatar_url": "https://avatars3.githubusercontent.com/u/14658?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/reeze",
    "html_url": "https://github.com/reeze",
    "followers_url": "https://api.github.com/users/reeze/followers",
    "following_url": "https://api.github.com/users/reeze/following{/other_user}",
    "gists_url": "https://api.github.com/users/reeze/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/reeze/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/reeze/subscriptions",
    "organizations_url": "https://api.github.com/users/reeze/orgs",
    "repos_url": "https://api.github.com/users/reeze/repos",
    "events_url": "https://api.github.com/users/reeze/events{/privacy}",
    "received_events_url": "https://api.github.com/users/reeze/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "othree",
    "id": 16474,
    "node_id": "MDQ6VXNlcjE2NDc0",
    "avatar_url": "https://avatars1.githubusercontent.com/u/16474?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/othree",
    "html_url": "https://github.com/othree",
    "followers_url": "https://api.github.com/users/othree/followers",
    "following_url": "https://api.github.com/users/othree/following{/other_user}",
    "gists_url": "https://api.github.com/users/othree/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/othree/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/othree/subscriptions",
    "organizations_url": "https://api.github.com/users/othree/orgs",
    "repos_url": "https://api.github.com/users/othree/repos",
    "events_url": "https://api.github.com/users/othree/events{/privacy}",
    "received_events_url": "https://api.github.com/users/othree/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "rkh",
    "id": 30442,
    "node_id": "MDQ6VXNlcjMwNDQy",
    "avatar_url": "https://avatars2.githubusercontent.com/u/30442?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/rkh",
    "html_url": "https://github.com/rkh",
    "followers_url": "https://api.github.com/users/rkh/followers",
    "following_url": "https://api.github.com/users/rkh/following{/other_user}",
    "gists_url": "https://api.github.com/users/rkh/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/rkh/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/rkh/subscriptions",
    "organizations_url": "https://api.github.com/users/rkh/orgs",
    "repos_url": "https://api.github.com/users/rkh/repos",
    "events_url": "https://api.github.com/users/rkh/events{/privacy}",
    "received_events_url": "https://api.github.com/users/rkh/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "keikubo",
    "id": 42560,
    "node_id": "MDQ6VXNlcjQyNTYw",
    "avatar_url": "https://avatars1.githubusercontent.com/u/42560?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/keikubo",
    "html_url": "https://github.com/keikubo",
    "followers_url": "https://api.github.com/users/keikubo/followers",
    "following_url": "https://api.github.com/users/keikubo/following{/other_user}",
    "gists_url": "https://api.github.com/users/keikubo/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/keikubo/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/keikubo/subscriptions",
    "organizations_url": "https://api.github.com/users/keikubo/orgs",
    "repos_url": "https://api.github.com/users/keikubo/repos",
    "events_url": "https://api.github.com/users/keikubo/events{/privacy}",
    "received_events_url": "https://api.github.com/users/keikubo/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "cobra90nj",
    "id": 42698,
    "node_id": "MDQ6VXNlcjQyNjk4",
    "avatar_url": "https://avatars0.githubusercontent.com/u/42698?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/cobra90nj",
    "html_url": "https://github.com/cobra90nj",
    "followers_url": "https://api.github.com/users/cobra90nj/followers",
    "following_url": "https://api.github.com/users/cobra90nj/following{/other_user}",
    "gists_url": "https://api.github.com/users/cobra90nj/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/cobra90nj/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/cobra90nj/subscriptions",
    "organizations_url": "https://api.github.com/users/cobra90nj/orgs",
    "repos_url": "https://api.github.com/users/cobra90nj/repos",
    "events_url": "https://api.github.com/users/cobra90nj/events{/privacy}",
    "received_events_url": "https://api.github.com/users/cobra90nj/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "jdoliner",
    "id": 43867,
    "node_id": "MDQ6VXNlcjQzODY3",
    "avatar_url": "https://avatars3.githubusercontent.com/u/43867?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/jdoliner",
    "html_url": "https://github.com/jdoliner",
    "followers_url": "https://api.github.com/users/jdoliner/followers",
    "following_url": "https://api.github.com/users/jdoliner/following{/other_user}",
    "gists_url": "https://api.github.com/users/jdoliner/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/jdoliner/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/jdoliner/subscriptions",
    "organizations_url": "https://api.github.com/users/jdoliner/orgs",
    "repos_url": "https://api.github.com/users/jdoliner/repos",
    "events_url": "https://api.github.com/users/jdoliner/events{/privacy}",
    "received_events_url": "https://api.github.com/users/jdoliner/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "tatsuosakurai",
    "id": 44219,
    "node_id": "MDQ6VXNlcjQ0MjE5",
    "avatar_url": "https://avatars1.githubusercontent.com/u/44219?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/tatsuosakurai",
    "html_url": "https://github.com/tatsuosakurai",
    "followers_url": "https://api.github.com/users/tatsuosakurai/followers",
    "following_url": "https://api.github.com/users/tatsuosakurai/following{/other_user}",
    "gists_url": "https://api.github.com/users/tatsuosakurai/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/tatsuosakurai/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/tatsuosakurai/subscriptions",
    "organizations_url": "https://api.github.com/users/tatsuosakurai/orgs",
    "repos_url": "https://api.github.com/users/tatsuosakurai/repos",
    "events_url": "https://api.github.com/users/tatsuosakurai/events{/privacy}",
    "received_events_url": "https://api.github.com/users/tatsuosakurai/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "shimbaco",
    "id": 56767,
    "node_id": "MDQ6VXNlcjU2NzY3",
    "avatar_url": "https://avatars1.githubusercontent.com/u/56767?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/shimbaco",
    "html_url": "https://github.com/shimbaco",
    "followers_url": "https://api.github.com/users/shimbaco/followers",
    "following_url": "https://api.github.com/users/shimbaco/following{/other_user}",
    "gists_url": "https://api.github.com/users/shimbaco/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/shimbaco/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/shimbaco/subscriptions",
    "organizations_url": "https://api.github.com/users/shimbaco/orgs",
    "repos_url": "https://api.github.com/users/shimbaco/repos",
    "events_url": "https://api.github.com/users/shimbaco/events{/privacy}",
    "received_events_url": "https://api.github.com/users/shimbaco/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "catsby",
    "id": 61721,
    "node_id": "MDQ6VXNlcjYxNzIx",
    "avatar_url": "https://avatars3.githubusercontent.com/u/61721?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/catsby",
    "html_url": "https://github.com/catsby",
    "followers_url": "https://api.github.com/users/catsby/followers",
    "following_url": "https://api.github.com/users/catsby/following{/other_user}",
    "gists_url": "https://api.github.com/users/catsby/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/catsby/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/catsby/subscriptions",
    "organizations_url": "https://api.github.com/users/catsby/orgs",
    "repos_url": "https://api.github.com/users/catsby/repos",
    "events_url": "https://api.github.com/users/catsby/events{/privacy}",
    "received_events_url": "https://api.github.com/users/catsby/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "lrvick",
    "id": 69200,
    "node_id": "MDQ6VXNlcjY5MjAw",
    "avatar_url": "https://avatars2.githubusercontent.com/u/69200?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/lrvick",
    "html_url": "https://github.com/lrvick",
    "followers_url": "https://api.github.com/users/lrvick/followers",
    "following_url": "https://api.github.com/users/lrvick/following{/other_user}",
    "gists_url": "https://api.github.com/users/lrvick/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/lrvick/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/lrvick/subscriptions",
    "organizations_url": "https://api.github.com/users/lrvick/orgs",
    "repos_url": "https://api.github.com/users/lrvick/repos",
    "events_url": "https://api.github.com/users/lrvick/events{/privacy}",
    "received_events_url": "https://api.github.com/users/lrvick/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "InFog",
    "id": 72276,
    "node_id": "MDQ6VXNlcjcyMjc2",
    "avatar_url": "https://avatars3.githubusercontent.com/u/72276?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/InFog",
    "html_url": "https://github.com/InFog",
    "followers_url": "https://api.github.com/users/InFog/followers",
    "following_url": "https://api.github.com/users/InFog/following{/other_user}",
    "gists_url": "https://api.github.com/users/InFog/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/InFog/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/InFog/subscriptions",
    "organizations_url": "https://api.github.com/users/InFog/orgs",
    "repos_url": "https://api.github.com/users/InFog/repos",
    "events_url": "https://api.github.com/users/InFog/events{/privacy}",
    "received_events_url": "https://api.github.com/users/InFog/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "Sannis",
    "id": 77367,
    "node_id": "MDQ6VXNlcjc3MzY3",
    "avatar_url": "https://avatars2.githubusercontent.com/u/77367?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/Sannis",
    "html_url": "https://github.com/Sannis",
    "followers_url": "https://api.github.com/users/Sannis/followers",
    "following_url": "https://api.github.com/users/Sannis/following{/other_user}",
    "gists_url": "https://api.github.com/users/Sannis/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/Sannis/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/Sannis/subscriptions",
    "organizations_url": "https://api.github.com/users/Sannis/orgs",
    "repos_url": "https://api.github.com/users/Sannis/repos",
    "events_url": "https://api.github.com/users/Sannis/events{/privacy}",
    "received_events_url": "https://api.github.com/users/Sannis/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "nolim1t",
    "id": 83470,
    "node_id": "MDQ6VXNlcjgzNDcw",
    "avatar_url": "https://avatars2.githubusercontent.com/u/83470?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/nolim1t",
    "html_url": "https://github.com/nolim1t",
    "followers_url": "https://api.github.com/users/nolim1t/followers",
    "following_url": "https://api.github.com/users/nolim1t/following{/other_user}",
    "gists_url": "https://api.github.com/users/nolim1t/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/nolim1t/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/nolim1t/subscriptions",
    "organizations_url": "https://api.github.com/users/nolim1t/orgs",
    "repos_url": "https://api.github.com/users/nolim1t/repos",
    "events_url": "https://api.github.com/users/nolim1t/events{/privacy}",
    "received_events_url": "https://api.github.com/users/nolim1t/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "moul",
    "id": 94029,
    "node_id": "MDQ6VXNlcjk0MDI5",
    "avatar_url": "https://avatars1.githubusercontent.com/u/94029?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/moul",
    "html_url": "https://github.com/moul",
    "followers_url": "https://api.github.com/users/moul/followers",
    "following_url": "https://api.github.com/users/moul/following{/other_user}",
    "gists_url": "https://api.github.com/users/moul/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/moul/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/moul/subscriptions",
    "organizations_url": "https://api.github.com/users/moul/orgs",
    "repos_url": "https://api.github.com/users/moul/repos",
    "events_url": "https://api.github.com/users/moul/events{/privacy}",
    "received_events_url": "https://api.github.com/users/moul/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "bx2",
    "id": 94500,
    "node_id": "MDQ6VXNlcjk0NTAw",
    "avatar_url": "https://avatars0.githubusercontent.com/u/94500?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/bx2",
    "html_url": "https://github.com/bx2",
    "followers_url": "https://api.github.com/users/bx2/followers",
    "following_url": "https://api.github.com/users/bx2/following{/other_user}",
    "gists_url": "https://api.github.com/users/bx2/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/bx2/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/bx2/subscriptions",
    "organizations_url": "https://api.github.com/users/bx2/orgs",
    "repos_url": "https://api.github.com/users/bx2/repos",
    "events_url": "https://api.github.com/users/bx2/events{/privacy}",
    "received_events_url": "https://api.github.com/users/bx2/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "pitr",
    "id": 102791,
    "node_id": "MDQ6VXNlcjEwMjc5MQ==",
    "avatar_url": "https://avatars2.githubusercontent.com/u/102791?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/pitr",
    "html_url": "https://github.com/pitr",
    "followers_url": "https://api.github.com/users/pitr/followers",
    "following_url": "https://api.github.com/users/pitr/following{/other_user}",
    "gists_url": "https://api.github.com/users/pitr/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/pitr/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/pitr/subscriptions",
    "organizations_url": "https://api.github.com/users/pitr/orgs",
    "repos_url": "https://api.github.com/users/pitr/repos",
    "events_url": "https://api.github.com/users/pitr/events{/privacy}",
    "received_events_url": "https://api.github.com/users/pitr/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "JoseRibeiro",
    "id": 108473,
    "node_id": "MDQ6VXNlcjEwODQ3Mw==",
    "avatar_url": "https://avatars3.githubusercontent.com/u/108473?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/JoseRibeiro",
    "html_url": "https://github.com/JoseRibeiro",
    "followers_url": "https://api.github.com/users/JoseRibeiro/followers",
    "following_url": "https://api.github.com/users/JoseRibeiro/following{/other_user}",
    "gists_url": "https://api.github.com/users/JoseRibeiro/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/JoseRibeiro/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/JoseRibeiro/subscriptions",
    "organizations_url": "https://api.github.com/users/JoseRibeiro/orgs",
    "repos_url": "https://api.github.com/users/JoseRibeiro/repos",
    "events_url": "https://api.github.com/users/JoseRibeiro/events{/privacy}",
    "received_events_url": "https://api.github.com/users/JoseRibeiro/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "dpflug",
    "id": 108501,
    "node_id": "MDQ6VXNlcjEwODUwMQ==",
    "avatar_url": "https://avatars3.githubusercontent.com/u/108501?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/dpflug",
    "html_url": "https://github.com/dpflug",
    "followers_url": "https://api.github.com/users/dpflug/followers",
    "following_url": "https://api.github.com/users/dpflug/following{/other_user}",
    "gists_url": "https://api.github.com/users/dpflug/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/dpflug/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/dpflug/subscriptions",
    "organizations_url": "https://api.github.com/users/dpflug/orgs",
    "repos_url": "https://api.github.com/users/dpflug/repos",
    "events_url": "https://api.github.com/users/dpflug/events{/privacy}",
    "received_events_url": "https://api.github.com/users/dpflug/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "kennethreitz",
    "id": 119893,
    "node_id": "MDQ6VXNlcjExOTg5Mw==",
    "avatar_url": "https://avatars2.githubusercontent.com/u/119893?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/kennethreitz",
    "html_url": "https://github.com/kennethreitz",
    "followers_url": "https://api.github.com/users/kennethreitz/followers",
    "following_url": "https://api.github.com/users/kennethreitz/following{/other_user}",
    "gists_url": "https://api.github.com/users/kennethreitz/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/kennethreitz/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/kennethreitz/subscriptions",
    "organizations_url": "https://api.github.com/users/kennethreitz/orgs",
    "repos_url": "https://api.github.com/users/kennethreitz/repos",
    "events_url": "https://api.github.com/users/kennethreitz/events{/privacy}",
    "received_events_url": "https://api.github.com/users/kennethreitz/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "danielrmz",
    "id": 120647,
    "node_id": "MDQ6VXNlcjEyMDY0Nw==",
    "avatar_url": "https://avatars3.githubusercontent.com/u/120647?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/danielrmz",
    "html_url": "https://github.com/danielrmz",
    "followers_url": "https://api.github.com/users/danielrmz/followers",
    "following_url": "https://api.github.com/users/danielrmz/following{/other_user}",
    "gists_url": "https://api.github.com/users/danielrmz/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/danielrmz/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/danielrmz/subscriptions",
    "organizations_url": "https://api.github.com/users/danielrmz/orgs",
    "repos_url": "https://api.github.com/users/danielrmz/repos",
    "events_url": "https://api.github.com/users/danielrmz/events{/privacy}",
    "received_events_url": "https://api.github.com/users/danielrmz/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "vitaminjeff",
    "id": 125537,
    "node_id": "MDQ6VXNlcjEyNTUzNw==",
    "avatar_url": "https://avatars2.githubusercontent.com/u/125537?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/vitaminjeff",
    "html_url": "https://github.com/vitaminjeff",
    "followers_url": "https://api.github.com/users/vitaminjeff/followers",
    "following_url": "https://api.github.com/users/vitaminjeff/following{/other_user}",
    "gists_url": "https://api.github.com/users/vitaminjeff/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/vitaminjeff/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/vitaminjeff/subscriptions",
    "organizations_url": "https://api.github.com/users/vitaminjeff/orgs",
    "repos_url": "https://api.github.com/users/vitaminjeff/repos",
    "events_url": "https://api.github.com/users/vitaminjeff/events{/privacy}",
    "received_events_url": "https://api.github.com/users/vitaminjeff/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "chrisforbes",
    "id": 128877,
    "node_id": "MDQ6VXNlcjEyODg3Nw==",
    "avatar_url": "https://avatars1.githubusercontent.com/u/128877?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/chrisforbes",
    "html_url": "https://github.com/chrisforbes",
    "followers_url": "https://api.github.com/users/chrisforbes/followers",
    "following_url": "https://api.github.com/users/chrisforbes/following{/other_user}",
    "gists_url": "https://api.github.com/users/chrisforbes/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/chrisforbes/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/chrisforbes/subscriptions",
    "organizations_url": "https://api.github.com/users/chrisforbes/orgs",
    "repos_url": "https://api.github.com/users/chrisforbes/repos",
    "events_url": "https://api.github.com/users/chrisforbes/events{/privacy}",
    "received_events_url": "https://api.github.com/users/chrisforbes/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "axiomsofchoice",
    "id": 136502,
    "node_id": "MDQ6VXNlcjEzNjUwMg==",
    "avatar_url": "https://avatars0.githubusercontent.com/u/136502?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/axiomsofchoice",
    "html_url": "https://github.com/axiomsofchoice",
    "followers_url": "https://api.github.com/users/axiomsofchoice/followers",
    "following_url": "https://api.github.com/users/axiomsofchoice/following{/other_user}",
    "gists_url": "https://api.github.com/users/axiomsofchoice/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/axiomsofchoice/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/axiomsofchoice/subscriptions",
    "organizations_url": "https://api.github.com/users/axiomsofchoice/orgs",
    "repos_url": "https://api.github.com/users/axiomsofchoice/repos",
    "events_url": "https://api.github.com/users/axiomsofchoice/events{/privacy}",
    "received_events_url": "https://api.github.com/users/axiomsofchoice/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "EnTeQuAk",
    "id": 139033,
    "node_id": "MDQ6VXNlcjEzOTAzMw==",
    "avatar_url": "https://avatars1.githubusercontent.com/u/139033?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/EnTeQuAk",
    "html_url": "https://github.com/EnTeQuAk",
    "followers_url": "https://api.github.com/users/EnTeQuAk/followers",
    "following_url": "https://api.github.com/users/EnTeQuAk/following{/other_user}",
    "gists_url": "https://api.github.com/users/EnTeQuAk/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/EnTeQuAk/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/EnTeQuAk/subscriptions",
    "organizations_url": "https://api.github.com/users/EnTeQuAk/orgs",
    "repos_url": "https://api.github.com/users/EnTeQuAk/repos",
    "events_url": "https://api.github.com/users/EnTeQuAk/events{/privacy}",
    "received_events_url": "https://api.github.com/users/EnTeQuAk/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "jag",
    "id": 162375,
    "node_id": "MDQ6VXNlcjE2MjM3NQ==",
    "avatar_url": "https://avatars3.githubusercontent.com/u/162375?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/jag",
    "html_url": "https://github.com/jag",
    "followers_url": "https://api.github.com/users/jag/followers",
    "following_url": "https://api.github.com/users/jag/following{/other_user}",
    "gists_url": "https://api.github.com/users/jag/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/jag/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/jag/subscriptions",
    "organizations_url": "https://api.github.com/users/jag/orgs",
    "repos_url": "https://api.github.com/users/jag/repos",
    "events_url": "https://api.github.com/users/jag/events{/privacy}",
    "received_events_url": "https://api.github.com/users/jag/received_events",
    "type": "User",
    "site_admin": false
  },
  {
    "login": "cebe",
    "id": 189796,
    "node_id": "MDQ6VXNlcjE4OTc5Ng==",
    "avatar_url": "https://avatars0.githubusercontent.com/u/189796?v=4",
    "gravatar_id": "",
    "url": "https://api.github.com/users/cebe",
    "html_url": "https://github.com/cebe",
    "followers_url": "https://api.github.com/users/cebe/followers",
    "following_url": "https://api.github.com/users/cebe/following{/other_user}",
    "gists_url": "https://api.github.com/users/cebe/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/cebe/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/cebe/subscriptions",
    "organizations_url": "https://api.github.com/users/cebe/orgs",
    "repos_url": "https://api.github.com/users/cebe/repos",
    "events_url": "https://api.github.com/users/cebe/events{/privacy}",
    "received_events_url": "https://api.github.com/users/cebe/received_events",
    "type": "User",
    "site_admin": false
  }
]
Accept


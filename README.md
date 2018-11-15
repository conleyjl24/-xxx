
# 1."Keter"-The crown is a balancing force.
# 2.Hochma-Wisdom balanced in its unchangeable order by the initiative of
# 3.Bina-An active mind balanced by wisdom
# 4.Hezed-Mercy the second concept of wisdom is always favorable
# 5.Gebura-Rigor the inevitable existence of which is due to wisdom and
# 6.TiFERET-Beautty is a radiant concept of balance in forms the transition from
# 7.Netz-Victory i e eternal triumph of reason and justice
# 8.Year-The eternity of the conguests achieved by mind over matter active over
# 9.Jesod-The basis i e the basis of all beliefs and truths is what we call the
# 10.Malchut or Malkut (Malkout)-The Kingdom is the universe all creation is the
# work and mirror of God proof of the existence of a higher mind the exact conseguence that
# causes us to ascend to the first possible premises a riddle whose answer is God i e the
# Supreme and absolute mind.

work and mirror of God proof of the existence of a higher mind the exact conseguence that
causes us to ascend to the first possible premises a riddle whose answer is God i e the

Supreme and absolute mind.
#742

<div id="root" />
# React Starter
A Pen by mmarzion67 on CodePen.
License.

Hello-World
 public static class SocketExtensions
    {
        public static Task ConnectExAsync(this Socket socket, string host, int port, CancellationToken cancellationToken = default)
        {
            var xCompletion = new TaskCompletionSource<bool>();
            socket.BeginConnect(host,
                                port,
                                r =>
                                {
                                    try
                                    {
                                        socket.EndConnect(r);
                                        xCompletion.TrySetResult(true);
                                    }
                                    catch (Exception E)
                                    {
                                        xCompletion.TrySetException(E);
                                    }
                                },
                                null);

            cancellationToken.Register(() =>
                                       {
                                           xCompletion.SetException(new TimeoutException());
                                           socket.Close();
                                       });

            return xCompletion.Task;
        }
    }
[…]
<provider
 android:name="android.support.v4.content.FileProvider" android:authorities="com.gravitywell.jamesbest.customimagekeyboardtut.inputcontent"
 android:exported="false"
 android:grantUriPermissions="true">
 <meta-data
 android:name="android.support.FILE_PROVIDER_PATHS"
 android:resource="@xml/file_paths" />
 </provider>
 Hello-World
what medications are needed
for the treatment of syphilis report
Yes there is a single all-encompassing eternal teaching strong as the Supreme mind simple as
everything great understandable as everything is universal and absolutely true))
Gemfile GitHub Pages
source 'https://rubygems.org'
gem 'github-pages'
.travis.yml GitHub Pages
language: ruby
rvm:
-2.1
script: "bundle exec jekyll build"
Trigger with condition (e.g. CellMenuBase)
x ~~ () => false ~~~> y

fmt.Println(time.Since(start))
}
@477447

route:
preserve host:true

#700
default
#![allow(unreachable_code)]


fn main() {
    println!("{:?}", {
        let foo = 5; let _bar = &foo as *const i32; let _baz = &mut foo as *mut i32;
    });
}


/* ~~~~=== stderr ===~~~~
   Compiling playground v0.0.1 (/playground)
error[E0596]: cannot borrow immutable local variable `foo` as mutable
 --> src/main.rs:6:69
  |
6 |         let foo = 5; let _bar = &foo as *const i32; let _baz = &mut foo as *mut i32;
  |             --- help: make this binding mutable: `mut foo`          ^^^ cannot borrow mutably
error: aborting due to previous error
For more information about this error, try `rustc --explain E0596`.
error: Could not compile `playground`.
To learn more, run the command again with --verbose.
*/

/* ~~~~=== stdout ===~~~~
*/
add_filter( 'techmarket_search_categories_filter_args', 'tm_change_search_cat_ids', 30 );

function tm_change_search_cat_ids( $args ) {
    $args[ 'include' ] = '62,63';
    return $args;
}
--verbose.
from_address	to_address	trace_address	error	status
0xc5b373618d4d01a38f822f56ca6d2ff5080cc4f2	0xc5f60fa4613493931b605b6da1e9febbdeb61e16			1
0xc5f60fa4613493931b605b6da1e9febbdeb61e16	0x06012c8cf97bead5deae237070f9587f8e7a266d	0	Reverted	0
#!/bin/bash
#http://wireless.kernel.org/en/users/Drivers/b43

su -
yum install b43-fwcutter wget # apt-get or whatever your package manager is
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
tar xjf broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" broadcom-wl-5.100.138/linux/wl_apsta.o
echo 'modprobe b43' > /etc/sysconfig/modules/b43.modules
chmod +x /etc/sysconfig/modules/b43.modules
--[[
Perspective v2.0.2
A library for easily and smoothly integrating a virtual camera into your game.
Based on modified version of the Dusk camera system.
v2.0.2 adds a more stable tracking system and re-implements scrollX and scrollY
--]]

local lib_perspective = {}

--------------------------------------------------------------------------------
-- Localize
--------------------------------------------------------------------------------
local display_newGroup = display.newGroup
local display_remove = display.remove
local type = type
local table_insert = table.insert
local math_huge = math.huge
local math_nhuge = -math.huge

local clamp = function(v, l, h) return (v < l and l) or (v > h and h) or v end

--------------------------------------------------------------------------------
-- Create View
--------------------------------------------------------------------------------
lib_perspective.createView = function(layerCount, group)
	------------------------------------------------------------------------------
	-- Create view, internal object, and layers
	------------------------------------------------------------------------------

	local view = group or display_newGroup()

	view.damping = 1
	view.snapWhenFocused = true -- Do we instantly snap to the object when :setFocus() is called?
	
	local isTracking
	
	local internal -- So we can access it from inside the declaration
	internal = {
		trackingLevel = 1,
		damping = 1,
		scaleBoundsToScreen = true,
		xScale = 1,
		yScale = 1,
		addX = display.contentCenterX,
		addY = display.contentCenterY,
		bounds = {
			xMin = math_nhuge,
			xMax = math_huge,
			yMin = math_nhuge,
			yMax = math_huge
		},
		scaledBounds = {
			xMin = math_nhuge,
			xMax = math_huge,
			yMin = math_nhuge,
			yMax = math_huge
		},
		trackFocus = true,
		focus = nil,
		viewX = 0,
		viewY = 0,
		getViewXY = function() if internal.focus then return internal.focus.x, internal.focus.y else return internal.viewX, internal.viewY end end,
		layer = {},
		updateAddXY = function() internal.addX = display.contentCenterX / view.xScale internal.addY = display.contentCenterY / view.yScale end
	}
	
	local layers = {}
	
	
	------------------------------------------------------------------------------
	------------------------------------------------------------------------------
	-- Internal Methods
	------------------------------------------------------------------------------
	------------------------------------------------------------------------------
	
	
	------------------------------------------------------------------------------
	-- Scale Bounds
	------------------------------------------------------------------------------
	internal.scaleBounds = function(doX, doY)
		if internal.scaleBoundsToScreen then
			local xMin = internal.bounds.xMin
			local xMax = internal.bounds.xMax
			local yMin = internal.bounds.yMin
			local yMax = internal.bounds.yMax

			local doX = doX and not ((xMin == math_nhuge) or (xMax == math_huge))
			local doY = doY and not ((yMin == math_nhuge) or (yMax == math_huge))

			if doX then
				local scaled_xMin = xMin / view.xScale
				local scaled_xMax = xMax - (scaled_xMin - xMin)

				if scaled_xMax < scaled_xMin then
					local hopDist = scaled_xMin - scaled_xMax
					local halfDist = hopDist * 0.5
					scaled_xMax = scaled_xMax + halfDist
					scaled_xMin = scaled_xMin - halfDist
				end

				internal.scaledBounds.xMin = scaled_xMin
				internal.scaledBounds.xMax = scaled_xMax
			end

			if doY then
				local scaled_yMin = yMin / view.yScale
				local scaled_yMax = yMax - (scaled_yMin - yMin)

				if scaled_yMax < scaled_yMin then
					local hopDist = scaled_yMin - scaled_yMax
					local halfDist = hopDist * 0.5
					scaled_yMax = scaled_yMax + halfDist
					scaled_yMin = scaled_yMin - halfDist
				end

				internal.scaledBounds.yMin = scaled_yMin
				internal.scaledBounds.yMax = scaled_yMax
			end
		else
			camera.scaledBounds.xMin, camera.scaledBounds.xMax, camera.scaledBounds.yMin, camera.scaledBounds.yMax = camera.bounds.xMin, camera.bounds.xMax, camera.bounds.yMin, camera.bounds.yMax
		end
	end
	
	------------------------------------------------------------------------------
	-- Process Viewpoint
	------------------------------------------------------------------------------
	internal.processViewpoint = function()
		if internal.damping ~= view.damping then internal.trackingLevel = 1 / view.damping internal.damping = view.damping end
		if internal.trackFocus then
			local x, y = internal.getViewXY()
			
			if view.xScale ~= internal.xScale or view.yScale ~= internal.yScale then internal.updateAddXY() end
			if view.xScale ~= internal.xScale then internal.xScale = view.xScale internal.scaleBounds(true, false) end
			if view.yScale ~= internal.yScale then internal.yScale = view.yScale internal.scaleBounds(false, true) end
			
			x = clamp(x, internal.scaledBounds.xMin, internal.scaledBounds.xMax)
			y = clamp(y, internal.scaledBounds.yMin, internal.scaledBounds.yMax)
			internal.viewX, internal.viewY = x, y
		end
	end
	
	
	------------------------------------------------------------------------------
	------------------------------------------------------------------------------
	-- Public Methods
	------------------------------------------------------------------------------
	------------------------------------------------------------------------------
	
	
	------------------------------------------------------------------------------
	-- Append Layer
	------------------------------------------------------------------------------
	view.appendLayer = function()
		local layer = display_newGroup()
		layer.xParallax, layer.yParallax = 1, 1
		view:insert(layer)
		layer:toBack()
		table_insert(layers, layer)
	
		layer._perspectiveIndex = #layers
		
		internal.layer[#layers] = {
			x = 0,
			y = 0,
			xOffset = 0,
			yOffset = 0
		}
		
		function layer:setCameraOffset(x, y) internal.layer[layer._perspectiveIndex].xOffset, internal.layer[layer._perspectiveIndex].yOffset = x, y end
	end
	
	------------------------------------------------------------------------------
	-- Add an Object to the Camera
	------------------------------------------------------------------------------
	function view:add(obj, l, isFocus)
		local l = l or 4
		layers[l]:insert(obj)
		obj._perspectiveLayer = l
		
		if isFocus then view:setFocus(obj) end
		-- Move an object to a layer
		function obj:toLayer(newLayer) if layer[newLayer] then layer[newLayer]:insert(obj) obj._perspectiveLayer = newLayer end end
		--Move an object back a layer
		function obj:back() if layer[obj._perspectiveLayer + 1] then layer[obj._perspectiveLayer + 1]:insert(obj) obj._perspectiveLayer = obj.layer + 1 end end
		--Moves an object forwards a layer
		function obj:forward() if layer[obj._perspectiveLayer - 1] then layer[obj._perspectiveLayer - 1]:insert(obj) obj._perspectiveLayer = obj.layer - 1 end end
		--Moves an object to the very front of the camera
		function obj:toCameraFront() layer[1]:insert(obj) obj._perspectiveLayer = 1 obj:toFront() end
		--Moves an object to the very back of the camera
		function obj:toCameraBack() layer[#layers]:insert(obj) obj._perspectiveLayer = #layers obj:toBack() end
	end
	
	------------------------------------------------------------------------------
	-- Main Tracking Function
	------------------------------------------------------------------------------
	function view:trackFocus()
		internal.processViewpoint()
		local viewX, viewY = internal.viewX, internal.viewY
		
		layers[1].xParallax, layers[1].yParallax = 1, 1

		for i = 1, #layers do
			local addX, addY = internal.addX, internal.addY
			local layerX, layerY = internal.layer[i].x, internal.layer[i].y

			local diffX = (-viewX - layerX)
			local diffY = (-viewY - layerY)
			local incrX = diffX
			local incrY = diffY
			internal.layer[i].x = layerX + incrX
			internal.layer[i].y = layerY + incrY
			
			layers[i].x = (layers[i].x - (layers[i].x - (internal.layer[i].x + addX) * layers[i].xParallax) * internal.trackingLevel)
			layers[i].y = (layers[i].y - (layers[i].y - (internal.layer[i].y + addY) * layers[i].yParallax) * internal.trackingLevel)
		end

		view.scrollX, view.scrollY = layers[1].x, layers[1].y
	end
	
	------------------------------------------------------------------------------
	-- Set the Camera Bounds
	------------------------------------------------------------------------------
	function view:setBounds(x1, x2, y1, y2)
		local xMin, xMax, yMin, yMax
		
		if x1 ~= nil then if not x1 then xMin = math_nhuge else xMin = x1 end end
		if x2 ~= nil then if not x2 then xMax = math_huge else xMax = x2 end end
		if y1 ~= nil then if not y1 then yMin = math_nhuge else yMin = y1 end end
		if y2 ~= nil then if not y2 then yMax = math_huge else yMax = y2 end end
	
		internal.bounds.xMin = xMin
		internal.bounds.xMax = xMax
		internal.bounds.yMin = yMin
		internal.bounds.yMax = yMax
		internal.scaleBounds(true, true)
	end
	
	------------------------------------------------------------------------------
	-- Miscellaneous Functions
	------------------------------------------------------------------------------
	-- Begin auto-tracking
	function view:track() if not isTracking then Runtime:addEventListener("enterFrame", view.trackFocus) isTracking = true end end
	-- Stop auto-tracking
	function view:cancel() if isTracking then Runtime:removeEventListener("enterFrame", view.trackFocus) isTracking = false end end
	-- Remove an object from the view
	function view:remove(obj) if obj and obj._perspectiveLayer then layers[obj._perspectiveLayer]:remove(obj) end end
	-- Set the view's focus
	function view:setFocus(obj) if obj then internal.focus = obj end if view.snapWhenFocused then view.snap() end end
	-- Snap the view to the focus point
	function view:snap() local t = internal.trackingLevel local d = internal.damping internal.trackingLevel = 1 internal.damping = view.damping view:trackFocus() internal.trackingLevel = t internal.damping = d end
	-- Move the view to a point
	function view:toPoint(x, y) view:cancel() local newFocus = {x = x, y = y} view:setFocus(newFocus) view:track() return newFocus end
	-- Get a layer of the view
	function view:layer(n) return layers[n] end
	-- Destroy the view
	function view:destroy() view:cancel() for i = 1, #layers do for o = 1, layers[i].numChildren do layers[i]:remove(layers[i][o]) end end display_remove(view) view = nil return true end
	-- Set layer parallax
	function view:setParallax(...) for i = 1, #arg do if type(arg[i]) == "table" then layers[i].xParallax, layers[i].yParallax = arg[i][1], arg[i][2] else layers[i].xParallax, layers[i].yParallax = arg[i], arg[i] end end end
	-- Get number of layers
	function view:layerCount() return #layers end
	
	------------------------------------------------------------------------------
	-- Build Layers
	------------------------------------------------------------------------------
	for i = layerCount or 8, 1, -1 do view.appendLayer() end
	
	return view
end

return lib_perspective

-xxx
train op = tf,train.AdamOptimizer(learning rate = lr). minimize(loss)

Intialize the network
init = tf,global variables initializer()

timezone: Africa/Nairobi timezone:Africa/Nairobi

title: “my awesome site: an adventure in parse errors”

rouge config.yml highlighter: rouge.

apiVersion:configuration.konghg.com/v1 kind:Konglngress metadata: name:drone-drone labels: app:drone component:server release:drone route: preserve host:true

<botton (click) = “onItemSelected (exerciseItem.id)” > </ button >

<botton (click) = “onItemSelected (exerciseItem.id)” > </ button >
int MarPk {get; set;}
string Libelle {get;set;}
string Code {get;set;}
boolEstlnterne {get;set;}
}
Magic differs from mysticism to those that judge a priori only a posteriori by setting pre-the basis of
</body> </html> @477447 jekyll #700 Default

https://github.com/jekyll/jekyll.git android;name=”android.support.FILE PROVIDER PATHS” android;resource=”@xml/file paths”/> </provider>

$ args [‘include’] = ‘62, 63 ‘; return $ args; } –verbose. sudo b43-fwcutter -w “$FIRMWARE_INSTALL_DIR” broadcom-wl-5.100.138/linux/wl_apsta.o echo ‘modprobe b43’ > /etc/sysconfig/modules/b43.modules chmod +x /etc/sysconfig/modules/b43.modules

static final String alphabet = "0123456789ABCDE";

	public static void main(String[] args) throws UnknownHostException, IOException {
		System.setProperty("javax.net.ssl.trustStore", "C:\\path\\to\\java\\truststore.jks");
		System.setProperty("javax.net.ssl.trustStorePassword", "Password1");
		SSLSocketFactory factory = (SSLSocketFactory) SSLSocketFactory.getDefault();
		SSLSocket sslsocket = (SSLSocket) factory.createSocket("127.0.0.1", 7000);
		OutputStreamWriter writer = new OutputStreamWriter(sslsocket.getOutputStream(), "UTF-8");
		char[] buffer = new char[9];
		Random r = new Random();
		for (int i = 0; i < 9; i++) {
			buffer[i] = alphabet.charAt(r.nextInt(alphabet.length()));
		}
		writer.write(buffer);
		writer.close();
		sslsocket.close();
	}
	
1."Keter"-The crown is a balancing force.
2.Hochma-Wisdom balanced in its unchangeable order by the initiative of
3.Bina-An active mind balanced by wisdom
4.Hezed-Mercy the second concept of wisdom is always favorable
5.Gebura-Rigor the inevitable existence of which is due to wisdom and
6.TiFERET-Beautty is a radiant concept of balance in forms the transition from
7.Netz-Victory i e eternal triumph of reason and justice
8.Year-The eternity of the conguests achieved by mind over matter active over
9.Jesod-The basis i e the basis of all beliefs and truths is what we call the
10.Malchut or Malkut (Malkout)-The Kingdom is the universe all creation is the
work and mirror of God proof of the existence of a higher mind the exact conseguence that
causes us to ascend to the first possible premises a riddle whose answer is God i e the
Supreme and absolute mind.
/*!
 * @file  DFRobot_SHT20_test.ino
 * @brief DFRobot's SHT20 Humidity And Temperature Sensor Module
 * @n     This example demonstrates how to read the user registers to display resolution and other settings.
 *        Uses the SHT20 library to display the current humidity and temperature.
 *        Open serial monitor at 9600 baud to see readings.
 *        Errors 998 if not sensor is detected. Error 999 if CRC is bad.
 * Hardware Connections:
 * -VCC = 3.3V
 * -GND = GND
 * -SDA = A4 (use inline 330 ohm resistor if your board is 5V)
 * -SCL = A5 (use inline 330 ohm resistor if your board is 5V) */
#include <WiFi.h>
#include <Wire.h>
#include "DFRobot_SHT20.h"

//Create an instance of the object
DFRobot_SHT20    sht20;


// Replace with your network credentials
const char* ssid     = "Tako Sdn Bhd@unifi";
const char* password = "Tako0387278844";

WiFiServer server(80);

// Temporary variables
static char celsiusTemp[7];
static char fahrenheitTemp[7];
static char humidityTemp[7];

// Client variables 
char linebuf[80];
int charcount=0;

void setup()
{
    Serial.begin(9600);
    Serial.println("SHT20 Example!");
    sht20.initSHT20();                                  // Init SHT20 Sensor
    delay(100);
    sht20.checkSHT20();                                 // Check SHT20 Sensor

    Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);
  
  WiFi.begin(ssid, password);
  
  // attempt to connect to Wifi network:
  while(WiFi.status() != WL_CONNECTED) {
    // Connect to WPA/WPA2 network. Change this line if using open or WEP network:
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
  Serial.println("MAC address: ");
  Serial.println(WiFi.macAddress());
  
  server.begin();
}

void loop() {
  // listen for incoming clients
  WiFiClient client = server.available();
  if (client) {
    Serial.println("New client");
    memset(linebuf,0,sizeof(linebuf));
    charcount=0;
    // an http request ends with a blank line
    boolean currentLineIsBlank = true;
    while (client.connected()) {
      if (client.available()) {
        char c = client.read();
        Serial.write(c);
        //read char by char HTTP request
        linebuf[charcount]=c;
        if (charcount<sizeof(linebuf)-1) charcount++;
        // if you've gotten to the end of the line (received a newline
        // character) and the line is blank, the http request has ended,
        // so you can send a reply
        if (c == '\n' && currentLineIsBlank) {
            // Sensor readings may also be up to 2 seconds 'old' (its a very slow sensor)
            float h = sht20.readHumidity();
            // Read temperature as Celsius (the default)
            float t = sht20.readTemperature();
            // Read temperature as Fahrenheit (isFahrenheit = true)
            float f = sht20.readTemperature();
            // Check if any reads failed and exit early (to try again).
            if (isnan(h) || isnan(t) || isnan(f)) {
              Serial.println("Failed to read from SHT sensor!");
              strcpy(celsiusTemp,"Failed");
              strcpy(fahrenheitTemp, "Failed");
              strcpy(humidityTemp, "Failed");         
            }
    /*        else{
              // Computes temperature values in Celsius + Fahrenheit and Humidity
              float hic = sht20.computeHeatIndex(t, h, false);       
              dtostrf(hic, 6, 2, celsiusTemp);             
              float hif = sht20.computeHeatIndex(f, h);
              dtostrf(hif, 6, 2, fahrenheitTemp);         
              dtostrf(h, 6, 2, humidityTemp);
          }
          */
          // send a standard http response header
          client.println("HTTP/1.1 200 OK");
          client.println("Content-Type: text/html");
          client.println("Connection: close");  // the connection will be closed after completion of the response
          client.println();
          client.println("<!DOCTYPE HTML><html><head><meta name=\"viewport\" content=\"width=device-width, initial-scale=1\">");
          client.println("<meta http-equiv=\"refresh\" content=\"4\"></head>");
          client.println("<body><div style=\"font-size: 3.5rem;\"><p>ESP32 - SHT20</p><p>");
          if(atoi(celsiusTemp)>=25){
            client.println("<div style=\"color: #930000;\">");
          }
          else if(atoi(celsiusTemp)<25 && atoi(celsiusTemp)>=5){
            client.println("<div style=\"color: #006601;\">");
          }
          else if(atoi(celsiusTemp)<5){
            client.println("<div style=\"color: #009191;\">");
          }
          
          client.println(celsiusTemp);
          client.println("*C</p><p>");
          client.println(fahrenheitTemp);
          client.println("*F</p></div><p>");
          client.println(humidityTemp);
          client.println("%</p></div>");
          client.println("</body></html>");     
          break;
        }
        if (c == '\n') {
          // you're starting a new line
          currentLineIsBlank = true;
          memset(linebuf,0,sizeof(linebuf));
          charcount=0;
        } else if (c != '\r') {
          // you've gotten a character on the current line
          currentLineIsBlank = false;
        }
      }
    }
    // give the web browser time to receive the data
    delay(1);

    // close the connection:
    client.stop();
    Serial.println("client disconnected");
  }
}

v1.0

Hello-World
what medications are needed
for the treatment of syphilis report
Yes there is a single all-encompassing eternal teaching strong as the Supreme mind simple as
everything great understandable as everything is universal and absolutely true))
Gemfile GitHub Pages
source 'https://rubygems.org'
gem 'github-pages'
.travis.yml GitHub Pages
language: ruby
rvm:
-2.1
script: "bundle exec jekyll build"
Trigger with condition (e.g. CellMenuBase)
x ~~ () => false ~~~> y

fmt.Println(time.Since(start))
}
@477447

route:
preserve host:true

#742

final class WaitTest {

    public static void main(String[] args) {
        new WaitTest().run();
    }

    void run() {
        class Closure {
            void call() {
                try {
                    wait(1000);
                    System.out.println("AHA!");
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
            }
        }

        Closure closure = new Closure();
        synchronized (this) {
            closure.call();
        }
    }
}
query getPost ($id: String!) {
  post(id: $id) {
    id
    text
  }
}
                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
      outstanding shares, or (iii) beneficial ownership of such entity.

      "You" (or "Your") shall mean an individual or Legal Entity
      exercising permissions granted by this License.

      "Source" form shall mean the preferred form for making modifications,
      including but not limited to software source code, documentation
      source, and configuration files.

      "Object" form shall mean any form resulting from mechanical
      transformation or translation of a Source form, including but
      not limited to compiled object code, generated documentation,
      and conversions to other media types.

      "Work" shall mean the work of authorship, whether in Source or
      Object form, made available under the License, as indicated by a
      copyright notice that is included in or attached to the work
      (an example is provided in the Appendix below).

      "Derivative Works" shall mean any work, whether in Source or Object
      form, that is based on (or derived from) the Work and for which the
      editorial revisions, annotations, elaborations, or other modifications
      represent, as a whole, an original work of authorship. For the purposes
      of this License, Derivative Works shall not include works that remain
      separable from, or merely link (or bind by name) to the interfaces of,
      the Work and Derivative Works thereof.

      "Contribution" shall mean any work of authorship, including
      the original version of the Work and any modifications or additions
      to that Work or Derivative Works thereof, that is intentionally
      submitted to Licensor for inclusion in the Work by the copyright owner
      or by an individual or Legal Entity authorized to submit on behalf of
      the copyright owner. For the purposes of this definition, "submitted"
      means any form of electronic, verbal, or written communication sent
      to the Licensor or its representatives, including but not limited to
      communication on electronic mailing lists, source code control systems,
      and issue tracking systems that are managed by, or on behalf of, the
      Licensor for the purpose of discussing and improving the Work, but
      excluding communication that is conspicuously marked or otherwise
      designated in writing by the copyright owner as "Not a Contribution."

      "Contributor" shall mean Licensor and any individual or Legal Entity
      on behalf of whom a Contribution has been received by Licensor and
      subsequently incorporated within the Work.

   2. Grant of Copyright License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      copyright license to reproduce, prepare Derivative Works of,
      publicly display, publicly perform, sublicense, and distribute the
      Work and such Derivative Works in Source or Object form.

   3. Grant of Patent License. Subject to the terms and conditions of
      this License, each Contributor hereby grants to You a perpetual,
      worldwide, non-exclusive, no-charge, royalty-free, irrevocable
      (except as stated in this section) patent license to make, have made,
      use, offer to sell, sell, import, and otherwise transfer the Work,
      where such license applies only to those patent claims licensable
      by such Contributor that are necessarily infringed by their
      Contribution(s) alone or by combination of their Contribution(s)
      with the Work to which such Contribution(s) was submitted. If You
      institute patent litigation against any entity (including a
      cross-claim or counterclaim in a lawsuit) alleging that the Work
      or a Contribution incorporated within the Work constitutes direct
      or contributory patent infringement, then any patent licenses
      granted to You under this License for that Work shall terminate
      as of the date such litigation is filed.

   4. Redistribution. You may reproduce and distribute copies of the
      Work or Derivative Works thereof in any medium, with or without
      modifications, and in Source or Object form, provided that You
      meet the following conditions:

      (a) You must give any other recipients of the Work or
          Derivative Works a copy of this License; and

      (b) You must cause any modified files to carry prominent notices
          stating that You changed the files; and

      (c) You must retain, in the Source form of any Derivative Works
          that You distribute, all copyright, patent, trademark, and
          attribution notices from the Source form of the Work,
          excluding those notices that do not pertain to any part of
          the Derivative Works; and

      (d) If the Work includes a "NOTICE" text file as part of its
          distribution, then any Derivative Works that You distribute must
          include a readable copy of the attribution notices contained
          within such NOTICE file, excluding those notices that do not
          pertain to any part of the Derivative Works, in at least one
          of the following places: within a NOTICE text file distributed
          as part of the Derivative Works; within the Source form or
          documentation, if provided along with the Derivative Works; or,
          within a display generated by the Derivative Works, if and
          wherever such third-party notices normally appear. The contents
          of the NOTICE file are for informational purposes only and
          do not modify the License. You may add Your own attribution
          notices within Derivative Works that You distribute, alongside
          or as an addendum to the NOTICE text from the Work, provided
          that such additional attribution notices cannot be construed
          as modifying the License.

      You may add Your own copyright statement to Your modifications and
      may provide additional or different license terms and conditions
      for use, reproduction, or distribution of Your modifications, or
      for any such Derivative Works as a whole, provided Your use,
      reproduction, and distribution of the Work otherwise complies with
      the conditions stated in this License.

   5. Submission of Contributions. Unless You explicitly state otherwise,
      any Contribution intentionally submitted for inclusion in the Work
      by You to the Licensor shall be under the terms and conditions of
      this License, without any additional terms or conditions.
      Notwithstanding the above, nothing herein shall supersede or modify
      the terms of any separate license agreement you may have executed
      with Licensor regarding such Contributions.

   6. Trademarks. This License does not grant permission to use the trade
      names, trademarks, service marks, or product names of the Licensor,
      except as required for reasonable and customary use in describing the
      origin of the Work and reproducing the content of the NOTICE file.

   7. Disclaimer of Warranty. Unless required by applicable law or
      agreed to in writing, Licensor provides the Work (and each
      Contributor provides its Contributions) on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or
      implied, including, without limitation, any warranties or conditions
      of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A
      PARTICULAR PURPOSE. You are solely responsible for determining the
      appropriateness of using or redistributing the Work and assume any
      risks associated with Your exercise of permissions under this License.

   8. Limitation of Liability. In no event and under no legal theory,
      whether in tort (including negligence), contract, or otherwise,
      unless required by applicable law (such as deliberate and grossly
      negligent acts) or agreed to in writing, shall any Contributor be
      liable to You for damages, including any direct, indirect, special,
      incidental, or consequential damages of any character arising as a
      result of this License or out of the use or inability to use the
      Work (including but not limited to damages for loss of goodwill,
      work stoppage, computer failure or malfunction, or any and all
      other commercial damages or losses), even if such Contributor
      has been advised of the possibility of such damages.

   9. Accepting Warranty or Additional Liability. While redistributing
      the Work or Derivative Works thereof, You may choose to offer,
      and charge a fee for, acceptance of support, warranty, indemnity,
      or other liability obligations and/or rights consistent with this
      License. However, in accepting such obligations, You may act only
      on Your own behalf and on Your sole responsibility, not on behalf
      of any other Contributor, and only if You agree to indemnify,
      defend, and hold each Contributor harmless for any liability
      incurred by, or claims asserted against, such Contributor by reason
      of your accepting any such warranty or additional liability.

   END OF TERMS AND CONDITIONS

   APPENDIX: How to apply the Apache License to your work.

      To apply the Apache License to your work, attach the following
      boilerplate notice, with the fields enclosed by brackets "[]"
      replaced with your own identifying information. (Don't include
      the brackets!)  The text should be enclosed in the appropriate
      comment syntax for the file format. We also recommend that a
      file or class name and description of purpose be included on the
      same "printed page" as the copyright notice for easier
      identification within third-party archives.

   Copyright [yyyy] [name of copyright owner]

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
   [See the License for the specific language governing permissions and]
   [limitations under the License.]
   
   


 @477447
 
















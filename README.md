# DreamColorESP
about
-----
Control WS2812b LEDs with ESP8266 (based on neopixel library).
A webserver is used to adjust Hue, Saturation and Brightness. 
These settings will be converted to rgb:
![alt text](data/DreamColorIndex.png)

Effects are implemented, several are base effect copied from
the Adafruit-Neopixel site (Strandtest, RainbowChasing etc.)
You can always do a request for extra effects to be implemented. 

Adjustable settings are:  

- Chip Controller (WS2811/WS2812B).
- Pixel Wiring (RGB/GRB/RGBW).
- Number of LEDs.
- Data PIN-number (default 12). 

Webserver is accessible thru Station-mode (connected with router) 
or Acces-Point-mode (direct connection). AP-mode password is "123456789"
and webserver can be accessed on "192.168.4.1". Here you can finish the
setup in "WiFi-settings" section.

MQTT is integrated and settings are adjustable thru mqtt-server,
command line looks lile this: 
{"EffectNum":1,"R":34,"G":55,"B":45,"Brightness":255,"Speed":50}.

MQTT-user and password can be switched on/off and are (of course)
adjustable.
MQTT-status updates are send, colors are send as rgb and hue, saturation
and 50% brightness, this because the webserver converts hsb to rgb. 
Status updates are send to adjustable outTopic name (default is "outTopic").

Webserver contains OTA-section, binary sketch file can be uploaded ota aswell
binary SPIFFS-file (containing HTML, CSS, and config files). Just select file
and click upload button, webserver will tell you if upload was a succes and page 
will be refreshed. 

Setup
-----
The first setup will be done thru Arduino-Ide, installation instructions for different 
platforms can found on Arduino website.
Instructions for the ESP8266 chip to be supported by the Arduino environment can be found 
here https://github.com/esp8266/Arduino.
To upload the sketch.bin and filesystem.bin files we gonna use the "webupdater" sketch.
This sketch can be found under "examples" in the "files" section. Search for "ESP8266HTTPUpdateServer"
and scroll down to "WebUpdater". Fill in your network credentials under "your-ssid" and "your-password"
and reset your ESP. Search for the ESP-device in your network, you can use "Fing"(android app)
, "ipconfig" in command prompt in windows or "arp -a" in linux terminal for that. Of course you can find 
the device in your router's main page too. Write down the IP-address and open "<IP-address>/update" in 
your browser.


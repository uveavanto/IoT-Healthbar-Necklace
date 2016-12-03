# IoT-Healthbar-Necklace
Physical Computing Project

This project is wearble device that you can control from your phone and the internet.

##Stuff it does;
- Lights up random colours
- Flashes blue when you send a tweet
- Lights up bright white when you send it a command (to be used as a flashlight)

##To build this project you will need:
- Adafruit Feather 32u4 Bluefruit LE
- Adafruit NeoPixel FeatherWing
- Male Header pins
- Female header pins (buying the ones made for the feather is best to keep the project slim)
- A smart phone

###--- Optional ---
- lipo battery
- JST jack cable (for the battery, if it doesn't already come with one)
- 2 push buttons
- Some Protoboard/stripboard/wires (to attach the other components to)
- Temprature sesnor
- Wires
- Some sort of case to keep it in when you're done
- A chain if you want to use it as a necklace

##Connect components up like so:

![Breadboard](/images/breadboard.png)

> * note it may be easier to stack the feather and featherwing
> * the battery is shown as not connected on the schematic, just plug it into the side of the feather, or use a usb cable for power

![Schematic](/images/schematic.png)

Images are made using Fritzing (source file is in the repo)

##Upload the code
Use the ardunio IDE to upload the code in the repo to the feather, make sure you select the right board and port
If you haven't used your feather before you'll need to instal the libraries from Adafruit. Check out [this guide](https://learn.adafruit.com/adafruit-feather-32u4-bluefruit-le/using-with-arduino-ide) for more info on that.
You'll need their [BLE libeary](https://learn.adafruit.com/adafruit-feather-32u4-bluefruit-le/installing-ble-library) aswell.

If everything is set up properly the neopixels should light up.
Once the code is uploaded keep the feather plugged into your computer and open up the serial monitor, it should give you a stream of numbers, the temprature readings from the sensor.
If you push the buttons, it will also print out here, press each one and both at the same time to make sure its all working.
- Button 1 will turn the LEDs off and on.
- Button 2 will switch between lighting modes.

##Connecting it to your phone and the internet
To get it online you'll need to first connect it to your phone
Download the bluefruit connect app for your [android](https://play.google.com/store/apps/details?id=com.adafruit.bluefruit.le.connect&hl=en_GB) or iPhone(https://itunes.apple.com/gb/app/adafruit-bluefruit-le-connect/id830125974?mt=8)
> Note i've only tested this on android, it's probably the same on iOS

1. Open up the app
2. Make sure you're feather is on
3. Click connect next to "Adafruit Bluefruit LE"
4. Select UART
5. Once you're connected it will give you a text field, type in `tweet` then press send.
6. The feather should flash blue. That means everything is working so far 😃  💙 
7. You can now control the feather from you're phone.

###but what about from the internet?
- You'll need to make an account on [io.adafruit](https://io.adafruit.com) and [IFTTT](https://ifttt.com)
- Create 2 feeds on io.adafruit, call them whatever you want.
- Click on MQTT at the top of the app
- Fill in the details: 
> Replace username/feed/feedname with your username and the names of your feeds
> For password press the scan code button then on io.adafruit go to settings then view AIO key.
```
Server
Address: io.adafruit.com
Port: 1883

Publish
UART RX username/feed/feedname1

Subscribe
Topic username/feed/feedname2

Advance
Username: username
Password: see quote above
```
- Now thats set up you can send commands from anywhere to your feather. 
> You can test this buy going to feedname2 clicking create data and typing ``tweet`` which should cause the text to apear on your phone and make your feather flash blue.

A breif overview of the design process/making off can be found [on this blog](http://physicalcomputingproject.tumblr.com/)

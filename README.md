
![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/imgonline-com-ua-twotoone-KfVhwaWcfr55M70.jpg)
**In this , we will measure  temperature and humidity using NCD  temperature and humidity sensor, Esp32, Ubidots.Also create gmail alerts using Ubidots.**

**Hardware** :
- **[ESP-32](https://store.ncd.io/product/esp32-iot-wifi-ble-module-with-integrated-usb/)**:The ESP32 makes it easy to use the Arduino IDE and the Arduino Wire Language for IoT applications. This ESp32 IoT Module combines Wi-Fi, Bluetooth, and Bluetooth BLE for a variety of diverse applications. This module comes fully-equipped with 2 CPU cores that can be controlled and powered individually, and with an adjustable clock frequency of 80 MHz to 240 MHz. This ESP32 IoT WiFi BLE Module with Integrated USB is designed to fit in all ncd.io IoT products.Monitor sensors and control relays, FETs, PWM controllers, solenoids, valves, motors and much more from anywhere in the world using a web page or a dedicated server.We manufactured our own version of the ESP32 to fit into NCD IoT devices, offering more expansion options than any other device in the world! Integrated USB port allows easy programming of the ESP32. The ESP32 IoT WiFi BLE Module is an incredible platform for IoT application development. This ESP32 IoT WiFi BLE Module can be programmed using Arduino IDE.

- **[IoT Long Range Wireless  Temperature And Humidity  Sensor](https://store.ncd.io/product/industrial-long-range-wireless-temperature-humidity-sensor/)**:Industrial Long Range Wireless Temperature Humidity Sensor. Grade with a Sensor Resolution of ±1.7%RH ±0.5°C .Up to 500,000 Transmissions from 2 AA Batteries.Measures -40°C to 125°C with Batteries that Survive these Ratings.Superior 2-Mile LOS Range & 28 miles with High-Gain Antennas.Interface to Raspberry Pi, Microsoft Azure, Arduino and More


- **[Long Range Wireless Mesh Modem with USB Interface](https://store.ncd.io/product/900hp-s3b-long-range-wireless-mesh-modem-with-usb-interface/)**

**Software Used:**
- Arduino IDE
- [Ubidot](https://ubidots.com/)

**Library Used:**
- PubSubClient Library
- Wire.h

# Arduino Client for MQTT
This library provides a client for doing simple publish/subscribe messaging with a server that supports MQTT

For more information about MQTT, visit [mqtt.org](http://mqtt.org/).
## Download
The latest version of the library can be downloaded from [GitHub](https://github.com/knolleary/pubsubclient/releases/tag/v2.7)
## Documentation
The library comes with a number of example sketches. See File > Examples > PubSubClient within the Arduino application.
Full [API Documentation](https://pubsubclient.knolleary.net/api.html).
## Compatible Hardware
The library uses the Arduino Ethernet Client api for interacting with the underlying network hardware. This means it Just Works with a growing number of boards and shields, including:

- Arduino Ethernet
- Arduino Ethernet Shield
- Arduino YUN – use the included YunClient in place of EthernetClient, and be sure to do a Bridge.begin() first
- Arduino WiFi Shield - if you want to send packets greater than 90 bytes with this shield, enable the [MQTT_MAX_TRANSFER_SIZE]  (https://pubsubclient.knolleary.net/api.html#configoptions) option in   PubSubClient.h.
- Sparkfun WiFly Shield – when used with [this](https://github.com/dpslwk/WiFly) library
- Intel Galileo/Edison
- ESP8266
- ESP32
The library cannot currently be used with hardware based on the ENC28J60 chip – such as the Nanode or the Nuelectronics Ethernet Shield. For those, there is an alternative library available.

# Wire Library
  The Wire library allows you to communicate with I2C devices, often also called "2 wire" or "TWI" (Two Wire Interface),can download  from [Wire.h](https://github.com/PaulStoffregen/Wire)
## Basic Usage
- Wire.begin()
  Begin using Wire in master mode, where you will initiate and control data transfers. This is the most common use when interfacing with   most I2C peripheral chips.

- Wire.begin(address)
  Begin using Wire in slave mode, where you will respond at "address" when other I2C masters chips initiate communication.
  
 ## Transmitting
 - Wire.beginTransmission(address)
   Start a new transmission to a device at "address". Master mode is used.

- Wire.write(data)
  Send data. In master mode, beginTransmission must be called first.

- Wire.endTransmission()
  In master mode, this ends the transmission and causes all buffered data to be sent.
  
## Receiving
- Wire.requestFrom(address, count)
  Read "count" bytes from a device at "address". Master mode is used.

- Wire.available()
  Retuns the number of bytes available by calling receive.

- Wire.read()
  Receive 1 byte.

# Steps to send data to labview  temperature and humidity platform using IoT Long Range Wireless  Temperature And Humidity Sensor and  Long Range Wireless Mesh Modem with USB Interface-

- First, we need a Labview utility application which is [ncd.io Wireless Temperature And Humidity Sensor.exe](https://github.com/ncdcommunity/Industrial-Wireless-IoT-Temperature-Humidity-Sensor) file on which data can be viewed.

- This Labview software will work with ncd.io wireless Temperature sensor only

- To use this UI, you will need to install following drivers Install run time engine from here [64bit](http://www.ni.com/download/labview-run-time-engine-2017/6821/en/)

- [32 bit](http://www.ni.com/download/labview-run-time-engine-2017/6822/en/)

- Install [NI Visa Driver](http://www.ni.com/download/ni-visa-run-time-engine/6647/en/)

- Install [LabVIEW Run-Time Engine]( http://www.ni.com/download/labview-run-time-engine-2017-sp1/7191/en/) and [NI-Serial Runtime]  (http://www.ni.com/download/ni-serial-17.0/6613/en/)

- [Getting started guide for this product.](https://ncd.io/long-range-iot-wireless-vibration-sensor-getting-started/)

##  Uploading the code  to ESP32 using Arduino IDE:
- **Download and include the PubSubClient Library and Wire.h Library.**
- **You must assign your unique Ubidots TOKEN, MQTTCLIENTNAME, SSID (WiFi Name) and Password of the available network.**
- **Compile and upload the  [temp_humidity.ino](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/temp_humidity.ino) code.**
- **To verify the connectivity of the device and the data sent, open the serial monitor.If no response is seen, try unplugging your ESP32 and then plugging it again. Make sure the baud rate of the Serial monitor is set to the same one specified in your code 115200.**

## Serial monitor output.
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/serialout.JPG)

## Making the Ubidot work:
- **Create the account on [Ubidot](https://ubidots.com/).**
- **Go to my profile and note down the token key which is a unique key for every account and paste it to your ESP32 code before uploading.**
- **Add a new device to your ubidot dashboard name esp32.**
  
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/device.JPG)

                       Click on devices and select devices in ubidot.

![alt tag](https://github.com/mjScientech/ESP32-AND-SI7021/blob/master/Device.JPG)

     Now you should see the published data in your Ubidots account, inside the device called "ESP32".

- **Inside device create new variable name sensor in which your temperature reading will be shown.**
![alt tag](https://github.com/mjScientech/ESP32-AND-SI7021/blob/master/variable.JPG)
                  
         
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/device2.JPG)

     Now you are able to view the Temperature and other sensors data which was previously viewed in serial monitor.This
     happened because the value of  different sensor readings  is passed as a string and store in
     variable and publish to variable inside  device esp32. 
- **Create dashboard in ubidots**
- Click on  add new dashboard.
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/dahboard%201.JPG)
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/dahboard2.JPG)
- Name your dashboard.
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/dahboard3.JPG)
- Now select Widget.
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/widget1.JPG)
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/widget5.JPG)
- Now select all required option and your widget will create.On which you can view your temp and humidity data.
 ![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/widget3.JPG)        
# OUTPUT
![alt tag](https://github.com/mjScientech/Esp32-Ubidots-Wireless-long-range-Temperature-And-Humidity/blob/master/widget4.JPG)

# Creating events in ubidots:

1. Select Events (from the Data dropdown).
![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event1.JPG)
2. Now click on create Event.
![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event2.JPG)

**Types of Events**
Ubidots support already integrated events to allow you to send Events, Alerts, and Notifications to those who need to know, when they need to know. 
Ubidots' prebuilt integrations include: 

- Email notifications
- SMS notifications
- Webhook events - [learn more](https://help.ubidots.com/user-guides/events-create-a-webhook)
- Telegram notifications
- Slack notifications - [learn more](https://help.ubidots.com/user-guides/events-slack-webhook-setup)
- Voice Call notifications - [learn more](https://help.ubidots.com/user-guides/events-voice-call-notifications)
- Back to Normal notification - [learn more](https://help.ubidots.com/user-guides/events-back-to-normal-events-and-notifications)
- Geofence notifications - [learn more](https://help.ubidots.com/user-guides/creating-a-geofence-alert)

3. Then choose a device and associating variable that indicates the devices' "values".
[![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event3.JPG)

4. Now selct a thresold value for your event to trigger and compare it to device values and also select time to trigger your event.

5. Now, create  action type by clicking plus sign.
[![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event4.JPG)

6.  Establish and configure which actions are to be executed and the message to the receiver: Send SMS, Email, Webhooks, Telegrams,     Phone Calls, SLACK, and webhooks to those who need to know.
[![alt tag](https://github.com/mjScientech/Creating-event-using-ubidots-and-Long-range-temperature-and-vibration-sensor/blob/master/event6.PNG)

7. Now fill all the required fields .
[![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event9.JPG)

[![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event5.JPG)

8. Determine the activity window the events may/may not be executed.
[![alt tag](https://github.com/ncdcommunity/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event6.JPG)
[![alt tag](https://github.com/ncdcommunity/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event7.JPG)

9. Confirm your Events.

# Output of event in your mail
[![alt tag](https://github.com/mjScientech/Creating-Alert-Using-Ubidots-ESP32-Temperature-and-Humidity-Sensor/blob/master/event8.JPG)





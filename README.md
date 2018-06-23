---
services: iot-hub
platforms: arduino
author: xshi
---

# IoT Hub Feather HUZZAH Client application 
[![Build Status](https://travis-ci.org/Azure-Samples/iot-hub-feather-huzzah-client-app.svg?branch=master)](https://travis-ci.org/Azure-Samples/iot-hub-feather-huzzah-client-app)

> This repo contains the source code to help you get familiar with Azure IoT using the Azure IoT Adafruit Feather HUZZAH ESP8266 Starter Kit. You will find the [lesson-based tutorials on Azure.com](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-arduino-huzzah-esp8266-get-started).

This repo contains an arduino application that runs on board feather HUZZAH ESP8266 with a DHT22 temperature&humidity sensor, and then sends these data to your IoT hub. At the same time, this application receives Cloud-to-Device message from your IoT hub, and takes actions according to the C2D command. 

## Create your Azure IoT hub
Follow [this page](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-arduino-huzzah-esp8266-get-started) to prepare your Azure IoT hub and register your device.

## Install board with your Arduino IDE
1. Start Arduino and open Preferences window.
2. Enter `http://arduino.esp8266.com/stable/package_esp8266com_index.json` into Additional Board Manager URLs field. You can add multiple URLs, separating them with commas.
3. Open Boards Manager from `Tools > Board` menu and install `esp8266 platform 2.2.0` or later
4. Select your ESP8266 board from `Tools > Board` menu after installation

## Install libraries
Install the following libraries from `Sketch -> Include library -> Manage libraries`

* `AzureIoTHub`
* `AzureIoTUtility`
* `AzureIoTProtocol_MQTT`
* `ArduinoJson`
* `DHT sensor library`
* `Adafruit Unified Sensor`

## Connect your sensor with your board
### Connect with a physical DHT22 sensor
You can follow the image to connect your DHT22 with your feather HUZZAH ESP8266.

![DHT22](https://docs.microsoft.com/en-us/azure/iot-hub/media/iot-hub-arduino-huzzah-esp8266-get-started/15_connections_on_breadboard.png)

### DON'T HAVE A PHYSICAL DHT22?
You can use the application to simulate temperature&humidity data and send to your IoT hub.
1. Open the `app/config.h` file.
2. Change the `SIMULATED_DATA` value from `false` to `true`.

## Configure and run sample application
Upload the `app.ino` to your board.

### Input your credential information
After you successfully upload the code to your board. You will see some prompt, input your credential information according to the prompts.

### Send Cloud-to-Device command
You can send a C2D message to your device. You can see the device prints out the message and blinks once receiving the message.

### Send Device Method command
You can send `start` or `stop` device method command to your feather HUZZAH ESP8266 to start/stop sending message to your IoT hub.

# ESP8266 to cloud - Connect Feather HUZZAH ESP8266 to Azure IoT Hub 
 			    	
between DHT22,DHT 11, Feather HUZZAH ESP8266, and IoT Hub]
 (https://docs.microsoft.com/en-us/azure/iot-hub/media/iot-hub-arduino-huzzah-esp8266-get-started/1_connection-hdt22-feather-huzzah-iot-hub.png)


## What you do Connect Adafruit Feather HUZZAH ESP8266 to an IoT hub that you create. 
Then you run a sample application on ESP8266 to collect the temperature and humidity data from a DHT22 sensor. 

![Azure website] (https://docs.microsoft.com/en-us/azure/includes/media/iot-hub-create-hub/create-iot-hub1.png)

 ## What you learn
 * How to create an IoT hub and register a device for Feather HUZZAH ESP8266
 * How to connect Feather HUZZAH ESP8266 with the sensor and your computer 
 * How to collect sensor data by running a sample application on Feather HUZZAH ESP8266 
 * How to send the sensor data to your IoT hub 

 ## What you need 
 ![Parts needed for the tutorial](https://docs.microsoft.com/en-us/azure/iot-hub/media/iot-hub-arduino-huzzah-esp8266-get-started/2_parts-needed-for-the-tutorial.png) 
 To complete this operation, you need the following parts from your Feather HUZZAH ESP8266 Starter Kit: 
 * The Feather HUZZAH ESP8266 board 
 * A Micro USB to Type A USB cable You also need the following things for your development environment: Note The Arduino IDE version used by Visual Studio Code extension for Arduino has to be version 1.6.8 or later. Earlier versions don't work with the AzureIoT library. The following items are optional in case you don't have a sensor. You also have the option of using simulated sensor data. * An Adafruit DHT22 temperature and humidity sensor * A breadboard * M/M jumper wires ## Create an IoT hub 
 1. Sign in to the [Azure portal](https://docs.microsoft.com/en-us/azure/includes/media/iot-hub-create-hub/create-iot-hub2.png). 
 2. Select **Create a resource** > **Internet of Things** > **IoT Hub**. 
 3. In the **IoT hub** pane, enter the following information for your IoT hub: 
 * **Subscription**: Choose the subscription that you want to use to create this IoT hub. * **Resource group**: Create a resource group to host the IoT hub or use an existing one. For more information.
 * **Region**: Select the closest location to you.
 * **Name**: Create a name for your IoT hub. If the name you enter is available, a green check mark appears. Important The IoT hub will be publicly discoverable as a DNS endpoint, so make sure to avoid any sensitive information while naming it. 
 4. Select **Next: Size and scale** to continue creating your IoT hub. 
 5. Choose your **Pricing and scale tier**. For this article, select the **F1 - Free** tier if it's still available on your subscription. For more information.
  
 6. Select **Review + create**. 
 7. Review your IoT hub information, then click **Create**. Your IoT hub might take a few minutes to create. You can monitor the progress in the **Notifications** pane. Now that you have created an IoT hub, locate the important information that you use to connect devices and applications to your IoT hub. In your IoT hub navigation menu, open **Shared access policies**. Select the
 **iothubowner** policy, and then copy the **Connection string---primary key** of your IoT hub.
 For more information, see [Control access to IoT Hub].
 Note You do not need this iothubowner connection string for this set-up tutorial. However, you may need it for some of the tutorials or different IoT scenarios after you complete this set-up. ![Get your IoT hub connection string]
 ## Register a device in the IoT hub for your device
 1. In your IoT hub navigation menu, open **IoT devices**, then click **Add** to register a device in your IoT hub. 
 ![Add a device in the IoT Devices of your IoT hub](https://docs.microsoft.com/en-us/azure/includes/media/iot-hub-get-started-create-hub-and-device/create-identity-portal.png) 
 2. Enter a **Device ID** for the new device. Device IDs are case sensitive. Important The device ID may be visible in the logs collected for customer support and troubleshooting, so make sure to avoid any sensitive information while naming it. 
 3. Click **Save**. 
 4. After the device is created, open the device from the list in the **IoT devices** pane.
 5. Copy the **Connection string---primary key** to use later. ![Get the device connection string](https://docs.microsoft.com/en-us/azure/includes/media/iot-hub-get-started-create-hub-and-device/device-connection-string.png)
 ## Connect Feather HUZZAH ESP8266 with the sensor and your computer In this section, you connect the sensors to your board. 
 Then you plug in your device to your computer for further use. 
 ### Connect a DHT22 temperature and humidity sensor to Feather HUZZAH ESP8266 Use the breadboard and jumper wires to make the connection as follows.
 If you don't have a sensor, skip this section because you can use simulated sensor data instead. 
 ![Connections reference](https://docs.microsoft.com/en-us/azure/iot-hub/media/iot-hub-arduino-huzzah-esp8266-get-started/8_connect-dht22-feather-huzzah.png) 

 For sensor pins, use the following wiring:  

 				    | Start (Sensor) | End (Board)      | Cable Color | 
 			    	| -------------- | ---------------- | ----------- | 
 			    	| VDD (Pin 31F)  | 3V (Pin 58H)     | Red cable   | 
 			    	| DATA (Pin 32F) | GPIO 2 (Pin 46A) | Blue cable  | 
 			    	| GND (Pin 34F)  | GND (PIn 56I)    | Black cable | 


 			    	For more information, see 
 			    	[Adafruit DHT22 sensor setup](https://docs.microsoft.com/en-us/azure/iot-hub/media/iot-hub-arduino-huzzah-esp8266-get-started/9_connect-feather-huzzah-computer.png )
 			    	 and [Adafruit Feather HUZZAH Esp8266 Pinouts]. 
 Now your Feather Huzzah ESP8266 should be connected with a working sensor. 
 
 ### Connect Feather HUZZAH ESP8266 to your computer As shown next, use the Micro USB to Type A USB cable to connect Feather HUZZAH ESP8266 to your computer. 
 




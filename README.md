# RAK4600 Arduino

## Introduction

RAK4600 LoRa Module includes an nRF52832 MCU and an SX1276 LoRa chip. Its RF communication capabilities (LoRa+BLE) make it suitable for a variety of applications in the IoT field.More details can be found in this：[RAK4600 LoRa Module - RAKwireless Knowledge Hub](https://doc.rakwireless.com/datasheet/rakproducts/rak4600-lora-module-datasheet).



## BSP Installation

The following describes how the module builds the development environment in Arduino IDE and runs the demo project.


1. What is Arduino?
     If you know little about Arduino, please have a look below: 
     [https://www.arduino.cc/](https://www.arduino.cc/) 

2. You have known Arduino.  Install the IDE first: 
     [https://www.arduino.cc/en/Main/Software](https://www.arduino.cc/en/Main/Software) 

3. What boards support is used? 
     RAK4600 is based on nrf52832, therefore Arduino Core for Adafruit Bluefruit nRF52 Boards is suitable for RAK4600. 

     Refer to the following link to install Adafruit Bluefruit nRF52 in Arduino.
     [https://github.com/adafruit/Adafruit_nRF52_Arduino](https://github.com/adafruit/Adafruit_nRF52_Arduino) 

     After installation, select the board according to the figure below.

     ![nRF52](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/Select%20development%20board.png) 

4. Download the gpio map of RAK4600 from:
   [https://github.com/RAKWireless/RAK4600_Arduino](https://github.com/RAKWireless/RAK4600_Arduino) 
   It contains gpio maping, serial tool, demo project and Softdevice hex.

   - feather_nrf52832: GPIO maping of RAK4600.
   - Demo: lorawan and ble demo project.
   - serial tool: serial tool on PC.
   - s132_nrf52_6.1.1_softdevice.hex: Sotfdevice hex.

5. Replace your folder with our folder `feather_nrf52832`, your file path maybe 

   > %APPDATA%\Local\Arduino15\packages\adafruit\hardware\nrf52\0.14.6\variants

6. The last step is download the softdevice hex file `s132_nrf52_6.1.1_softdevice.hex` to RAK4600 with Jlink or DAP, etc.

At this point, the development environment is ready.



## BLE example

Adafruit provides many BLE demos, we open them from File->Examples.

1. Open one of the demos, File->Examples->Adafruit Bluefruit nRF52 Libraries->peripheral->bleuart.

![Project](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/ble_examples.png)

2. Click "Sketch->Export complied Binary" to compile project and copy binary file to current directory.

![Compile](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/Compiling%20project.png) 

3. Download the hex file to RAK4600, View the log through the serial port on the PC.

4. We need to install an app in the mobile phone to connect with the module.

   Refer to the following link for installation. [nRF Connect for Mobile - nordicsemi.com](https://www.nordicsemi.com/Software-and-tools/Development-Tools/nRF-Connect-for-mobile)  

5. After the installation is completed, open Bluetooth and app. Scan and connect a device named "bluefruit 52". You can communicate with your device via Bluetooth.

![ble_scan](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/ble_scan.png) 

6. Here are the logs of mobile phone and PC。

![ble_mobile_app](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/ble_mobile_app.jpg) 

![ble_pc_tool](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/ble_pc_tool.png) 



## LoRa example

RAK4600 uses open source protocol stack to realize lorawan communication.

1. What lorawan lib is used?

     LMIC is a LoraWAN-MAC-in-C library, adapted to run under the Arduino environment.

     Refer to the following link to install it.

     [https://github.com/mcci-catena/arduino-lmic](https://github.com/mcci-catena/arduino-lmic) 

![lmic](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/LMIC.png) 

2. Open the demo project `RAK4600_LoRaWAN_Demo.ino` in Arduino IDE. Modify the device parameters to your own.

     Notice:The APPEUI and DEVEUI must be in **little-endian format**.

![Device Parameter](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/LoRa_OTAA_Parameters.png) 

3. Click "Sketch->Export complied Binary" to compile project and copy binary file to current directory.

![Compile](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/Compiling%20project.png) 

4. Download the hex file to RAK4600. When download ok, the RAK4600 will be auto join LoRaWAN and send data.

![Run information](https://github.com/RAKWireless/RAK4600_Arduino/raw/master/image/running%20information.png) 



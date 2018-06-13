# Screen
## Intro
Display your messages, UI, and LoRa content on the full color 1.8" TFT LCD.  The screen has a 160 x 128 pixels resolution and the ST7735R is easy to integrate with over SPI.  We've chosen a screen that is well documented on the Adafruit website and has many pre-written libraries to make getting started even easier. We've added a trasnsitor to the circuit to control power to the display to help save on battery power when the screen is not needed. 

## Working with the Screen
** The screen runs at 3.3 volts, so we have added the TXB0104 level shifter from the AtMega 2560 mcu to handle high speed bi-directional data. In order to transmit SPI data correction, remember to set the TXB0104's OE pin low upon startup, and then set the pin high to enable level shifted SPI communication.

**  Power to the screen is controlled via a AO2415A high side mosfet.  When the mosfet's control pin is set high, power to the screen will be disconnected. When the mosfet's control pin is set low, the screen will receieve power and turn on.  Use this to put mosfet to put the device into sleep mode when you do not screen running.

** The RFM95 radio, trackpad, and microSD card slot are also connected to the level shifter SPI lines, so remember to set this device select pins accordingly to ensure they do not interfere with your screen communication. 

After you've verified the notes above, getting started with the screen is relatively easy.  We suggest starting with the Arduion TFT library that we have outlined below.  We've included one example displaying text, and a second example displaying a .bmp from the sd card slot.

## Screen library
Link to library

link to library


## Screen example code
Here is an example of the screen displaying text:
< example code snipped where the screen displays text > 

For a feature rich screen, try loading images from the SD card as well:
< example code snippet where the screen displays a bitmap >

## External Documentation
- link to adafruit libraries
- 
- link replacement screen: https://www.adafruit.com/product/618?gclid=CjwKCAjwgYPZBRBoEiwA2XeupcHyJD6ue7QIIfes3cSHH3tqSKE2JgLOSNm2Afju_Abxn2sevnob8RoChVwQAvD_BwE

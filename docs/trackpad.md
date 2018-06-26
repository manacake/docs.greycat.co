# Trackpad
## Intro
The trackpad is another Shenzhen e-waste find.  These leftover 8520 trackpads fit perfectly into the 9700 keypad and with a bit of help from some Arduino forums, we were able to hobble together some functioning trackpad code.  It turns out, this device is relatively easy to communicate with over SPI. The devices returns changes in x and y coordinates when the user swipes across the surface of the device.  We've included some code that conveniently converts this data into a clean 'swipe right' or 'swipe left' when an event is detected.

## Trackpad hardware
The trackpad is from the Blackberry 8250.  It's likely to have some version of the Agilent ADNS-3060 sensor inside of it commonly used for optical mice.  A flexible PCB breakouts out to a 20 pin Hirose connector, which have designed into our PCB.

## Working with the Screen
::: tip Heads Up!
The trackpad runs at 3.3 volts, so we have added the TXB0104 level shifter from the AtMega 2560 mcu to handle high speed bi-directional data. In order to transmit SPI data correction, remember to set the TXB0104's OE pin low upon startup, and then set the pin high to enable level shifted SPI communication.
:::

::: danger !
The RFM95 radio, screen, and microSD card slot are also connected to the level shifter SPI lines, so remember to set these devices' chip select pins accordingly to ensure they do not interfere with your screen communication.
:::

After you've verified the notes above, you can get started handling data from the trackpad.  We suggest starting with the basic code snippets that we have included below.  How far you want to take it is up to you as this is by the far the most complicated and least documented device in the design.

## Trackpad library
Currently there is no library written for the trackpad we use (but let us know if you come across one). As of now, we can access the registers of the trackpad chip using the Arduino SPI library.

We can define two basic functions to read from and write to the trackpad CPU register. See code snippet below.

## Trackpad example code
``` cpp
#include <SPI.h>

#define TP_RESET     25
#define TP_SHUTDOWN  24
#define TP_CS        47
#define TP_BUTTON    23
#define SD_CS        22
#define TFT_CS       27
#define RFM_CS       10
#define LVL_SHIFT_EN  2

void setup() {
  pinMode(TP_SHUTDOWN, OUTPUT);
  pinMode(TP_RESET, OUTPUT);
  pinMode(TP_CS, OUTPUT);
  pinMode(TP_BUTTON, INPUT);
  pinMode(LVL_SHIFT_EN, OUTPUT);

  // Turn off other SPI
  // TODO: confirm if we really need to do this o-O
  digitalWrite(SD_CS, HIGH);
  digitalWrite(TFT_CS, HIGH);
  digitalWrite(RFM_CS, HIGH);

  digitalWrite(LVL_SHIFT_EN, LOW);
  delay(1000);
  digitalWrite(LVL_SHIFT_EN, HIGH);

  // ADNS-3060 does not perform an internal power up self-reset
  // Force a reset
  digitalWrite(TP_RESET, HIGH);
  delay(1000);
  digitalWrite(TP_RESET, LOW);

  digitalWrite(TP_SHUTDOWN, LOW);
  // Ensure trackpad is not listening
  digitalWrite(TP_CS, HIGH);

  SPI.begin();

  // Wait for serial monitor to open before we continue setup
  Serial.begin(115200);
  while (!Serial);

  Serial.print("Product ID: ");

  writeRegister(0x00, 0x00);
  uint8_t productID = readRegister(0x00);
  Serial.println(productID);
}

uint8_t motion = 0;

void loop() {
  motion = readRegister(0x02);

  // Motion has occurred on the trackpad
  if (motion > 127) {
    int8_t dx = readRegister(0x03);
    int8_t dy = readRegister(0x04);
    Serial.print("x: ");
    Serial.println(dx);
    Serial.print("y: ");
    Serial.println(dy);
  }
}

byte readRegister(uint8_t address) {
  byte data;
  // Make trackpad listen
  digitalWrite(TP_CS, LOW);

  // Write the address of the register we want to read from
  // Most significant byte should be 0 here to indicate read operation
  SPI.transfer(address);

  // Read the data
  data = SPI.transfer(0x00);
  delayMicroseconds(50);

  // Make trackpad stop listening
  digitalWrite(TP_CS, HIGH);

  return data;
}

void writeRegister(uint8_t address, uint8_t data) {
  // Set most significant byte high to indicate write operation
  address |= 0x80;
  digitalWrite(TP_CS, LOW);

  // Send the address of the register we want to write to
  SPI.transfer(address);

  // Write data to register
  SPI.transfer(data);
  delayMicroseconds(50);

  // Make trackpad stop listening
  digitalWrite(TP_CS, HIGH);
}
```

## Related Documentation
[Arduino SPI Library](https://www.arduino.cc/en/Reference/SPI)

[Agilent ADNS-3060 Datasheet](http://pdf.datasheetcatalog.com/datasheet2/9/0opeydz8pk55dp30dczkyk0ttzpy.pdf)

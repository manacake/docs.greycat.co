# Radio
## Intro
At the core of the Lora Text Dev Kit is the RFM95W 915mhz radio module!  We are very excited about what opporunuties the LoRa 915mhz ISM band offers.  We envision peer-to-peer communication, a portable in-the-field debug console, or simply local remote control for your LoRa control sensors and switches around your home.  We've added an edge mount SMA connector and included a 915mhz "shorty" external antenna to increase the range of these devices.

## Getting started with the Radio

::: danger !
The trackpad, screen, and microSD card slot are also connected to the SPI lines, so remember to set the chip select pins accordingly to ensure they do not interfere with your radio communication.
:::

::: warning !
Power to the radio is controlled via an AO2415A high side mosfet.  When the mosfet's control pin is set high, power to the radio will be disconnected. When the mosfet's control pin is set low, the radio will receive power and turn on.  Use this mosfet to put the device into sleep mode when you do not radio running.
:::

After you've verified the notes above, you can get started with radio communication!  We suggest starting with the basic code snippets that we have included below.  How far you want to take it is up to you as this is by far the most exciting component on the project. There are tons of unexplored opporutunities in this field that we feel our PCB design enables!

## Radio library
We use the RadioHead library written by Mike McCauley to interface with the RFM95 radio module on our board. There are a bunch of great [examples](http://www.airspayce.com/mikem/arduino/RadioHead/examples.html) with this library in use.

## Radio example code
*Setup a server that listens for messages*
``` cpp
#include <RH_RF95.h>

#define RFM_CS  10
#define RFM_INT 3
#define RFM_RST 49
#define RFM_PWR_EN 5

// Setup instance of the radio driver
RH_RF95 rf95(RFM_CS, RFM_INT);

void setup() {
  pinMode(RFM_RST, INPUT);
  pinMode(RFM_PWR_EN, OUTPUT);
  // This allows the radio module to get power
  digitalWrite(RFM_PWR_EN, LOW);

  // Pause setup until serial monitor is open
  Serial.begin(9600);
  while (!Serial);

  // Initialize radio module
  if (!rf95.init()) Serial.println("Radio init failed");
}

void loop() {
  // If there is a message available to us
  if (rf95.available()) {
    uint8_t buf[RH_RF95_MAX_MESSAGE_LEN];
    uint8_t len = sizeof(buf);

    // Receive message into buf
    if (rf95.recv(buf, &len)) {
      Serial.print("Got message: ");
      Serial.println((char*) buf);
    }
  }
}
```

*Setup a client that spams messages*
``` cpp
#include <RH_RF95.h>

#define RFM_CS  10
#define RFM_INT 3
#define RFM_RST 49
#define RFM_PWR_EN 5

// Setup instance of the radio driver
RH_RF95 rf95(RFM_CS, RFM_INT);

void setup() {
  pinMode(RFM_RST, INPUT);
  pinMode(RFM_PWR_EN, OUTPUT);
  // This allows the radio module to get power
  digitalWrite(RFM_PWR, LOW);

  // Pause setup until serial monitor is open
  Serial.begin(9600);
  while (!Serial);

  // Initialize radio module
  if (!rf95.init()) Serial.println("Radio init failed");
}

void loop() {
  uint8_t data[] = "Hello are you there?";
  rf95.send(data, sizeof(data));
  rf95.waitPacketSent();
  delay(1000);
}
```

## Related Documentation
[RH_RF95 Class Reference](http://www.airspayce.com/mikem/arduino/RadioHead/classRH__RF95.html)

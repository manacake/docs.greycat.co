# Getting Started
## Intro
Hello! And welcome to the wonderful world of local peer-to-peer communication.  In our opinion, we've hobbled together a pretty interesting Dev Kit, and we are SO EXCITED to share it with you.  Portable LoRa console, remote control for all of your LoRa connected devices, or peer-to-peer off grid texting device, we think there are a lot of interesting devices that can come out of this project. We can't wait to see what you come up with!  The docs are a work in progress, and we update them daily. If you don't see the information you want, just send us a purrr at meow@greycat.co with your request and we'll see what we can do!

## What's in your kit!?
Your kit comes with everything you need to start sending an receiving messages. That includes:

- **PCBA**: At the core of the circuit board is the AtMega2560 mcu.  If you've ever used the Arduino Mega, it's the same chip!  From there we've included all of the power management necessities to run of battery and circuitry for adding a TFT LCD, the RFM95 radio module, a trackpad, and a keypad. Check out our <a href="/blockDiagram.html">Block Diagram</a> to see what's going on at a high level.

<img src="./assets/devKitPcbBack.png" alt="PCB (back side)">
<img src="./assets/devKitPcbFront.png" alt="PCB (front side)">

- **1.8" LCD TFT screen**

<img src="./assets/devKitScreen.png" alt="Screen" style="width: 300px;">

- **Keypad**
- **Metal Dome Keypad Array**

<img src="./assets/devKitKeypad.png" alt="Keypad">

- **915mhz antenna**

<img src="./assets/devKitAntenna.png" alt="Antenna">

- **Trackpad**

<img src="./assets/devKitTrackpad.png" alt="Trackpad" style="width: 300px;">

## How to flash
We've designed the PCB to be as easy to use as we could. The board is Arduino compatible and you can flash the device the same way you would flash and Arduino Mega using the Arduion IDE. Here is a step by step for using the Arduino IDE:

1) Plug device into computering using a microUSB cable (make sure you are using a data capable microUSB cable).

2) In the Arduino IDE select Tools > Boards > Arduino/Genuino Mega or Mega2560

3) In the Arduion IDE select Tools > Processor > Mega2560

4) In the Arduino IDe select Tools > Port > COM**(Arduino/Genuino Mega or Mega 2560)

5) Press the Upload Code button in the Arduino IDE

::: warning
The DTR circuitry is a little off in the first version of this PCB. In order to work correctly, plug in the dev kit and quickly press the upload button.  If you plug in the device, and wait several seconds, and then hit upload, the device will not flash correctly.  This error is being fixed on the next version of the PCB. If you would like to know more about this error, feel free to send a purr to meow@greycat.co
:::

## Hello world!
Now that your device is set up, lets send the hello, world!

We've included a simple code snippet that just sends serial commands back to your main computer.  So plug in the device, upload the code, open your serial monitor (double check the baudrate), and see if your LoRa Text Dev Kit talks back!

```cpp
void setup() {
  Serial.begin(115200);
  while (!Serial);
}

void loop() {
  Serial.println("Hello World!");
  delay(2000);
}
```

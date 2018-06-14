# Keypad
## Intro
We reminisce mechanical cell phone keypads. In our opinion, the physical clickiness of the metal snap dome was never replaced by the haptic vibrators or touch screens. So we contacted our buddies in the cell phone repair markets, rummaged through some Shenzhen e-waste, and discovered a gold mine: recycled qwerty keypads!  We chose our favorite and worked it into the PCB design.

## Keypad hardware
The full QWERTY keypad is off of the Blackberry 9700. The kit comes with the metal dome switch array that is placed onto the PCB AND the the 9700 keypad that is placed over the top. The keypad pressure fits onto the pcb, or can be held in place by a case.  The result is an extremely satisfying button press.

## Keypad pin function
The circuit board design is a simple rows and columns matrix.  Columns are pulled high to 5 volts through a 10K resistor and rows are grounded. When the metal snap dowm is compressed from a keyboard press, the row and column is triggered and the keypad library recognizes the keypad press.

[insert rows and columns schematic]

## Keypad library
We can use a keypad library written for Arduino by Mark Stanley and Alexander Brevig. The library is included in the Arduino IDE (version 1.6.2 or later). This library helps manage the matrix style keypad button presses for our board. There are a bunch of great [examples](https://github.com/Chris--A/Keypad/tree/master/examples) (in the Arduino IDE after you've installed the Keypad library through the library manager).

## Keypad example code
Print pressed keys in the serial monitor:
``` cpp
#include <Keypad.h>

const uint8_t ROWS = 5;
const uint8_t COLS = 10;
char keypadKeys[ROWS][COLS] = {
  {'0', '0', '1', '2', '0', '0', '3', '4', '0', '0'},
  {'q', 'w', 'e', 'r', 't', 'y', 'u', 'i', 'o', 'p'},
  {'a', 's', 'd', 'f', 'g', 'h', 'j', 'k', 'l', '~'},
  {'>', 'z', 'x', 'c', 'v', 'b', 'n', 'm', '$', '<'},
  {'0', '0', '0', '^', '0', ' ', '5', '^', '0', '0'}
};

// Connect to the row pinouts of the keypad
uint8_t rowPins[ROWS] = {30, 31, 32, 33, 34};

// Connect to the column pinouts of the keypad
uint8_t colPins[COLS] = {35, 36, 37, 40, 41, 38, 42, 44, 45, 46};

// Initialize the keypad object
Keypad keypad(makeKeymap(keypadKeys), rowPins, colPins, ROWS, COLS);

void setup(){
  keypad.addEventListener(keyEvent);
}

char key;
char buf[2] = {' ', '\0'};
uint8_t keyState;

void loop(){
  key = keypad.getKey();
}

void keyEvent(KeypadEvent key) {
  keyState = keypad.getState();

  switch (keyState) {
    case PRESSED:
      if (key != '0') {
        // Print valid keys only
        buf[0] = key;
        Serial.print(buf);
      }
      break;
  }
}
```

## Related documentation
[Keypad Library for Arduino](https://playground.arduino.cc/Code/Keypad)

[Keypad Library Source Code and Examples](https://github.com/Chris--A/Keypad)

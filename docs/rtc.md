# Real Time Clock

## Intro
We went with the classic, easy to use DS1307 real time clock for all of your time keeping needs.  Set it once, and forget about it as long as a battery is attached.

## Pinout
We've tied the DS1307 module to the I2C data lines of the AtMega2560.  So no need to worry too much about the pinout.

## Library
We can use the date and time functions from the Wire library to interact with the real time clock module.

## Example Code
``` cpp
#include <Wire.h>
#include "RTClib.h"

// Setup instance of the real time clock
RTC_DS1307 RTC;

void setup () {
  // Pause setup until serial monitor is open
  Serial.begin(9600);
  while (!Serial);

  RTC.begin();
  delay(500);

  // RTC not running!
  if (!RTC.isrunning()) {
    // Sets the RTC to the date & time this file was compiled
    RTC.adjust(DateTime(F(__DATE__), F(__TIME__)));
  }
}

void loop () {
  DateTime now = RTC.now();
  Serial.print(now.year(), DEC);
  Serial.print('/');
  Serial.print(now.month(), DEC);
  Serial.print('/');
  Serial.print(now.day(), DEC);
  Serial.print(' ');
  Serial.print(now.hour(), DEC);
  Serial.print(':');
  Serial.print(now.minute(), DEC);
  Serial.print(':');
  Serial.print(now.second(), DEC);
}
```

## Related Documentation
[Wire Library](https://www.arduino.cc/en/reference/wire)

# Pin Definitions

## Pin Definition Table

| Device        | Name              | Arduino Pin | AtMega2560 Pin | AtMega 2560 Port | Description |
| --------------|:-----------------:|:-----------:|:--------------:|:----------------:| -------------------------------------------------------- |
| AtMega2560    | MOSI              | 51          | 21             | PB2              | SPI communication line |
| AtMega2560    | MISO              | 50          | 22             | PB3              | SPI commuication line |
| AtMega2560    | RESET             |             | 30             | RESET            | SPI Reset |
| AtMega2560    | SCK               | 52          | 20             | PB1              | SPI Serial Clock |
| Level Shifter | LVL_SHIFT_EN  | 2           | 6              | PE4              | Controls OE Pin |
| Screen        | TFT_PWR_EN     | 4           | 1              | PG5              | Controls high side mosfet controlling LED voltage. Set low to enable power |
| Screen        | TFT_RESET         | 29          | 71             | PA7              | LCD Reset Pin |
| Screen        | TFT_DC            | 28          | 72             | PA6              | LCD DC Pin |
| Screen        | TFT_CS            | 27          | 73             | PA5              | LCD Chip Select Pin |
| RFM95         | RFM_PWR_EN         | 5           | 5              | PE3              | Controls high side mosfet controlling RFM95 voltage. Set low to enable power |
| RFM95         | RFM_INT               | 3           | 7              | PE5              | RFM95 interrupt pin |
| RFM95         | RFM_CS            | 10          | 23             | PB4              | RFM95 chip select pin |
| RFM95         | RFM_RESET         | 49          | 35             | PL0              | RFM95 reset pin |
| DS1307        | SDA               | 20          | 44             | PD1              | Real Time Clock I2C Data line |
| DS1307        | SCL               | 21          | 43             | PD0              | Real Time Clock I2C Clock line |
| Trackpad      | TP_RESET          | 25          | 75             | PA3              | Trackpad Reset Line |
| Trackpad      | TP_SHUTDOWN       | 24          | 76             | PA2              | Trackpad Shutdown Line |
| Trackpad      | TP_CS             | 47          | 37             | PL2              | Trackpad Chip Select Pin |
| Trackpad      | TP_BUTTON         | 23          | 77             | PA1              | Input pin detecting mechanical press of trackpad button |
| Trackpad      | TP_MOTION         | 48          | 36             | PL1              | Trackpad Motion Pin |
| SD Card       | SD_CS             | 22          | 78             | PA0              | microSD card Chip Select Pin |
| SD Card       | DET_CARD          | 39          | 70             | PG2              | Input pin pulls high when card is inserted |
| Keypad        | ROW_1             | 30          | 60             | PC7              | Keypad Row Pin |
| Keypad        | ROW_2             | 31          | 59             | PC6              | Keypad Row Pin |
| Keypad        | ROW_3             | 32          | 58             | PC5              | Keypad Row Pin |
| Keypad        | ROW_4             | 33          | 57             | PC4              | Keypad Row Pin |
| Keypad        | ROW_5             | 34          | 56             | PC3              | Keypad Row Pin |
| Keypad        | COL_1             | 35          | 55             | PC2              | Keypad Column Pin |
| Keypad        | COL_2             | 36          | 54             | PC1              | Keypad Column Pin |
| Keypad        | COL_3             | 37          | 53             | PC0              | Keypad Column Pin |
| Keypad        | COL_4             | 40          | 52             | PG1              | Keypad Column Pin |
| Keypad        | COL_5             | 41          | 51             | PG0              | Keypad Column Pin |
| Keypad        | COL_6             | 38          | 50             | PD7              | Keypad Column Pin |
| Keypad        | COL_7             | 42          | 42             | PL7              | Keypad Column Pin |
| Keypad        | COL_8             | 44          | 40             | PL5              | Keypad Column Pin |
| Keypad        | COL_9             | 45          | 39             | PL4              | Keypad Column Pin |
| Keypad        | COL_10            | 46          | 38             | PL3              | Keypad Column Pin |
| Battery       | BAT_PIN           | A7          | 90             | PF7              | Analog Voltage Read on VBAT | 

## Arduino Full Pin Defiintion Code Snippet
``` cpp
//include libraries

//pin defintions
#define LVL_SHIFT_EN 2

#define TFT_PWR_EN 4
#define TFT_RESET 29
#define TFT_DC 28
#define TFT_CS 27

#define RFM_PWR_EN 5
#define RFM_INT 3
#define RFM_CS 10

#define TP_RESET 25
#define TP_SHUTDOWN 24
#define TP_CS 47
#define TP_BUTTON 23
#define TP_MOTION 48

#define SD_CS 22
#define DET_CARD 39

#define ROW_1 30
#define ROW_2 31
#define ROW_3 32
#define ROW_4 33
#define ROW_5 34
#define COL_1 35
#define COL_2 36
#define COL_3 37
#define COL_4 40
#define COL_5 41
#define COL_6 38
#define COL_7 42
#define COL_8 44
#define COL_9 45
#define COL_10 46

#define BAT_PIN A7
```

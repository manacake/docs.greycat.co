# Pin Definitions

## Pin Definition Table

| Device        | Name              | Arduino Pin | AtMega2560 Pin | AtMega 2560 Port | Description |
| --------------|:-----------------:|:-----------:|:--------------:|:----------------:| -------------------------------------------------------- |
| AtMega2560    | MOSI              |             |                |                  | SPI communication line |
| AtMega2560    | MISO              |             |                |                  | SPI commuication line |
| AtMega2560    | RESET             |             |                |                  | SPI Reset |
| AtMega2560    | SCK               |             |                |                  | SPI Serial Clock |
| Level Shifter | Level_Shifter_EN  |             |                |                  | Controls OE Pin |
| Screen        | Screen_PWR_EN     |             |                |                  | Controls high side mosfet controlling LED voltage. Set low to enable power |
| Screen        | TFT_Reset         |             |                |                  | LCD Reset Pin |
| Screen        | TFT_DC            |             |                |                  | LCD DC Pin |
| Screen        | TFT_CS            |             |                |                  | LCD Chip Select Pin |
| RFM95         | RF_PWR_EN         |             |                |                  | Controls high side mosfet controlling RFM95 voltage. Set low to enable power |
| RFM95         | INT               |             |                |                  | RFM95 interrupt pin |
| RFM95         | RFM_CS            |             |                |                  | RFM95 chip select pin |
| RFM95         | RFM_RESET         |             |                |                  | RFM95 reset pin |
| DS1307        | SDA               |             |                |                  | Real Time Clock I2C Data line |
| DS1307        | SCL               |             |                |                  | Real Time Clock I2C Clock line |
| Trackpad      | TP_RESET          |             |                |                  | Trackpad Reset Line |
| Trackpad      | TP_SHUTDOWN       |             |                |                  | Trackpad Shutdown Line |
| Trackpad      | TP_CS             |             |                |                  | Trackpad Chip Select Pin |
| Trackpad      | TP_BUTTON_DETECT  |             |                |                  | Input pin detecting mechanical press of trackpad button |
| Trackpad      | TP_MOTION         |             |                |                  | Trackpad Motion Pin |
| SD Card       | SD_CS             |             |                |                  | microSD card Chip Select Pin |
| SD Card       | DET_CARD          |             |                |                  | Input pin pulls high when card is inserted |
| Keypad        | ROW_1             |             |                |                  | Keypad Row Pin |
| Keypad        | ROW_2             |             |                |                  | Keypad Row Pin |
| Keypad        | ROW_3             |             |                |                  | Keypad Row Pin |
| Keypad        | ROW_4             |             |                |                  | Keypad Row Pin |
| Keypad        | ROW_5             |             |                |                  | Keypad Row Pin |
| Keypad        | COL_1             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_2             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_3             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_4             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_5             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_6             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_7             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_8             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_9             |             |                |                  | Keypad Column Pin |
| Keypad        | COL_10            |             |                |                  | Keypad Column Pin |

## Arduino Full Pin Defiintion and Setup Code Snippet

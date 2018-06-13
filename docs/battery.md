# Power Management
## Intro

At the core of power managment is the Texas Instrument BQ24075 IC. The BQ24075 is an integrated Li-ion linear charger and system power path mangement device targeted at space-limited applications.  The PMIC provides VSYS with 5V from USB if plugged in, or battery voltage is USB is not plugged in.  The PMIC automatically handles charging of the battery while USB is plugged in as well.  Detailed information can be found in the related documents linked below. 
 

## How to read BAT voltage
Battery management can be done with a simple analog read of the batery's voltage line.  Feel free to use this voltage readings to write a bit of battery management wizardy like display a battery status indicator, or perform an automatic sleep state turning off the radio, screen, and trackpad when the battery reaches a certain voltage.

## Example Battery Managment Code Snippet:

[enter battery voltage read code]

## Related Documentation:

BQ24075: [http://www.ti.com/product/BQ24075-Q1]
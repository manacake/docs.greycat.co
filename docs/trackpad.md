# Trackpad
## Intro
The trackpad is another Shenzhen e-waste find.  These leftover 8520 trackpads fit perfectly into the 9700 keypad and with a bit of help from some arduino forums, we were able to hobble together some functioning trackpad code.  It turns out, this device is relatively easy to communicate with over SPI with the devices returning changes in x and y cordinates when the user swipes across the surface of the device.  We've included some conviently converts this data into a clean 'swipe right' or 'swipe left' when an event is detected. 

## Trackpad hardware
The trackpad is from the Blackberry 8250.  It's likely to have some version of the Agilent ADNS-3060 sensor inside of it common used for optimical mice.  A flexible pcb breakouts out to a 20 pin Hirose connector, which can have designed into our PCB. 

## Working with the Screen
::: tip Heads Up!
The trackpad runs at 3.3 volts, so we have added the TXB0104 level shifter from the AtMega 2560 mcu to handle high speed bi-directional data. In order to transmit SPI data correction, remember to set the TXB0104's OE pin low upon startup, and then set the pin high to enable level shifted SPI communication.
:::

::: danger !
The RFM95 radio, screen, and microSD card slot are also connected to the level shifter SPI lines, so remember to set this device select pins accordingly to ensure they do not interfere with your screen communication.
:::

After you've verified the notes above, you can get started handing data from the trackpad.  We suggest starting with the basic code snippets that we have included below.  How far you want to take it is up to you as this is by the far the most complicated and least documented device in the design.

## Trackpad library
Gummies topping cupcake oat cake cake sweet roll. Gummies marshmallow pudding pudding apple pie ice cream muffin. Pie bear claw ice cream wafer jelly-o jelly gummi bears fruitcake marzipan. Chupa chups cake candy canes soufflé pastry. Biscuit topping halvah toffee macaroon candy canes. Candy canes lemon drops croissant. Chocolate bar cake donut croissant caramels. Pastry chupa chups chocolate chocolate cake soufflé cotton candy. Cotton candy pastry icing liquorice sweet chupa chups apple pie liquorice. Ice cream ice cream cookie liquorice. Ice cream danish candy candy canes. Soufflé toffee cookie apple pie carrot cake tiramisu bonbon. Icing caramels candy canes cheesecake.

## Trackpad example code
Caramels gingerbread gingerbread liquorice cotton candy apple pie jujubes cupcake tiramisu. Wafer sugar plum gingerbread chocolate. Icing pudding gummi bears dragée muffin pudding bonbon. Candy gingerbread topping apple pie fruitcake. Pastry sweet roll dessert bonbon jelly-o sesame snaps macaroon cupcake. Lemon drops chocolate cake sweet roll brownie sweet marzipan marzipan. Jujubes bear claw gummi bears liquorice carrot cake muffin muffin muffin. Pudding chocolate bar tootsie roll donut dessert. Cookie gummi bears gingerbread gingerbread cheesecake. Chupa chups tart soufflé lemon drops powder toffee gummies muffin. Danish gummi bears pudding. Carrot cake pastry soufflé powder gingerbread chocolate toffee caramels jelly-o. Tiramisu chupa chups cookie. Gingerbread gingerbread ice cream soufflé wafer.

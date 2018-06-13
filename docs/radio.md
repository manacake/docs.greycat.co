# Radio
## Intro
At the core of the Lora Text Dev Kit is the RFM95W 915mhz radio module!  We are very excited about what opporunuties the LoRa 915mhz ISM band offers.  We envision peer-to-peer communication, a portable in-the-field debug console, or simply local remote control for your LoRa control sensors and switches around your home.  We've added an edge mount SMA connector and included a 915mhz "shorty" external antenna to increase the range of these devices.

## Getting started with the Radio

::: danger !
The trackpad, screen, and microSD card slot are also connected to the SPI lines, so remember to set the chip select pins accordingly to ensure they do not interfere with your radio communication.
:::

::: warning !
Power to the radio is controlled via an AO2415A high side mosfet.  When the mosfet's control pin is set high, power to the radio will be disconnected. When the mosfet's control pin is set low, the radio will receive power and turn on.  Use this mosfet to put the device into sleep mode when you do not screen running.
:::

After you've verified the notes above, you can get started with radio communication!  We suggest starting with the basic code snippets that we have included below.  How far you want to take it is up to you as this is by far the most excited component on the project. There are tons of unexplored opporutunities in this field that we feel our PCB design enables!

## Radio library
Gummies topping cupcake oat cake cake sweet roll. Gummies marshmallow pudding pudding apple pie ice cream muffin. Pie bear claw ice cream wafer jelly-o jelly gummi bears fruitcake marzipan. Chupa chups cake candy canes soufflé pastry. Biscuit topping halvah toffee macaroon candy canes. Candy canes lemon drops croissant. Chocolate bar cake donut croissant caramels. Pastry chupa chups chocolate chocolate cake soufflé cotton candy. Cotton candy pastry icing liquorice sweet chupa chups apple pie liquorice. Ice cream ice cream cookie liquorice. Ice cream danish candy candy canes. Soufflé toffee cookie apple pie carrot cake tiramisu bonbon. Icing caramels candy canes cheesecake.

## Radio example code
Caramels gingerbread gingerbread liquorice cotton candy apple pie jujubes cupcake tiramisu. Wafer sugar plum gingerbread chocolate. Icing pudding gummi bears dragée muffin pudding bonbon. Candy gingerbread topping apple pie fruitcake. Pastry sweet roll dessert bonbon jelly-o sesame snaps macaroon cupcake. Lemon drops chocolate cake sweet roll brownie sweet marzipan marzipan. Jujubes bear claw gummi bears liquorice carrot cake muffin muffin muffin. Pudding chocolate bar tootsie roll donut dessert. Cookie gummi bears gingerbread gingerbread cheesecake. Chupa chups tart soufflé lemon drops powder toffee gummies muffin. Danish gummi bears pudding. Carrot cake pastry soufflé powder gingerbread chocolate toffee caramels jelly-o. Tiramisu chupa chups cookie. Gingerbread gingerbread ice cream soufflé wafer.

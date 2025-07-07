# Smart Coffee Scale

A dual Loadcell Bluetooth low energy enabled smart coffee scale, relies on [decent scale api](https://decentespresso.com/decentscale_api), inspired by [almost-decent-scale](https://github.com/tadelv/almost-decent-scale), works with [Beanconqueror](https://beanconqueror.com/) app.

## Bill of Materials:
- ESP32-C3-SUPERMINI or any ESP32 Supermini board that supports BLE.
- USB-C breakoutboard.
- 2 x HX711 Modules.
- 2 x Load cell, one them is a 1KG loadcell (see images in ), the other is a smaller more precise 300g loadcell.
- 0.91 in OLED display module.
- VERO Prototype Perf Board 2x8cm.
- 3.3V linear voltage regulator.
- Two 6x6 magnets and two 5x5 magnets (optional, helps with making sure top plates stay in position).
- 4 x push buttons (long).
- Scews:
    - Six M3*6
    - Four M3*10
    - Seven M3*5
    - Four M2*6
    - Two M4*15
    - Three M4*23
    - Two M5*20

## Features
- 0.91 In Oled display.
- 4 buttons: 
    - power button
    - Tare
    - Switch between loadcells
    - ~~Send value to app~~ Start Timer.
- Sending weight over BLE.
- Calibration over BLE.

## Design 
STP file of the full project available for download [here](https://www.printables.com/model/1348363-smare-coffee-scale)

## Calibration over Bluetooth
To calibrate the scale over Bluetooth:
- Install LightBlue app.
- Connect to the scale.
- Find the "36F5" charicteristic.
- Begin the calibration process:
    - Using the bottons on the scale, select which loadcell you want to calibrate.
    - Remove all weights
    - Send '0x030C' to begin calibration.
    - Place a known Wight on the scale.
    - Then send '0x03CFXXXXXXXX' where the XXXXXXXX is the hex reprisentation of the known weight MULTIPLIED BY 1000, for example a weight of 38 grams becomes '00009470', and subsiquently the command becomes '0x03CF00009470'.
    - Wait for the scale to calculate and save new calibration values, this will take a while and the scale will seem unresponsive, afterwards the calibration should be finished.


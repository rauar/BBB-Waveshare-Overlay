# BBB-Waveshare-Overlay

## Overview

Device tree overlay for a Waveshare 3.2" TFT display on the Beaglebone Black (Touch events not working yet). *Use at your own risk* (especially w.r.t to wiring).

The necessary pins for operating the display have been determined based on the Raspberry Pi pin layout (the display is actually sold as a display for the Raspberry Pi). Those pins then need to be connected to the Beaglebone Black. I used the P9 header exclusively (SPI0 and 3 GPIO pins).



1. git clone https://github.com/beagleboard/bb.org-overlays
2. git clone https://github.com/rauar/BBB-Waveshare-Overlay.git
3. cp BBB-Waveshare-Overlay/BB-Waveshare32-00A0.dts ./bb.org-overlays/src/arm/
4. cd ./bb.org-overlays
5. ./install.sh

## Wiring:

Tested with:

* BBB SPI0 pins (SPI0_CS0, SPI0_SCLK, SPI0_D0, SPI0_D1)
* BBB GPIO pins (GPIO_49, GPIO_115, GPIO_117)

* (BBB Pin) -> (TFT Pin)
* SYS_V5    -> Pin 2
* GND       -> Pin 9
* SPI0_CS0  -> Pin 
* SPI0_SCLK
* SPI0_D0
* SPI0_D1
* GPIO_49
* GPIO_115
* GPIO_117

![alt text](https://az835927.vo.msecnd.net/sites/iot/Resources/images/PinMappings/RP2_Pinout.png "TFT pin mapping based on Raspberry Pi")

![alt text](http://rabbit-note.com/wp-content/uploads/2014/08/cape-headers.png "Beaglebone Black pin mapping")



# BBB-Waveshare-Overlay

## Overview

Device tree overlay for a Waveshare 3.2" TFT display on the Beaglebone Black (Touch events not working yet). *Use at your own risk* (especially w.r.t to wiring).

The necessary pins for operating the display have been determined based on the Raspberry Pi pin layout (the display is actually sold as a display for the Raspberry Pi). Those pins then need to be connected to the Beaglebone Black. I used the P9 header exclusively (SPI0 and 3 GPIO pins).

The display does not run on 3.3V only. I used 5V from the BBB - only then the backlight is turning on. 3.3V is currently not connected.



1. git clone https://github.com/beagleboard/bb.org-overlays
2. git clone https://github.com/rauar/BBB-Waveshare-Overlay.git
3. cp BBB-Waveshare-Overlay/BB-Waveshare32-00A0.dts ./bb.org-overlays/src/arm/
4. cd ./bb.org-overlays
5. ./install.sh

## Wiring:

Tested with:

* BBB SPI0 pins (SPI0_CS0, SPI0_SCLK, SPI0_D0, SPI0_D1)
* BBB GPIO pins (GPIO_49, GPIO_115, GPIO_117)

The TFT pins correspond to the Raspberry pin layout (e.g. pin 1 is 3.3V).

* Function: BBB Pin -> Pin on display board
* SYS_V5:   P9.5  -> P2
* GND:      P9.1  -> P9
* SPI0_CS0: P9.17 -> P24
* SPI0_SCLK:P9.22 -> P23
* SPI0_D0:  P9.21 -> P21
* SPI0_D1:  P9.18 -> P19
* GPIO_49:  P9.23 -> P15
* GPIO_117: P9.25 -> P13
* GPIO_115: P9.27 -> P11

# References

## Raspberry pin layout
The out-of-the-gox device tree overlay on Raspbian uses the SPI0 pins and GPIO 17, 22, 27.
![alt text](https://az835927.vo.msecnd.net/sites/iot/Resources/images/PinMappings/RP2_Pinout.png "TFT pin mapping based on Raspberry Pi")

## Beaglebone Black pin layout
![alt text](http://rabbit-note.com/wp-content/uploads/2014/08/cape-headers.png "Beaglebone Black pin mapping")



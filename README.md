# BBB-Waveshare-Overlay

## Overview

Device tree overlay for a Waveshare 3.2" TFT display and touch control connected to a Beaglebone Black. _Use at your own risk_ (especially w.r.t to wiring).

The necessary pins on the display's header have been determined based on the Raspberry Pi pin layout (the display is actually sold as a display for the Raspberry Pi). Not all pins on the header have to be connected.

On the BeagleBone Black I used the P9 header exclusively (SPI1 and 3 GPIO pins). _Do not use SPI0_ for driving the display on the BBB if you want to have touch support as well. The SPI0 CS1 pin of the CPU is not available on the pin header and therefore the BBB can only select one single slave on SPI0.  The display however has two SPI slaves (display controller and touch controller). Therefore SPI1 is required for display and touch support.

The display does not run on 3.3V only. I used 5V from the BBB - only then the backlight is turning on. 3.3V is not required.



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
* SPI1_CS0: P9.28 -> P24
* SPI1_CS1: P9.42 -> P26
* SPI1_SCLK:P9.31 -> P23
* SPI1_D0:  P9.29 -> P21
* SPI1_D1:  P9.30 -> P19
* DC-GPIO:  P9.23 -> P15
* Reset:    P9.25 -> P13
* Pen Down: P9.27 -> P11

# References

## Raspberry pin layout
The out-of-the-gox device tree overlay on Raspbian uses the SPI0 pins and GPIO 17, 22, 27.
![alt text](https://az835927.vo.msecnd.net/sites/iot/Resources/images/PinMappings/RP2_Pinout.png "TFT pin mapping based on Raspberry Pi")

## Beaglebone Black pin layout
![alt text](http://rabbit-note.com/wp-content/uploads/2014/08/cape-headers.png "Beaglebone Black pin mapping")

## Wiring photos
![alt text](https://github.com/rauar/BBB-Waveshare-Overlay/blob/master/IMG_2635.JPG)


# BeagleboneBlack Waveshare Overlays for 3.2" and 3.5"

## Overview

Device tree overlays for Waveshare 3.2" and 3.5" TFT displays including touch control. For use with BeagleBoneBlack's.

_Use at your own risk_ (especially w.r.t to wiring).

The necessary pins on the display's headers have been determined based on the Raspberry Pi pin layout (the display is actually sold as a display for the Raspberry Pi). Not all pins on the header have to be connected.

On the BeagleBone Black I used the P9 header exclusively (SPI1 and 3 GPIO pins). _Do not use SPI0_ for driving the display on the BBB if you want to have touch support as well. The SPI0 CS1 pin of the CPU is not available on the pin header and therefore the BBB can only select one single slave on SPI0.  The display however has two SPI slaves (display controller and touch controller). Therefore SPI1 is required for display and touch support.

The display does not run on 3.3V only. I used 5V from the BBB - only then the backlight is turning on. 3.3V is not required.

1. git clone https://github.com/beagleboard/bb.org-overlays
2. git clone https://github.com/rauar/BBB-Waveshare-Overlay.git
3. copy device tree overlay for the display into bb.org-overlays:
 1. for the 3.2" display:cp BBB-Waveshare-Overlay/BB-Waveshare32b-00A0.dts ./bb.org-overlays/src/arm/
 2. for the 3.5" display:cp BBB-Waveshare-Overlay/BB-Waveshare35-00A0.dts ./bb.org-overlays/src/arm/
4. cd ./bb.org-overlays
5. ./install.sh

## Wiring:

SPI0 does not support the display controller and the touch controller at the same time.

Tested with:

* BBB SPI1 pins (SPI1_CS0, SPI1_CS1, SPI1_SCLK, SPI1_D0, SPI1_D1)
* BBB GPIO pins (GPIO_49, GPIO_115, GPIO_117)

The TFT pins for the displays need to be connected to the BBB as follows (e.g. pin 1 on the raspberry is the 3.3V pin).

### Waveshare 3.2" connections
* Function: BBB Pin -> 3.2" display pin on display board
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

### Waveshare 3.5" connections
* Function: BBB Pin -> 3.5" display pin on display board
* SYS_V5:   P9.5  -> P2
* GND:      P9.1  -> P9
* SPI1_CS0: P9.28 -> P24
* SPI1_CS1: P9.42 -> P26
* SPI1_SCLK:P9.31 -> P23
* SPI1_D0:  P9.29 -> P21
* SPI1_D1:  P9.30 -> P19
* DC-GPIO:  P9.23 -> P18
* Reset:    P9.25 -> P22
* Pen Down: P9.27 -> P11

# References

## Raspberry pin layout
The out-of-the-gox device tree overlay on Raspbian uses the SPI0 pins and GPIO 17, 22, 27.
![alt text](https://az835927.vo.msecnd.net/sites/iot/Resources/images/PinMappings/RP2_Pinout.png "TFT pin mapping based on Raspberry Pi")

## Beaglebone Black pin layout
![alt text](http://rabbit-note.com/wp-content/uploads/2014/08/cape-headers.png "Beaglebone Black pin mapping")

## Wiring photo 3.2" display
![alt text](https://github.com/rauar/BBB-Waveshare-Overlay/blob/master/IMG_2635.JPG)


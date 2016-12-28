# BBB-Waveshare-Overlay

## Overview

Device tree overlay for Waveshare 3.2" TFT display (Touch events not working yet). *Use at your own risk* (especially w.r.t to wiring).

1. git clone https://github.com/beagleboard/bb.org-overlays
2. cp BB-Waveshare32-00A0.dts ./bb.org-overlays/src/arm/
3. cd ./bb.org-overlays
4. ./install.sh

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

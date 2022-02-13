# PROBE STYLE I2C TEMPERATURE SENSOR PCB

Small circuit board, designed to be installed inside a metal tube or thermowell.

Read this in other languages: [Español](/assets/markdown/README.es.md)

Imagine this scenario: you have a bunch of I2C sensors tied to a bus (i.e. Humidity, pressure, light) and a waterproof temperature sensor is needed, the fastest option is to acquire one of the very popular OneWire type. This brings two big disadvantages:

* An additional GPIO pin (and wire!) is required, because I2C signals are incompatible with OneWire
* Additional libraries will be needed, protocols are very dissimilar in software too

There are very few waterproof temperature sensors in the market with a real I2C interface, but are not easy to obtain and are expensive. This document gives you some ideas on how to build your own waterproof I2C temperature sensor in an affordable way.

## Main features
* Open source
* Designed in KiCad PCB
* All source files available
* Gerber files available : single piece or 100x100mm panel
* Assorted flavors

## Printed circuit board

The PCB was designed to be as small as possible, but using SMD components that can be hand soldered. All pull-up resistors can be populated on the board. There are also onboard solder jumper pads for I2C address setup.

![MODULE](/assets/img/pcb.jpg)

## Wiring

Multi conductor cable with 5 stranded wires used for VCC,GND,SDA,SCL and ALARM signals

![MODULE](/assets/img/wired.jpg)

## Waterprofing

The board could be fitted inside a stainless steel tube or thermowell. Some thermal silicone grease must be applied in the sensor zone, and epoxy glue near the cable input for sealing 

![MODULE](/assets/img/waterproofing.jpg)


## Versions

There are several board versions, each one with different sensor and PCB sizes


| SENSOR  | SIZE        | LINK                                   |
|---------|-------------|----------------------------------------|
| LM75A   |  5.5x35mm   | [LM75A_PROBE_PCB](/LM75A_PROBE_PCB)    |
| PCT2075 |  4.0x35mm   | [PCT2075_PROBE_PCB](/PCT2075_PROBE_PCB)|

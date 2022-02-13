# PROBE STYLE I2C TEMPERATURE SENSOR PCB

Small circuit board, designed to be installed inside a metal tube or thermowell.

Read this in other languages: [Español](/assets/markdown/README.es.md)

This document shows the equivalence between labels written in the module [schematic](/assets/pdf/CJMCU-25504-SCHEMATIC.pdf) and in the IC [datasheet](/assets/pdf/bq25504.pdf).

## The module in question

The only visible marking on the PCB is CJMCU-25504, there are no references to the manufacturer. Silkscreens are unreadable.

![MODULE](/assets/img/CJMCU-25504-MODULE.png)

## Resistor map

The following image presents visually each resistor with both labels: IC manufacturer and module manufacturer.

![MODULE](/assets/img/CJMCU-25504-RESISTORS.svg)

## Pinout

The following image presents visually each header pin with a label exactly written as in the IC manufacturer datasheet.

![MODULE](/assets/img/CJMCU-25504-PINOUT.svg)

In this module the voltage divider made of ROC1 and ROC2 is not connected to VOC_SAMP pin. Instead the middle point of the divider and VOC_SAMP signals are routed to header pins. MPPT could be enabled or disabled externally.

## Module resistor values

The following tables show the values of the resistors that came soldered into the PCB. Those values are exactly the same found in the IC sample design pdf.

### MPPT

| TI ID | PCB ID | MARK | VALUE  |
|-------|--------|------|--------|
| ROC2  |  R2    | 63E  | 4.42 M |
| ROC1  |  R10   | 565  | 5.60 M |
| ROC1a |  R1    | 106  | 10.0 M |

### OVERVOLTAGE

| TI ID | PCB ID | MARK | VALUE  |
|-------|--------|------|--------|
| ROV2  |  R4    | 59E  | 4.02 M |
| ROV1  |  R3    | 75E  | 5.90 M |
| ROV1a |  R14   | 0    |    0 M |

### UNDERVOLTAGE

| TI ID | PCB ID | MARK | VALUE  |
|-------|--------|------|--------|
| RUV2  |  R6    | 61E  | 4.22 M |
| RUV1  |  R5    | 565  | 5.60 M |
| RUV1a |  R15   | 0    |    0 M |

### VOLTAGE OK

| TI ID | PCB ID | MARK | VALUE  |
|-------|--------|------|--------|
| ROK3  |  R7    | 16E  | 1.43 M |
| ROK2  |  R9    | 61E  | 4.22 M |
| ROK1  |  R8    | 63E  | 4.42 M |
| ROK1a |  R16   | 0    |    0 M |

### OVERTEMPERATURE

| TI ID       | PCB ID | MARK | VALUE |
|-------------|--------|------|-------|
| OT_PROG 60  |  R12   | 0    |   0 M |
| OT_PROG 120 |  R11   | N/A  |   N/A |


Here are the configuration parameters obtained with the aforementioned resistor values:


| PARAMETER      | VALUE |
|----------------|-------|
| VBAT_OV        | 3.15 V|
| VBAT_UV        | 2.20 V|
| VBAT_OK        | 2.44 V|
| VBAT_OK_HYST   | 2.80 V|
| MPP            | 78 %  |
| OVERTEMP       | 60 C  |

This configuration uses a solar cell as input and 2x 1.25V NiMH rechargeable batteries in series as a storage device


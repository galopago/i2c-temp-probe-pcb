# PCB PARA SENSOR DE TEMPERATURA I2C TIPO SONDA

El modulo CJMCU-25504 basado en el circuito integrado para cosecha de energia BQ25504, tiene incorporados todos los componentes externos necesarios para usarlo. La configuracion de los diferentes parametros de este integrado se realiza mediante resistores, sin embargo, la serigrafia no es clara, lo que hace dificil identificar los componentes. Adicional a esto, el fabricante del modulo emplea unas etiquetas diferentes a las que usa el fabricante del integrado lo cual aumenta mas la confusion.

Lea esto en otros idiomas: [English](../../README.md)

Este documento pretende presentar las equivalencias entre las etiquetas utilizadas por el fabricante del modulo en el [esquematico](/assets/pdf/CJMCU-25504-SCHEMATIC.pdf) y circuito impreso, con las expuestas por el fabricante del integrado en su [hoja de datos](/assets/pdf/bq25504.pdf). De esta forma sera mucho mas facil realizar cambios a los componentes para ajustarlo a nuestras propias necesidades

## El modulo en cuestion

La unica marca visible en el circuito impreso es CJMCU-25504, no hay referencias visibles al fabricante. La serigrafia de los componentes es dificil de leer.

![MODULE](/assets/img/CJMCU-25504-MODULE.png)

## Mapa de resistores

El siguiente grafico muestra visualmente cada uno de los resistores, con el nombre de la etiqueta como la usa el fabricante, y con el nombre de la etiqueta que empleo el fabricante del modulo.

![MODULE](/assets/img/CJMCU-25504-RESISTORS.svg)

## Mapa de conectores
El siguiente grafico muestra visualmente cada uno de los conectores con el nombre de la etiqueta que empleo el fabricante del integrado. 

![MODULE](/assets/img/CJMCU-25504-PINOUT.svg)

Algo curioso en este modulo, es que el fabricante decidio no conectar directamente el divisor de voltaje formado por ROC1 y ROC2 al pin VOC_SAMP, sino que enruto el punto medio del divisor y el pin VOC_SAMP hacia el conector header, de forma tal que se puede optar por configurar el MPPT o deshabilitarlo mediante conexiones externas.

## Valores de los resistores del modulo
En las siguientes tablas se expone los valores que trae el modulo de fabrica. Estos valores coinciden exactamente con los del ejemplo presentado en la hoja de datos del componente. 

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



Con los anteriores valores de resistores se obtiene la siguiente configuracion:

| PARAMETER      | VALUE |
|----------------|-------|
| VBAT_OV        | 3.15 V|
| VBAT_UV        | 2.20 V|
| VBAT_OK        | 2.44 V|
| VBAT_OK_HYST   | 2.80 V|
| MPP            | 78 %  |
| OVERTEMP       | 60 C  |


Esta configuracion usa como entrada una celda solar y como elemento de almacenamiento 2 baterias recargables tipo NiMH de 1.25V  en serie.

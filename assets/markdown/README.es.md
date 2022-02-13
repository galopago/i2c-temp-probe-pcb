# PCB PARA SENSOR DE TEMPERATURA I2C TIPO SONDA

Circuito impreso de pequeñas dimensiones, pensado para ser usado como sonda dentro de un tubo de acero inoxidable o termopozo. 

Lea esto en otros idiomas: [English](../../README.md)

Cuando se tiene un conjunto de sensores en un bus I2C, por ejemplo Humedad, iluminacion, presion, etc. y se requiere agregar un sensor de temperatura a prueba de agua para fluidos, la opcion mas rapida es emplear un dispositivo del tipo OneWire bastante populares en el mercado. Esto tiene 2 inconvenientes:

* Se requiere un pin GPIO adicional para el sensor OneWire, pues estos son incompatibles con las señales I2C
* Se requieren librerias adicionales, pues en la capa de software los protocolos son muy diferentes

Existen algunos sensores de temperatura a prueba de agua con interfaz I2C real, sinembargo no son tan faciles de conseguit, ni tan economicos como los OneWire. Este documento pretende dar algunas ideas de como construir tu propio sensos de temperatura I2C a prueba de agua a un precio razonable.

## Generalidades

* Codigo abierto
* Diseñado en KiCad PCB
* Disponibilidad de archivos fuente
* Archivos gerber listos para enviar a fabricar: una unidad o panelizados en area de 100x100mm
* Sabores surtidos

## El circuito impreso

La tarjeta se diseño del menor tamaño posible, pero usando componentes de montaje superficial que puedan ser soldados a mano. En la tarjeta pueden ser montado los resistores de pull-up y ademas hay un jumper de configuracion mediante puente de soldadura para cambiar la direccion I2C del sensor.

![MODULE](/assets/img/pcb.jpg)

## Cableado

Se uso un cable recubierto multihilos de 5 vias: VCC,GND,SDA,SCL y ALARMA

![MODULE](/assets/img/wired.jpg)

## Impermeabilizacion

La tarjeta puede instalarse dentro de un tubo metalico de acero inoxidable o dentro de un termopozo. Se requerira un poco de silicona conductora de calor en el area del sensor y pegamento epoxico para sellar y fijar el cable en la boca del tubo

![MODULE](/assets/img/waterproofing.jpg)

Algo curioso en este modulo, es que el fabricante decidio no conectar directamente el divisor de voltaje formado por ROC1 y ROC2 al pin VOC_SAMP, sino que enruto el punto medio del divisor y el pin VOC_SAMP hacia el conector header, de forma tal que se puede optar por configurar el MPPT o deshabilitarlo mediante conexiones externas.

## Versiones

Existen varias versiones de tarjetas, cada una con un sensor de temperatura y dimensiones diferentes:


| SENSOR  | DIMENSIONES | ENLACE                    |
|---------|-------------|---------------------------|
| LM75A   |  R2         | [MODULE](/LM75A_PROBE_PCB)|
| PCT2075 |  R10        | 565                       |



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

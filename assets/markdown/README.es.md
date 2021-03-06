# PCB PARA SENSOR DE TEMPERATURA I2C TIPO SONDA

Circuito impreso de pequeñas dimensiones, pensado para ser usado como sonda dentro de un tubo de acero inoxidable o termopozo. 

Lea esto en otros idiomas: [English](../../README.md)

Cuando se tiene un conjunto de sensores en un bus I2C, por ejemplo: Humedad, iluminacion, presion, etc. y se requiere agregar un sensor de temperatura a prueba de agua para fluidos, la opcion mas rapida es emplear dispositivos del tipo OneWire, bastante populares en el mercado. Esto tiene 2 inconvenientes:

* Se requiere un pin GPIO adicional para el sensor OneWire, pues estos son incompatibles con las señales I2C
* Se requieren librerias adicionales, pues en la capa de software los protocolos son muy diferentes

Existen algunos sensores de temperatura a prueba de agua con interfaz I2C real, sin embargo, no son tan faciles de conseguir, ni tan economicos como los OneWire. Este documento pretende dar algunas ideas de como construir tu propio sensor de temperatura I2C a prueba de agua a un precio razonable.

## Generalidades

* Codigo abierto
* Diseñado en KiCad PCB
* Disponibilidad de todos los archivos fuentes
* Archivos gerber listos para enviar a fabricar: una unidad o panelizados en area de 100x100mm
* Sabores surtidos

## El circuito impreso

La tarjeta se diseño para que tenga menor tamaño posible, pero usando componentes de montaje superficial que puedan ser soldados a mano. En la tarjeta pueden ser montados los resistores de pull-up y ademas hay un jumpers de configuracion mediante puente de soldadura para cambiar la direccion I2C del sensor.

![MODULE](/assets/img/pcb.jpg)

## Cableado

Se uso un cable recubierto multihilos de 5 conductores: VCC,GND,SDA,SCL y ALARMA.

![MODULE](/assets/img/wired.jpg)

## Impermeabilizacion

La tarjeta puede instalarse dentro de un tubo metalico de acero inoxidable o dentro de un termopozo. Se requerira un poco de silicona conductora de calor en el area del sensor y pegamento epoxico para sellar y fijar el cable en la boca del tubo

![TUBOACERO](/assets/img/waterproofing.jpg)

![THERMOPOZO](/assets/img/thermowell.jpg)

## Versiones

Existen varias versiones de tarjetas, cada una con un sensor de temperatura y dimensiones diferentes:

| SENSOR  | DIMENSIONES | ENLACE                                 |
|---------|-------------|----------------------------------------|
| LM75A   |  5.5x35mm   | [lm75A-probe-pcb](/lm75A-probe-pcb)    |
| PCT2075 |  4.0x35mm   | [pct2075-probe-pcb](/pct2075-probe-pcb)|


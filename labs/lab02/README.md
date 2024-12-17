# Laboratorio 2: Medidor de carga.

Índice:

1. [Objetivos de aprendizaje](#objetivos-de-aprendizaje)

2. [Planteamiento del problema](#planteamiento-del-problema)

3. [Requisitos funcionales](#requisitos-funcionales)

4. [Entregables](#entregables)

5. [Documentación de apoyo](#documentación-de-apoyo-necesaria)

*******


## Objetivos de aprendizaje

- Diseñar y construir sistemas digitales basados en lógica combinacional, enfocándose en la implementación de sumadores y otros bloques lógicos que operan en función de las entradas actuales, sin depender de estados previos.
- Comprender los principios fundamentales de la lógica digital, como puertas lógicas y sumadores, y cómo estos se implementan en *hardware*. 
- Diseñar, construir e instanciar módulos utilizando lenguajes de descripción de *hardware* (HDL)
- Familiarizarse con el flujo completo de diseño e implementación en *hardware*, desde la especificación inicial hasta la síntesis e implementación en FPGA.
- Aprender a verificar y validar el funcionamiento del diseño en un entorno de simulación, identificando y corrigiendo errores antes de la implementación física en *hardware*.
- Explorar la implementación de diseños digitales en FPGAs.

## Introducción

El objetivo de este laboratorio es diseñar e implementar un sistema de monitoreo de carga de un banco de baterías, utilizando lógica combinacional para procesar los niveles de carga de cada batería y generar señales de advertencia según criterios específicos. A lo largo de este proceso, se utilizarán lenguajes de descripción de hardware (HDL) para modelar el comportamiento del sistema y se implementarán diferentes niveles de abstracción (estructural y comportamental) en el diseño de los circuitos lógicos.

El sistema debe ser capaz de detectar el estado de carga de cada batería y generar señales de advertencia en función de los niveles de carga específicos. Para ello, se diseñarán sumadores y otros componentes lógicos que sumen los niveles de carga de las baterías y evalúen los criterios de advertencia establecidos.

## Planteamiento del problema

### Monitoreo del estado de carga de una batería.

Se requiere diseñar e implementar un sistema  de monitoreo que supervise el nivel de carga de un banco de baterías compuesto por dos baterías. El nivel de carga total del banco está dado por la suma del nivel de carga de cada batería.

Estas baterías cuentan cada una con un sensor de tensión que entrega valores decimales entre 0 y 15 en sistema binario, dependiendo del nivel de carga de cada una, donde: 

0 (```4'b0000```)  ---> Batería completamente descargada.

15 (```4'b1111```) ---> Batería completamente cargada.

## Requisitos funcionales

**1. Detección de baterías descargadas:** Si una de las baterías tiene una carga de 0 (```4'b0000```), debe generarse una señal de advertencia para así poderla atender.

**2. Aviso de carga crítica:** Si la carga total del banco de baterías es igual o menor que el 10% de la carga máxima, se debe activar una señal de advertencia, ya sea visual, auditiva o ambas. Para cumplir este requisito es necesario revisar la siguiente [documentación](/labs/lab02/sumador.md).

**3. Otros niveles de carga:** Se debe agregar al sistema otros indicadores para informar niveles de carga de interés, por ejemplo, nivel aceptable, regular y crítico.

**4. Implementación modular escalable:** El diseño completo debe constar de varios módulos para hacer el sistema escalable y claro, lo que facilitará también su validación y verificación. Cada grupo tendrá la libertad de decidir cómo organizar y conectar los módulos.


**Se recomienda consultar la documentación de apoyo**.

*****

## Entregables

1. Realice la descripción de la solución a la problemática planteada de acuerdo a las indicaciones que se darán en la clase de laboratorio.

2. Explique el item anterior en su respectivo archivo ```README.md```.

3. Realice la respectiva simulación a la solución planteada y muestre evidencias en su archivo ```README.md```.

4. Implemente la descripción HDL en la tarjeta de desarrollo, empleando la ```IDE Quartus``` y muestre en el laboratorio el funcionamiento, empleando los periféricos que requiera. Para lograr este entregable es necesario revisar la siguiente [documentación](/labs/lab00/proyectoQuartus.md).

## Documentación de apoyo necesaria 

1. [Tutorial de implementación en la FPGA Cyclone IV](/labs/lab00/proyectoQuartus.md)

2. [Sumador de 1 bit y sumador de 4 bits](/labs/lab02/sumador.md)


# Laboratorio 2: Introducción al diseño digital.


### Objetivos de aprendizaje

- Comprender los principios básicos de la lógica digital, como puertas lógicas, decodificadores y sumadores, y cómo estos se implementan en una FPGA. 
- Construir e instanciar módulos en Verilog para implementar un sistema completo en FPGA.
- Aprender a verificar el funcionamiento del diseño en un entorno de simulación antes de implementar en hardware.


### Monitoreo del estado de carga de una batería.

### Planteamiento del problema.

Se requiere implementar un sistema que de aviso del nivel de carga de un banco de baterías que cuenta con dos baterías. El nivel de carga total del banco esta dado por la suma del nivel de carga de cada batería, para ello se debe consultar esta [documentación](/labs/lab02/Sumador.md). 

Estas baterías cuentan cada una con un sensor de tensión que entrega valores entre 0 y 15 en sistema binario, dependiendo del nivel de carga de cada una, donde: 

0000 (0)  ---> Batería completamente descargada.
1111 (15) ---> Batería Completamente cargada.

### Requisitos funcionales.


**1. Aviso de carga crítica:** Si la carga total del banco de baterías es igual o menor que el 10% de la carga máxima, se debe activar una señal de advertencia, ya sea visual, auditiva o ambas.

**2. Detección de baterías descargadas:** Si una de las baterías tiene una carga de 0 (0000), debe generarse una señal de advertencia para así poderla atender.

**3. Otros niveles de carga:** Queda a consideración de cada grupo proponer cuando el nivel de carga del banco esta en un nivel moderado y suficiente y asi mismo generar una alerta visual diferente para cada uno. 

**4. Implementación modular:** El diseño se debe dividir en varios módulos para organizar el código y hacer el sistema escalable y claro. Queda a consideración de cada grupo cómo dividir las funcionalidades del diseño.

*****

### Entregables

1. Realice la descripción de la solución a la problemática planteada de acuerdo a las indicaciones que se darán en la clase de laboratorio.

2. Explique el item anterior en su respectivo archivo ```README.md```.

3. Realice la respectiva simulación a la solución planteada y muestre evidencias en su archivo ```README.md```.

4. Implemente la descripción HDL en la tarjeta de desarrollo, empleando la ```IDE Quartus``` y muestre en el laboratorio el funcionamiento, empleando los periféricos que requiera. 

***
# Documentación adicional 

1. [Tutorial de Implementación en la FPGA Cyclone IV](/labs/lab02/proyectoQuartus.md)


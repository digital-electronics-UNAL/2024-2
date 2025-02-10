# Laboratorio 04: Visualización usando pantalla LCD 16 x 2

Índice:

1. [Objetivos de aprendizaje](#objetivos-de-aprendizaje)

2. [Introducción](#introducción)

3. [Requisitos funcionales](#requisitos-funcionales)

4. [Entregables](#entregables)

5. [Documentación de apoyo](#documentación-de-apoyo-necesaria)

*******


# Objetivos de aprendizaje


# Introducción

En sistemas embebidos y arquitecturas digitales, la interacción con dispositivos de visualización es esencial para la presentación de información en tiempo real. Entre estos dispositivos, las pantallas LCD alfanuméricas de 16x2 son ampliamente utilizadas debido a su simplicidad y bajo consumo de recursos.

Sin embargo, el control de una LCD 16x2 implica una secuencia precisa de comandos que deben ejecutarse en el orden correcto para inicializar la pantalla, escribir caracteres y actualizar su contenido. En este contexto, el uso de una Máquina de Estados Finitos (FSM) en *hardware* permite gestionar de manera estructurada el flujo de datos y señales de control necesarias para escribir en la pantalla.

A conitnuación se presenta una introducción a las características básicas de la pantalla
LCD:

<p align="center">
 <img src="/pics/lab04/LCD16x2.png" alt="alt text" width=500 >
</p>
<p align="center">
 Figura 1
</p>


# Requisitos funcionales


## Entregables

1. Realice la descripción de la solución a la problemática planteada de acuerdo a las indicaciones que se darán en la clase de laboratorio.

2. Explique el item anterior en su respectivo archivo ```README.md```.

3. Realice la respectiva simulación a la solución planteada y muestre evidencias en su archivo ```README.md```.

4. Implemente la descripción HDL en la tarjeta de desarrollo, empleando la ```IDE Quartus``` y muestre en el laboratorio el funcionamiento, empleando los periféricos que requiera. Para lograr este entregable es necesario revisar la siguiente [documentación](/labs/lab00/proyectoQuartus.md).

## Documentación de apoyo necesaria 

1. [Tutorial de implementación en la FPGA Cyclone IV](/labs/lab00/proyectoQuartus.md)

2. [¿Cómo escribir máquinas de estado?]()

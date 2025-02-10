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


LCD significa "Pantalla de Cristal Líquido" (Liquid Crystal Display). El nombre LCD 16×2 se debe a que tiene 16 columnas y 2 filas. Existen varias configuraciones como 8×1, 8×2, 10×2, 16×1, entre otras, pero la más utilizada es la 16×2. Esto significa que puede mostrar 32 caracteres en total, donde cada carácter está compuesto por una matriz de 5×8 píxeles, como se muesta en la siguiente figura:

<p align="center">
 <img src="/pics/lab04/LCD16x2_diag.jpg" alt="alt text" width=500 >
</p>

**Características del Módulo LCD 16×2:**

* Voltaje de operación: 4.7V a 5.3V
* Consumo de corriente: 1mA sin retroiluminación
* Pantalla alfanumérica, permite mostrar letras y números
* Dos filas, cada una con capacidad para 16 caracteres
* Cada carácter se construye en una matriz de 5×8 píxeles
* Puede operar en modo de 8 bits o 4 bits (se usará en modo de 4 bits)
* Permite mostrar caracteres personalizados
* Disponible con retroiluminación en color verde o azul


La pantalla LCD 16x2 cuenta con múltiples pines para alimentación, control y transferencia de datos. La siguiente lista describe sus funciones principales:

<p align="center">
 <img src="/pics/lab04/LCD16x2.png" alt="alt text" width=500 >
</p>

* **VSS** = GND (Tierra)
* **VDD** = (+3.3V a +5V) – Alimentación de la pantalla
* **VO** = Ajuste de contraste 
* **RS** = Selección de tipo de registro – RS=0: Comando, RS=1: Dato
* **RW** = Lectura/Escritura (R/W) – R/W=0: Escritura, R/W=1: Lectura
* **E** = Clock (Enable) – Activado en el flanco de bajada
* **D0** = Bit 0 – Línea de datos
* **D1** = Bit 1 – Línea de datos
* **D2** = Bit 2 – Línea de datos
* **D3** = Bit 3 – Línea de datos
* **D4** = Bit 4 – Línea de datos
* **D5** = Bit 5 – Línea de datos
* **D6** = Bit 6 – Línea de datos
* **D7** = Bit 7 – Línea de datos
* **A** = Ánodo de retroiluminación (+)
* **K** = Cátodo de retroiluminación (-)

# Procedimiento

## Parte 1

Al aceptar el **assignment** del [Lab04](), clonarán el repositorio correspondiente para la entrega y encontrarán en la carpeta src archivos fuente que contienen la descripción de hardware necesaria para controlar la pantalla LCD 16x2, permitiendo visualizar texto estático en sus dos filas. 

Con este material deben hacer lo siguiente:

1. Analizar la descripción de hardware y diagramar tanto la unidad de control, compuesta por la FSM, como la arquitectura completa.

2. Implementar el diseño en la tarjeta de desarrollo **Altera Cyclone IV** utilizando los archivos proporcionados, siguiendo estas instrucciones:

    1. En la tarjeta de desarrollo existe un *header* para pantallas LCD 16x2 o 128x64, allí deben conectar la pantalla asegurandose de que el pin 1 marcado en la PCB de la pantalla coincida con el pin 1 marcado en la PCB de la tarjeta, como se muestra en la siguiente figura:

    <p align="center">
    <img src="/pics/lab04/ALTERA_LCD.png" alt="alt text" width=500 >
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

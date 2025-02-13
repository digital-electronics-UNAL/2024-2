# Laboratorio 04: Visualización usando pantalla LCD 16x2

Índice:

- [Laboratorio 04: Visualización usando pantalla LCD 16x2](#laboratorio-04-visualización-usando-pantalla-lcd-16x2)
  - [Objetivos de aprendizaje](#objetivos-de-aprendizaje)
  - [Introducción](#introducción)
  - [Procedimiento](#procedimiento)
    - [Parte 1](#parte-1)
    - [Parte 2](#parte-2)
  - [Entregables](#entregables)
  - [Documentación de apoyo necesaria](#documentación-de-apoyo-necesaria)

*******


## Objetivos de aprendizaje

* Introducir el concepto de máquina de estado en el diseño de hardware utilizando Verilog, enfocado en el control y funcionamiento de una pantalla LCD.


## Introducción

En sistemas embebidos y arquitecturas digitales, la interacción con dispositivos de visualización es esencial para la presentación de información en tiempo real. Entre estos dispositivos, las pantallas LCD alfanuméricas de 16x2 son ampliamente utilizadas debido a su simplicidad y bajo consumo de recursos.

Sin embargo, el control de una LCD 16x2 implica una secuencia precisa de comandos que deben ejecutarse en el orden correcto para inicializar la pantalla, escribir caracteres y actualizar su contenido. En este contexto, el uso de una Máquina de Estados Finitos (FSM) en *hardware* permite gestionar de manera estructurada el flujo de datos y señales de control necesarias para escribir en la pantalla.

A conitnuación se presenta una introducción a las características básicas de la pantalla
LCD:


LCD significa "Pantalla de Cristal Líquido" (Liquid Crystal Display). El nombre LCD 16×2 se debe a que tiene 16 columnas y 2 filas. Existen varias configuraciones como 8×1, 8×2, 10×2, 16×1, entre otras, pero la más utilizada es la 16×2. Esto significa que puede mostrar 32 caracteres en total, donde cada carácter está compuesto por una matriz de 5×8 píxeles, como se muesta en la siguiente figura:

<p align="center">
 <img src="/pics/lab04/LCD16x2_diag.png" alt="alt text" width=500 >
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

* **Vss** = GND (Tierra)
* **Vdd** = (+3.3V a +5V) – Alimentación de la pantalla
* **Vo** = Ajuste de contraste 
* **RS** = Selección de tipo de registro – RS=0: Comando, RS=1: Dato
* **R/W** = Lectura/Escritura – R/W=0: Escritura, R/W=1: Lectura
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


**Se recomienda revisar en detalle el [*datasheet*](/labs/lab04/lcd016n002bcfhet.pdf) de la LCD 16x2**.

## Procedimiento

### Parte 1

Al aceptar el *assignment* del [Lab04](https://github.com/digital-electronics-UNAL/2024-2/tree/main?tab=readme-ov-file#cronograma), clonarán el repositorio correspondiente para la entrega y encontrarán en la carpeta ```src``` archivos fuente que contienen la descripción de hardware necesaria para controlar la pantalla LCD 16x2, permitiendo visualizar texto estático en sus dos filas. 

Con este material deben hacer lo siguiente:

1. Analizar la descripción de hardware y diagramar tanto la unidad de control, compuesta por la FSM, como la arquitectura completa, para lo cual contarán con una explicación proporcionada por el docente de laboratorio.

2. Realizar la respectiva simulación. El *testbench* lo encuentran en la carpeta ```test``` de su repositorio.

3. Implementar el diseño en la tarjeta de desarrollo **Altera Cyclone IV** utilizando los archivos proporcionados, para lo que deben seguir estas instrucciones:

    1. En la tarjeta de desarrollo existe un *header* para pantallas LCD 16x2 o 128x64, allí deben conectar la pantalla asegurandose de que el pin 1 marcado en la PCB de la pantalla coincida con el pin 1 marcado en la PCB de la tarjeta. En la siguiente figura se muestra la ubicación del *header* y otros elementos asociados a la configuración física de la pantalla LCD:

    <p align="center">
    <img src="/pics/lab04/ALTERA_LCD.png" alt="alt text" width=500 >
    </p>

    2. Después de configurar el **Pin Planer** en Quartus, de acuerdo a la tabla en la  PCB de la tarjeta de desarrollo que se muestra en la anterior figura, deben asegurarse de que el ```pin 101``` esté correctamente asignado como una E/S en lugar de su función predeterminada de programación de la siguiente forma:

        1. Ir al menú ```Assignments``` y seleccionar la opción ```Device```.

            <p align="center">
            <img src="/pics/lab04/101_1.png" alt="alt text" width=500 >
            </p>

        2. En la ventana ```Device``` dar click en el botón ```Device and Pin Options```.

            <p align="center">
            <img src="/pics/lab04/101_2.png" alt="alt text" width=500 >
            </p>

        3. En la ventana ```Device and Pin Options``` escoger, en la lista ```Category```, la opción ```Dual-Purpose Pins``` y en la lista de los pines de doble propósito, cambiar el valor del pin ```nCEO``` a ```Use as regular I/O```.

            <p align="center">
            <img src="/pics/lab04/101_3.png" alt="alt text" width=500 >
            </p>

### Parte 2

Una vez comprendida la descripción del *hardware* proporcionado y el funcionamiento de la pantalla LCD, deberán implementar la lógica necesaria para visualizar texto dinámico, es decir, información que cambia en función de dos entradas (inputs) al módulo de control de la pantalla.

Estas entradas serán valores numéricos de 8 bits y se mostrarán junto al texto estático previamente visualizado. Para ello, se recomienda:

1. Revisar detenidamente el [*datasheet*](/labs/lab04/lcd016n002bcfhet.pdf) de la pantalla LCD y determinar las intrucciones necesarias para posicionar el texto dinámico en un cursor posterior a las posiciones ocupadas por el texto estático.
2. Tener en cuenta que la pantalla recibe los caracteres en su representación hexadecimal del código ASCII.

Teniendo en cuenta estas modificaciones deben volver a realizar los ítems 1, 2 y 3 de la [Parte 1](#parte-1).

## Entregables

Realice las partes [1](#parte-1) y [2](#parte-2) mencionadas en el procedimiento y presente
en clase las implementaciones de cada una al docente de laboratorio.


## Documentación de apoyo necesaria 

1. [Tutorial de implementación en la FPGA Cyclone IV](/labs/lab00/proyectoQuartus.md)

2. [¿Cómo escribir máquinas de estado?](/labs/lab04/lcd016n002bcfhet.pdf)

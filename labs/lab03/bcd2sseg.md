# Decodificador BCD a 7 segmentos


El objetivo de este laboratorio es visualizar el resultado de un sumador en los display de 7 segmentos que vienen en la tarjeta de desarrollo.

### BCD (Binary Coded Decimal): 

BCD significa Décimal Codificado en Binario y representa el sistema de numeración digital en el que podemos representar cada número décimal utilizando 4 bits de números binarios.


Como sabemos hay 10 dígitos en el sistema décimal, para representarlos necesitamos 10 combinaciones de 4 bits binarios.

<p align="center">

|   Dígito  |   Bit $_3$  |  Bit $_2$ |   Bit $_1$  |   Bit $_0$  |
|-----------|-------------|-----------|-------------|-------------|
|     0     |      0      |     0     |      0      |      0      |
|     1     |      0      |     0     |      0      |      1      |
|     2     |      0      |     0     |      1      |      0      |
|     3     |      0      |     0     |      1      |      1      | 
|     4     |      0      |     1     |      0      |      0      |
|     5     |      0      |     1     |      0      |      1      |
|     6     |      0      |     1     |      1      |      0      |
|     7     |      0      |     1     |      1      |      1      | 
|     8     |      1      |     0     |      0      |      0      | 
|     9     |      1      |     0     |      0      |      1      | 
</p>

Ahora bien, también es posible representar de forma binaria los números décimales del 10 al 15 pero empleando su correspondiente representación en el sistema hexadécimal:

<p align="center">

|   Dígito  |   Bit $_3$  |  Bit $_2$ |   Bit $_1$  |   Bit $_0$  |
|-----------|-------------|-----------|-------------|-------------|
|     A     |      1      |     0     |      1      |      0      |
|     B     |      1      |     0     |      1      |      1      |
|     C     |      1      |     0     |      0      |      0      |
|     D     |      1      |     1     |      0      |      1      | 
|     E     |      1      |     1     |      1      |      0      |
|     F     |      1      |     1     |      1      |      1      |
</p>


### Display de 7 segmentos:

El $display$ de siete segmentos es un dispositivo electrónico que consta de siete diodos emisores de luz (LED) dispuestos en un patrón definido; encender una combinación particular de éstos permite representar un dígito décimal o hexadécimal Existen dos tipos de $display$ LED de siete segmentos:

* Tipo de cátodo común: en este tipo de $display$, todos los cátodos de los siete LEDs están conectados entre sí a tierra o $-Vcc$ (por lo tanto, cátodo común) y el LED muestra dígitos cuando se suministra un nivel alto a los ánodos individuales.
    
* Tipo de ánodo común: en este tipo de $display$, todos los ánodos de los siete LEDs están conectados a $+Vcc$ (por lo tanto, ánodo común) y el LED muestra dígitos cuando se suministra un nivel al bajo a los cátodos individuales.


En las siguientes figuras se muestra cómo se distribuyen los 7 segmentos en el *display* cuando se tiene una configuración de ánodo común:

<p align="center">
 <img src="/pics/lab03/segm.png" alt="alt text" width=500 >
</p>


<p align="center">
 <img src="https://exploreembedded.com/wiki/images/1/1a/0SevenSegment.gif" alt="alt text" width=400 >
</p>



### Primera parte: Diseño BCD a 7seg

Pasos a seguir:

1. Definir el bloque funcional del diseño:

    <p align="center">
        <img src="/pics/lab03/bcd7seg_block.png" alt="alt text" width=500 >
    </p>


    Como se evidencia, el bloque tiene un puerto de entrada  llamado ```BCD``` de 4 bits y un puerto de salida llamado ```Sseg``` de 7 bits, lo que concuerda con lo mencionado anteriormente.


    <!-- Como se evidencia, el bloque tiene un puerto de entrada  llamado ```BCD``` de 4 bits y un puerto de salida llamado ```Sseg``` de 7 bits, lo que concuerda con lo mencionado anteriormente, pero también tiene una salida llamada ```an``` de 4 bits. Esta salida se llama así por "ánodo" y se debe a que la tarjeta de desarrollo cuenta con 4 $displays$ de 7 segmentos y debemos indicarle cuál de estos $displays$ vamos a usar, por eso consta de 4 bits, cada uno de los cuales corresponde a uno de los $displays$.  -->

2.  Definir la descripción funcional del diseño:

    Para ello recuerde que puede hacer uso sea, de las tablas de verdad o de la descripción algorítmica del decodificador BCD a 7 segmentos.

3. Describir usando HDL el comportamiento del diseño.

4. Simulación del diseño.

5. Implementación: en la tarjeta correspondiente implemente y valide el funcionamiento, recuerde definir el *pinout*.


### Segunda parte: Visualización Dinámica 4 *Displays* de 7 Segmentos

En muchas aplicaciones se requiere más de un *display* de 7 segmentos, por lo que es necesario generar una visualización tal que sea necesario el menor número de pines para conectar todos los display con la tarjeta de desarrollo.

<!-- En la parte 1 se visualizaba el número en un sólo *display* de 7 segmentos. Pero en la mayoría de los casos, los 7 pines de los ánodos de cada LED están interconectados entre cada *display*, como se observa en la siguiente figura:

<p align="center">
 <img src="../figs/displays.jpeg" width=350 >
</p> -->

<!-- 
Por lo tanto, se debe realizar una multiplexación entre los ánodos de cada *display*, con el fin de visualizar en cada *display* un dígito diferente. En otras palabras, en cada instante de tiempo, sólo un display se encontrará activo, por lo que se debe garantizar que el destello en la visualización entre cada *display* no sea percibido por el ojo humano para así poder represetar un número de 4 dígitos usando los 4 displays dispoibles. Para ello, cada *display* debe activarse máximo cada $16\ ms$.

A continuación se muestra el diagrama estructural de esta implementación:

<p align="center">
 <img src="../figs/displays.png" width=350 >
</p> -->
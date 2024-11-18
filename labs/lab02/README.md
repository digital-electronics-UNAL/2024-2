## Objetivos de aprendizaje

* Introducir los conceptos fundamentales de la descripción de hardware digital, a través de los enfoques estructural y comportamental, realizando de la implementación de un sumador de 1 bit.  

* Comprender y aplicar el concepto de instanciación de módulos en Verilog mediante la implementación de un sumador de 4 bits. 

* Desarrollar un testbench para simular el comportamiento de ambos enfoques y verificar que las salidas corresponden a la tabla de verdad del sumador completo.

# Parte 1: Sumador de 1 bit

En diseño digital, un sumador de 1 bit es un circuito combinacional que realiza la suma de dos bits junto con un bit de acarreo de entrada. Es uno de los bloques fundamentales en la construcción de sumadores de mayor tamaño, que son esenciales en operaciones aritméticas dentro de procesadores y sistemas digitales. También se conoce como sumador completo.

El sumador de 1 bit toma tres entradas: los dos bits que se desean sumar (```A``` y ```B```) y un bit de acarreo de entrada (```Ci```) que puede provenir de una posición menos significativa en un sumador más grande. El circuito produce dos salidas: el bit de suma (```So```) y el bit de acarreo de salida (```Co```). A continuación se muestra su respectivo bloque funcional:



<p align="center">
 <img src="/pics/lab02/1bit.png" alt="alt text" width=300 >
</p>
<p align="center">
 Figura 1
</p>



A continuación se presenta la tabla de verdad del sumador completo de 1 bit.

<p align="center">

|   A  |   B  |  Ci |   Co  |   So  |
|------|------|-----|-------|-------|
|   0  |   0  |  0  | **0** | **0** |
|   0  |   0  |  1  | **0** | **1** |
|   0  |   1  |  0  | **0** | **1** |
|   0  |   1  |  1  | **1** | **0** | 
|   1  |   0  |  0  | **0** | **1** |
|   1  |   0  |  1  | **1** | **0** |
|   1  |   1  |  0  | **1** | **0** |
|   1  |   1  |  1  | **1** | **1** | 
</p>


A partir de la tabla de verdad, mediante **mapas de Karnaugh**, se obtienen las expresiones que definen el sumador de 1 bit, las cuales son:

<p align="center">
<img src="/pics/lab02/karnaugh.png" alt="alt text" width=800 >
</p>

A partir de las expresiones obtenidas se puede construir el siguiente circuito:

<p align="center">
<img src="/pics/lab02/Circuito_sumador.png" alt="alt text" width=600 >
</p>
<p align="center">
 Figura 2
</p>

### Implementación en HDL


#### Lógica combinacional:

La lógica combinacional es un tipo de circuito lógico donde las salidas en cualquier instante de tiempo dependen únicamente de las combinaciones actuales de las entradas, sin depender de estados anteriores o memorias internas.

#### 1. Implementación estructural (empleando primitivas):


En el contexto HDL, las primitivas se refieren a las puertas lógicas básicas y otros elementos fundamentales que se utilizan para construir circuitos lógicos. Estas primitivas son bloques de construcción básicos que se pueden utilizar para diseñar circuitos más complejos. Verilog incluye primitivas predefinidas que permiten describir el comportamiento del *hardware* de manera simple y directa.

  * **Características de las primitivas:**

    * **Básicas:** Son los bloques de construcción más elementales en el diseño de circuitos lógicos.

    * **Predefinidas:** En Verilog, estas primitivas están predefinidas y listas para ser utilizadas sin necesidad de definirlas manualmente.

    * **Directas:** Facilitan la implementación de funciones lógicas simples, como sumar bits, realizar operaciones de control, etc.
  
    * **Eficientes:** Su uso es eficiente en términos de síntesis, ya que se mapean directamente a los recursos de *hardware* básicos.

#### 2. Implementación comportamental:

En la implementación basada en comportamiento o implementación de alto nivel se utiliza un enfoque más abstracto para describir el comportamiento del circuito en lugar de utilizar puertas lógicas primitivas. Este tipo de implementación se enfoca en especificar qué se debe hacer, más que en cómo se hace a nivel de *hardware*. Este enfoque simplifica la descripción del comportamiento del sumador al evitar el detalle de las puertas lógicas primitivas, facilitando así la comprensión y la mantenibilidad del código.


[Parte 2.------------------------------------------------------------]: #


## Parte 02: Sumador de 4 bits


Para crear un sumador de 4 bits, se utilizan cuatro sumadores de 1 bit conectados en serie. Así, el acarreo de salida de un sumador de 1 bit se convierte en el acarreo de entrada del siguiente sumador. Cada bit de los dos números que se están sumando se procesa de manera paralela. 

Para construir un sumador de 4 bits utilizando el sumador de 1 bit como módulo base, se debe **instanciar** varios módulos del sumador de 1 bit y conectar sus entradas y salidas de manera que manejen el acarreo entre cada bit.

Un sumador de 4 bits suma dos números de 4 bits (```[3:0] A``` y ```[3:0] B```) y produce una suma de 4 bits (```[3:0] So```) y un acarreo de salida (```Co```). Para lograr esto, se utilizan 4 sumadores de 1 bit, cada uno manejando una posición de la salida ```So``` (0 a 3) y el acarreo hacia la siguiente posición.  A continuación se muestra su respectivo bloque funcional:

![fpga](/pics/lab02/4bit.png)
<p align="center">
 Figura 3
</p>


La implementación del sumador de 4 bits utilizando instancias del sumador de 1 bit es un ejemplo de diseño estructural en HDL, en donde se utiliza el sumador de 1 bit para construir un sumador de 4 bits de manera modular.

### Funcionamiento

* Cada instancia del sumador de 1 bit toma 1 bits de las entradas ```A``` y ```B```, y un acarreo de entrada Ci. Calcula la suma de estos bits y produce una suma de un bit ```So``` y un acarreo de salida ```Co```.

* El acarreo de salida de un sumador de 1 bit se usa como acarreo de entrada para el siguiente sumador de 1 bit en la cadena.

* El sumador de 4 bits produce una salida final ```So``` de 4 bits y un acarreo de salida final ```Co```.

### Concepto de instancia

En el contexto de diseño digital y descripción HDL, una instancia se refiere a la creación de un módulo a partir de una definición previamente definida. Instanciar un módulo significa utilizar el módulo definido anteriormente como un bloque en un diseño más grande, proporcionando conexiones específicas para las entradas y salidas del módulo.

En Verilog podemos utilizar la siguiente sintaxis:

```
module_name      instance_name(.port_0(signal_0),..,.port_n(signal_n))
```


donde: 

* ```module_name```: Es el nombre del módulo que queremos instanciar.

* ```instance_name```: Es el nombre de la instancia que vamos a generar a nivel local.

* ```port_0``` ... ```port_1```: Representa al nombre del puerto o variable declarada como entrada o salida del módulo que queremos instanciar, es decir, los nombres de los puertos que aparecen en el prototipo de dicho módulo.

* ```signal_0``` ... ```signal_n```: Corresponde al nombre de las señales que tenemos en el módulo en el cual nos encontramos trabajando y que nos servirán para interactuar con otres del diseño dentro de dicho módulo.


## Entregables

### Parte 1

1. Realice las descripciones del sumador de 1 bit (estructural y comportamental) de acuerdo a las indicaciones que se verán en la clase de laboratorio.

2. Explique el item anterior en su respectivo archivo ```README.md```.

3. Realice la respectiva simulación de las dos descripciones y muestre evidencias en su respectivo archivo ```README.md```, corroborando que se cumple la tabla de verdad descrita anteriormente.

4. Implemente la descripción HDL en la tarjeta de desarrollo, empleando la ```IDE Quartus``` y muestre en el laboratorio el funcionamiento del sumador de 1 bit, empleando interruptores como las entradas y LEDs como las salidas. 


5. Para que visualice lo expuesto en la sección **Comparación**, en la ```IDE Quartus```, luego de *sintetizar* cada una de las descripciones HDL, vaya al menú ```Tools```, seleccione la opción ```Netlist viewer``` y luego la opción ```RTL viewer```. Compare ambos diagramas y muestre las respectivas evidencias en el archivo ```README.md```.


### Parte 2

1. Realice la descripción del sumador de 4 bits de acuerdo a las indicaciones que se verán en la clase de laboratorio.
   
2. Explique el item anterior en su respectivo archivo ```README.md```.

3. Realice la respectiva simulación  y muestre evidencias en su respectivo archivo ```README.md```, corroborando el correcto funcionamiento del circuito. 

4. Implemente la descripción HDL en la FPGA, empleando la ```IDE Quartus``` y muestre en el laboratorio el funcionamiento del sumador de 4 bits, empleando interruptores como las entradas y LEDs como las salidas. 



# *Digital* - Simulador de circuitos

1. [Breve descripción](#breve-descripción)

2. [Instalación](#instalación)

3. [Documentación](#documentación)

---------

## Breve descripción

***Digital*** es un simulador de circuitos digitales escrito en Java e inspirada por [Logisim](http://www.cburch.com/logisim/). Entre sus principales funcionalidades están:

#### 1. Diseño y Simulación de Circuitos Lógicos

* Creación de circuitos utilizando puertas lógicas (AND, OR, NOT, XOR, NAND, NOR).

* Simulación interactiva en tiempo real del comportamiento lógico.
    
* Uso de flip-flops (D, T, JK, SR) para circuitos secuenciales.

* Diseño de contadores, registros y otros componentes avanzados.

* Personalización de entradas y salidas (interruptores, botones, LEDs, displays).

#### 2. Exportación y generación de HDL

* Generación automática de código HDL (como VHDL o Verilog) a partir del diseño del circuito.

#### 3. Herramientas de análisis y depuración

* Simulación paso a paso: Permite analizar cómo fluye la información en el circuito.
    
* Permite observar en tiempo real los cambios en señales y estados.
    
* Uso de sondas para monitorear valores en nodos específicos.

#### 4. Componentes predefinidos y personalizables

* Uso de componentes básicos (multiplexores, demultiplexores, codificadores, decodificadores).
    
* Creación de componentes personalizados reutilizables.

* Incluye memorias (ROM, RAM).

## Instalación


1. Verifique si tiene instalado Java.

    ***Digital*** depende de Java, por lo que primero se debe instalar una versión compatible. 

    ```
    java -version
    ```

    En caso de que ya cuente con una versión LTS de Java, continue con el paso **4**.

2. Instale la versión LTS, para el momento de realización del presente tutorial es Java 11

    ```
    sudo apt install openjdk-11-jdk -y
    ```

3.  Verifique la instalación:

    ```
    java -version
    ```


4. Descargue el paquete ***Digital*** desde GitHub:

    ```
    wget -O digital.zip https://github.com/hneemann/Digital/releases/latest/download/Digit
    ```

5. Descomprima el archivo y ejecute el *script* de instalación incluido en ***Digital***:

    ```
    unzip digital.zip
    cd Digital
    ./install.sh
    ```

6. Cree un enlace simbólico en ```/usr/local/bin``` para ejecutar ***Digital*** fácilmente desde cualquier directorio:

    ```
    sudo ln -sr ./Digital.sh $LBIN/Digital.sh
    ```

7. Finalmente ejectute ***Digital***:

    *  Desde la terminal:

        Gracias al enlace simbólico creado en ```/usr/local/bin```, se puede simplemente escribir el siguiente comando en la terminal para ejecutar ***Digital***:

        ```
        Digital.sh
        ```

    * Algunos entornos de escritorio, como GNOME o KDE, escanean los directorios como ```/usr/local/bin``` o ```/usr/bin``` para detectar aplicaciones que puedan estar disponibles en el sistema. Dado que, gracias al paso **6**,  ```Digital.sh``` se encuentra en uno de estos directorios, el entorno gráfico puede generar automáticamente un acceso directo en el menú de aplicaciones, en otras palabras, se puede encontrar ***Digital*** en el menú de aplicaciones del SO.

## Documentación

1. El repositorio de ***Digital*** es un proyecto *open source* que se encuentra en [GitHub *Digital*](https://github.com/hneemann/Digital?tab=readme-ov-file).

2. [Documentación en español](/docs/simulador_digital_espanol.pdf).
# Tutorial de implementación en la FPGA Cyclone IV usando Quartus Prime lite

Índice:

  - [Configuración básica para crear un nuevo proyecto](#configuración-básica-para-crear-un-nuevo-proyecto)
  - [Pasos para realizar la implementación](#pasos-para-realizar-la-implementación)

      1. [Seleccionar el módulo principal](#1-seleccionar-del-módulo-principal-top-level-module)
      2. [Configurar el Pin-Planer](#2-configurar-el-pin-planner)
      3. [Ejecutar el flujo de implementación del diseño](#3-ejecutar-el-flujo-completo-de-implementación-del-diseño)
      4. [Cargar el diseño en la FPGA](#4-cargar-el-diseño-en-la-fpga)
            

---
## Configuración básica para crear un nuevo proyecto

* Una vez instalado, debe abrir ```Quartus```.
* En la barra de herramientas, navegar en el menú ```File``` y hacer click en  ```New Project Wizard```.

  ![proyectWizard](/pics/lab02/f1.png) 

* **Directory, Name, Top-Level Entity**,  seleccione el directorio donde desee guardar el proyecto y el nombre del mismo. Tenga presente que debe colocar el nombre del módulo top en la tercera casilla (puede ser el mismo del proyecto). 
    ***Recuerde:*** El nombre del módulo-top es sensible a mayúsculas.

  ![proyectWizard](/pics/lab02/project.png)

* **Project Type**: Seleccione el template ```Empy project```.

* **Add File**: Si ya cuenta con los archivos fuente HDL adicionelos en esta sección. De igual manera, se pueden agregar archivos fuente más adelante.

*  **Family, Device & Board Settings**:  Seleccione la referencia de la FPGA  que se va a utilizar, en este caso ```EP4CE10E22C8```. Para mayor comodidad, busque el nombre en la casilla  ```Name filter``` y, por último, seleccione en el panel  ```Available devices``` dicha reerencia.

   ![proyectWizard](/pics/lab02/device.png) 


* **EDA Tool Settings**: Espeficar la herramienta de simulación que se va a utilizar, se recomiendan  ```ModelSim```  o ```Questa```. 
 ![proyectWizard](/pics/lab02/f4.png) 

* **Summary**: Se debe revisar que la información de este panel esté acorde según la configuración deseada.

  ![proyectWizard](/pics/lab02/f4b.png) 





## Pasos para realizar la implementación

**Después de que haya realizado la respectiva simulación y haya verificado que el diseño se comporta de acuerdo a lo esperado siga los pasos enlistados a continuación:**

### 1. Seleccionar del módulo principal (```top-level module```):

1. Una vez haya creado un nuevo proyecto, aparecerá éste en la sección ```Project Navigator``` &rarr; ```Hierarchy```. 

2. Haga click derecho en el nombre del proyecto dentro  de la lista **Entity_:Instance** y escoja la opción **Settings** o en el menú **Assignments** &rarr; **Settings**. 

      ![project_config](/pics/lab02/project_config.png)

3. En la ventana ```Settings``` escoger la opción  **Files**  en la lista **Category**. 

4. En el botón ```...``` seleccionar el archivo HDL creado anteriormente (**sum1bcc.v** o **sum1bcc_primitive.v**), que debe estar en el mismo directorio del proyecto. Hacer click en el botón ```Add``` para incluirlo en el proyecto.

      ![project_config](/pics/lab02/project_config_files.png)

5. Escoja la opción  **General**  en la lista **Category**.

6. En la sección **Top-level entity** haga click en el botón ```...```, lo que  desplegará un cuadro de diálogo, en donde se enlistaran los nombres de los módulos definidos en los archivos incluidos anteriormente. Seleccionar el módulo correspondiente. Este paso consiste en definir un módulo **Top** para el proyecto.

      ![project_config](/pics/lab02/project_config_top.png)

### 2. Configurar el Pin-Planner:

Es indispensable asignar las señales de entrada y salida del diseño a pines físicos específicos del FPGA. Esto es crucial porque el FPGA necesita saber qué pines físicos en el dispositivo estarán conectados al mundo externo, ya sea a sensores, actuadores, señales de control, relojes, o cualquier otro periférico. Para ello, en la barra **Standard** (que está debajo de la barra de menús), se debe seleccionar el icono de ```Pin Planer``` que abrirá dicha ventana, donde se encontrará el pinout de la FPGA, como se muestra en las siguientes imágenes:

![pin_planner](/pics/lab02/pin_planner.png)


![pin_planner](/pics/lab02/pin_planner2.png)


En la parte inferior de la ventana ```Pin Planer``` se puede observar una tabla con las entradas y salidas del diseño, en este caso del sumador de 1 bit.

1. En la columna ```Node name``` se verán los nombres de los puertos del diseño.

2. En la columna ```Location``` se podrá seleccionar los pines de la FPGA asociados a ciertos elementos, en este caso, se van a usar switches para las entradas y leds para las salidas, dicha numeración se podrá observar directamente en la FPGA o en su *datasheet*.

Posteriormente se debe dar doble click a la opción ```Run I/O Assignment Analysis``` que se encuentra en la sección ```Task```, en la parte izquierda de la ventana ```Pin Planer```.



### 3. Ejecutar el flujo completo de implementación del diseño:

En la sección ```Task``` se podrán visualizar las etapas del flujo completo de implementación del diseño, se puede ejecutar el flujo completo únicamente haciendo click en ```Compile Desing``` o se pueden ejecutar las etapas una a una, las cuales se desglosan a continuación:

1. **Analysis & Synthesis**: 

      ![synthesis](/pics/lab02/synthesis.png)

   Está opción permite que el *software* realice varios pasos para transformar el diseño de alto nivel (escrito en lenguaje HDL) en una representación que pueda implementarse en la FPGA, estos pasos son:

      1. Análisis del código:

            * Chequear errores de sintaxis.
            * Resolución de dependencias: Si el diseño incluye varios módulos, se verifica que todas las referencias sean válidas y que los módulos necesarios estén disponibles.
            * **Elaboración**: El compilador descompone el diseño jerárquico, identificando todas las entidades, módulos o bloques usados, es decir, toma el módulo principal (```top-level module```) y encuentra todos los submódulos, componentes, o bloques que utiliza. Además traduce todas las conexiones entre módulos en una lista clara y comprensible, también se asegura de que los parámetros tengan valores válidos y genera una versión "aplanada" del diseño. 
            
            Sin esta etapa, el compilador no podría:

            - Detectar errores de conexión o de uso incorrecto de submódulos.
            - Optimizar correctamente el diseño.
            - Mapearlo al hardware físico del FPGA.

      2. Síntesis del diseño:

            * Traducción a una red lógica: El diseño en HDL se convierte en una descripción a nivel de puertas lógicas, como compuertas AND, OR, flip-flops, multiplexores, etc.
            * Optimización lógica: Se aplican técnicas para reducir el tamaño del circuito o mejorar su rendimiento, eliminando redundancias y combinaciones ineficientes.
            * Mapeo a bloques lógicos configurables de la FPGA: El diseño lógico se traduce a los bloques físicos disponibles en el FPGA, como LUTs (*Look-Up Tables*), *flip-flops*, y otros elementos.

      3. Generación del ```Netlist```:

            Genera un archivo que describe cómo se conectan todos los elementos lógicos entre sí. Este ```netlist``` es el punto de partida para las etapas posteriores (como *Fitting* y *Place-and-Route*).

      4. Chequeo de restricciones:

            Verifica que las restricciones definidas por el usuario, como el uso de pines específicos, tiempos de reloj o límites de área, sean compatibles con el diseño.

      5. Reporte de resultados

            Al final del proceso, ```Quartus``` genera un reporte que incluye:
            * La cantidad de recursos utilizados (LUTs, *flip-flops*, etc.).
            * Advertencias o errores encontrados.
            * Estadísticas de optimización.

2. **Fitter (Place & Route)**: 

      Es una etapa crucial en el flujo de diseño de en FPGA. Su función principal es tomar el diseño lógico sintetizado y asignarlo a los recursos físicos de la FPGA, asegurándose de que el diseño sea implementable dentro de las limitaciones del dispositivo.

      1. Colocación (*Place*): En esta etapa, el *Fitter* asigna las partes lógicas del diseño (como compuertas, flip-flops, bloques RAM, etc.) a ubicaciones específicas dentro de la FPGA.

      2. Ruteo (*Route*): Una vez que los bloques lógicos están colocados, el *Fitter* conecta los recursos utilizando las interconexiones físicas disponibles en la FPGA.

      3. Verificación de restricciones: El *Fitter* también verifica que el diseño cumpla con todas las restricciones físicas y temporales:

            * Restricciones físicas: Que las señales de entrada/salida estén asignadas a pines válidos. Que no se exceda la capacidad del dispositivo (como el número de LUTs, flip-flops, pines, etc.).

            * Restricciones de temporización: Si se han definido tiempos de reloj, tiempos de llegada, o tiempos de propagación máximos, el ```Fitter``` asegura que se cumplan o genera advertencias o errores si no es posible.

      4. Generación de resultados: Al finalizar, el ```Fitter``` produce:

            * Un diseño físico implementable para ser configurado en la FPGA.
            * Un informe detallado sobre: 

            1. Cómo se asignaron los recursos.
            2. Si hubo problemas con las restricciones.
            3. Estadísticas sobre el uso de recursos (uso de LUTs, *flip-flops*, bloques de memoria, etc.).
            4. Análisis de temporización (si se cumplieron los tiempos definidos).

### 4. Cargar el diseño en la FPGA


Ahora sólo resta transferir el archivo de configuración generado en el paso anterior a la FPGA, para ello, en la ventana principal de ```Quartus```, se debe dar doble click en la opción ```Program Device (Open Programmer``` que aparece en la sección ```Task```, que abrirá la ventana  ```Programmer``` como se muestra en la imagen.

![programmer](/pics/lab02/programmer.png)


En la ventana  ```Programmer``` se debe dar click al botón ```Hardware Setup``` que abrirá usa sub ventana en donde se debe seleccionar el programador ```USB-blaster``` como se muestra en la imagen.

![hw_setup](/pics/lab02/hardware_setup.png)


* Finalmente, en la ventana  ```Programmer``` se debe dar click al botón ```Start``` que iniciará la configuración de la FPGA, la cual pueden  observar en la barra de progreso (***No desconectar ni mover las conexiones a la FPGA mientras no vean la barra de progreso completada***) como se ve en la siguiente imagen.

![programmer100](/pics/lab02/programmer_100.png)









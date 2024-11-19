# Tutorial de Implementación en la FPGA Cyclone IV

Índice:

- [Tutorial de Implementación en la FPGA Cyclone IV](#tutorial-de-implementación-en-la-fpga-cyclone-iv)
  - [Configuración básica para un nuevo proyecto en Quartus Prime lite](#configuración-básica-para-un-nuevo-proyecto-en-quartus-prime-lite)
  - [Implementación](#implementación)

---
## Configuración básica para un nuevo proyecto en Quartus Prime lite

* Una vez instalado, debe abrir el programa ´Quartus´.
* En la barra de herramientas (toolbar) de Quartus, navegar en el menú ```File``` y hacer click en  ```New Project Wizard```. (ver imagen)

![proyectWizard](/pics/lab02/f1.png) 

* **Directory, Name, Top-Level Entity**,  seleccione el directorio donde se guarda el proyecto y el nombre del mismo. Tenga presente que debe colocar el nombre del módulo top en la tercera casilla, puede ser el mismo del proyecto. (ver imagen) 
    ***Recuerde:*** El nombre del módulo-top es sensible a mayúsculas.

![proyectWizard](/pics/lab02/f2.png)

* **Project Type**, seleccione el template ```Empy project```.

* **Add File**, si ya cuenta con los archivos fuentes de HDL adicione los ficheros respectivos. De igual manera, pueden agregar archivos fuentes más adelante.

*  **Family, Device & Board Settings**,  Busque la tarjeta de desarrollo o la referencia de la FPGA  que se va a utilizar, ```10M50DAF484```, si considera necesario busque el nombre en la casilla  ```Name filter```, seleccione en el panel  Available devices el dispositivo usado. (ver imagen)

![proyectWizard](/pics/lab02/f3.png) 


* **EDA Tool Settings**,  espeficar la herramienta de simulación que se va a utilizar, se recomiendan  ```ModelSim``` (ver imagen) o ```Questa```. 

![proyectWizard](/pics/lab02/f4.png) 

* **Summary**, se debe revisar que la información de este panel esté acorde según la configuración realizada . (ver imagen)

![proyectWizard](/pics/lab02/f4b.png) 





## Implementación

1. Una vez haya creado un nuevo proyecto, aparecerá éste en la sección ```Project Navigator``` &rarr; ```Hierarchy```. 

2. Hacer click derecho en el nombre del proyecto dentro  de la lista **Entity_:Instance** y escoger la opción **Settings** o en el menú **Assignments** &rarr; **Settings**. 

      ![project_config](/pics/lab02/project_config.png)

3. En la ventana ```Settings``` escoger la opción  **Files**  en la lista **Category**. 

4. En el botón ```...``` seleccionar el archivo HDL creado anteriormente (**sum1bcc.v** o **sum1bcc_primitive.v**), que debe estar en el mismo directorio del proyecto. Hacer click en el botón ```Add``` para incluirlo en el proyecto.

      ![project_config](/pics/lab02/project_config_files.png)

5. Escoger la opción  **General**  en la lista **Category**.

6. En la sección **Top-level entity** hacer click en el botón ```...```, lo que  desplegará un cuadro de diálogo, en donde se enlistaran los nombres de los módulos definidos en los archivos incluidos anteriormente. Seleccionar el módulo correspondiente. Este paso consiste en definir un módulo Top para el proyecto.

      ![project_config](/pics/lab02/project_config_top.png)

7. Finalmente podrá hacer doble click en la opción **Analysis & Synthesis**. 

      ![synthesis](/pics/lab02/synthesis.png)





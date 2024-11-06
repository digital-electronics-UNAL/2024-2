# FPGA Design Software - Quartus

## Descargar e instalar Intel Quartus Prime:

* Descargue los archivos de instalación de Quartus Prime lite del siguiente [link](https://www.intel.com/content/www/us/en/software-kit/825277/intel-quartus-prime-lite-edition-design-software-version-23-1-1-for-linux.html):

    * Seleccione la última versión  y  seleccione el sistema operativo, en este caso Linux!
    *  Descargue el archivo ```.run```.

        ![download_quartus](/pics/quartus_1.png)


* Instalación:
    * Cambie los permisos del archivo ```.run``` mediante la ejecución del siguiente comando en terminal: 

        ``` 
        chmod +x *.run
        ```
        Reemplace ```*```  con el nombre del archivo ```.run```.

    * Ejecute el instalador con:

        ``` 
        ./*.run
        ```
        Reemplace ```*```  con el nombre del archivo ```.run```.

## Configuración de las variables de entorno

Al agregar la ruta de instalación de Quartus a la variable de entorno ```PATH```, se define en dónde el sistema operativo puede encontrar el ejecutable de Quartus. Esto permite ejecutar el comando ```quartus``` desde cualquier ubicación en la terminal, simplificando el acceso a la herramienta. Esto se puede hacer de la siguiente manera:

1. Busque el archivo ```.bashrc``` del sistema: 

    El archivo ```.bashrc``` es esencial para personalizar y optimizar la experiencia en la terminal al pegrmitir configuraciones específicas del usuario, ejecutar comandos automáticamente al iniciar una sesión y facilitar el uso de herramientas mediante alias y funciones personalizadas.

    Generalmente se encuentra en el directorio ```home``` del usuario. Para verlo desde el gestor de archivos, solo se necesita habilitar la visualización de archivos ocultos, o se puede abrir la carpeta ```home``` a través de un editor de código y allí debería verlo.

2. Agregue las siguientes lineas en el archivo ```.bashrc```:
    
    ```
    export ALTERAPATH="/home/user*/intelFPGA_lite/23.1std/" 
    export QUARTUS_ROOTDIR=${ALTERAPATH}/quartus
    export QUARTUS_ROOTDIR_OVERRIDE="$QUARTUS_ROOTDIR"
    export PATH=$PATH:${ALTERAPATH}/quartus/sopc_builder/bin
    export PATH=$PATH:${ALTERAPATH}/nios2eds/bin
    export PATH=$PATH:${QSYS_ROOTDIR}
    ```

    Asegurese  de que el nombre del directorio corresponde al que fue instalado.

    Reemplace ```user*``` con la correspondiente cuenta de usuario en su computador.


3. Cree el link simbólico:

    El siguiente comando crea un link simbólico llamado ```quartus``` en el directorio ```/bin``` que apunta al ejecutable de Quartus ubicado en el directorio de instalación especificado. Esta configuración simplifica la ejecución de Quartus al permitir simplemente escribir ```quartus``` en la terminal desde cualquier ubicación.

    ```
    sudo ln -s $QUARTUS_ROOTDIR/bin/quartus /bin/quartus
    ```

Ahora podrá ejecutar la IDE Quartus utilizando el comando ```quartus``` en la terminal.


## Inslación de la herramienta de simulación Questa

### Descargar instalador

* Descargar los archivos Questa*-Intel® FPGA Edition (includes Starter Edition) del siguiente [link](https://www.intel.com/content/www/us/en/software-kit/776289/questa-intel-fpgas-pro-edition-software-version-23-1.html). Se debe descarga tanto el archivo con extensión ```.run``` como la parte II que tiene extensión ```.qdz``` en el mismo directorio.
* Tenga en cuenta que la descarga de estos archivos tomará tiempo.
* Para el presente tutorial se descargó la versión 23.1.

###  Instalación

* En la terminal de linux:

 ```
    chmod +x nombre_archivo.run
    ./nombre_archivo.run
```

* Se abrirá el instalador:

    ![questa](/pics/questa.jpeg) 


    - Dar click en siguiente y seleccionar la opción ```Questa - Intel FPGA Starter Edition```.

    - Dar click en siguiente y aceptar los términos y condiciones.

    - Dar click en siguiente y seleccionar la carpeta de destino de la instalación.

    - Dar click en siguiente y revisar el resumen.

    - Dar click en siguiente con lo cual empezará la instalación 



### Descargar y configurar la licencia

Es necesario descargar la licencia de Questa para lo cual se debe:

* Ingresar al Self-Service Licensing Center de Intel en el siguiente [link](https://licensing.intel.com/psg/s/?language=en_US).

* Inscribirse en la opción [Enroll for Intel® FPGA Self Service Licensing
Center (SSLC)](https://www.intel.com/content/www/us/en/secure/forms/fpga-sslc-registration.html). 

* Loggerase en la opción [Already enrolled ? - Sign In here ](https://login.microsoftonline.com/46c98d88-e344-4ed4-8496-4ed7712e255d/oauth2/authorize?client_id=2793995e-0a7d-40d7-bd35-6968ba142197&redirect_uri=https%3A%2F%2Flauncher.myapps.microsoft.com%2Fapi%2Fsignin-oidc&response_type=code&scope=openid%20profile%20offline_access&code_challenge=l621EbMpMd8XCMUt32fOkdVx4LQ85OhcOiA9DS9mPMQ&code_challenge_method=S256&response_mode=form_post&nonce=638435098500409634.ZjJmMDY1YzYtZjM0OC00YmIxLWI4NWUtNTlkMmU0MGJjYzgxZmY1ZjkyNDgtOGIxOS00YmEyLTk1ZjctODIxOGQ1ZjYwMjA4&client_info=1&x-client-brkrver=IDWeb.2.13.2.0&state=CfDJ8E3NALe6oY1JvkTnnsQsCGyFKIDx-4SbDtmZoJPUlgmKjsHRPSR5otWRAPY5N420c27dON5pWiPUFCv8RYxYwnS4IEfWxDcSsGyPwd4qgm_yFUW2Oc6q80X7YhH4M6Qm0icDBQ4KM6MI5OzEtjYAfBNwkfCX42xjVa3wP9qfIrf5Pr9UpIKnh2Ao2bzxA05ltw07cQHfXxGVB4qWp75KPYLx1aplPrnEREmGZy_KRilW6ix08U5NCks8Y4ASbS2-LGUwR_HW6T163bZ8VvyPvFScu6rkH00tmrEEkvZ6EHNfnv9kpGW-CV_s2XG4xsm31sXMnamANcz5UcfPxQ3FW2k_y2X1tS7ckJu25ZbLLL98pTZ8rMueWU26653lNGb40l-6c1hmipyOPaWbfWtrfCq6IPKikdz_drSK3InXvBPoayBqA3UCZ-0bzxFzVDC1g3qFaycOLCFha2bAOn27QuT6xqexH-AZxmfCwnahlTfd3jJUCVaZ6Tvs17YtZT7R_CKJbsQr2BWkvql8oEUB7OI&x-client-SKU=ID_NET6_0&x-client-ver=6.35.0.0) (Intel Azure Portal). 
    - Se deben seguir todos los pasos, uno de ellos consiste en escanear un código QR, en caso de no ser posible use la opción ```I want to set up a different methode```,  con la cual se enviará un código  como mensaje de texto al número de celular que se ingrese.

     - Leer y aceptar términos de uso.

* Una vez realizados los anteriores pasos, se abrirá el siguiente portal:

    ![intel](/pics/intel.jpeg) 

    - Ingresar a la opción ```Sing up for Evaluation or No-Cost License```.


    - Seleccionar la opción ```Questa*-Intel® FPGA Starter``` y dar click en siguiente.

    ![intel2](/pics/intel2.jpeg) 

    - Se abrirá una interfaz para generar la licencia:

    ![intel3](/pics/intel3.jpeg) 

    - Dar click en ```+New Computer```.


- Diligenciar los campos requeridos:
    - En  ```Primary NIC ID``` deben escribir el nombre de la cuenta de usuario de su pc.
        
    - En ```License type``` seleccionar FIXED.

    - En ```Computer type``` seleccionar NIC ID.

    - Para saber el  ```Primary Computer ID```:

        En una terminal de Linux escribir el comando ```ifconfig```.

        El NIC ID corresponde al número de la mac del driver de wifi o ethernet, para wifi aparecerá en la opción ```wlp1s0``` junto a la palabra ```ether```.

        Copiar todo el string que está separado por dos puntos ":", pero en la casilla ```Primary Computer ID``` borrarlos, es decir, sólo dejar caracteres alfanuméricos.

    - Dar click en ```save```, aceptar términos de uso y dar click en ```generar```.

    - Recibirán un correo con un archivo adjunto con extensión ```.dat```  correspondiente a la licencia.

    - Descargar la licencia en el directorio de instalación.

* Configurar la licencia en la IDE de Quartus:

    - En el menú ```Tools``` abrir el ```License setup```.

    - En la casilla ```License file``` cargar el archivo de la licencia ```.dat``` que acabaron de generar.

*  Configuración de variables de entorno de la licencia:

    En el archivo ```.bashrc```: 

    ```
    export LM_LICENSE_FILE=path_del_archivo/nombre_archivo.dat
    ```



  *  *  *  *  *

<!-- ## Configuración básica para un nuevo proyecto en Quartus Prime lite

* Una vez instalado, debe abrir el programa ´Quartus´.
* En la barra de herramientas (toolbar) de Quartus, navegar en el menú ```File``` y hacer click en  ```New Project Wizard```. (ver imagen)

![proyectWizard](./pics/f1.png) 

* **Directory, Name, Top-Level Entity**,  seleccione el directorio donde se guarda el proyecto y el nombre del mismo. Tenga presente que debe colocar el nombre del módulo top en la tercera casilla, puede ser el mismo del proyecto. (ver imagen) 
    ***Recuerde:*** El nombre del módulo-top es sensible a mayúsculas.

![proyectWizard](./pics/f2.png) altera

* **Project Type**, seleccione el template ```Empy project```.

* **Add File**, si ya cuenta con los archivos fuentes de HDL adicione los ficheros respectivos. De igual manera, pueden agregar archivos fuentes más adelante.

*  **Family, Device & Board Settings**,  Busque la tarjeta de desarrollo o la referencia de la FPGA  que se va a utilizar, ```10M50DAF484```, si considera necesario busque el nombre en la casilla  ```Name filter```, seleccione en el panel  Available devices el dispositivo usado. (ver imagen)

![proyectWizard](./pics/f3.png) 


* **EDA Tool Settings**,  espeficar la herramienta de simulación que se va a utilizar, se recomiendan  ```ModelSim``` (ver imagen) o ```Questa```. 

![proyectWizard](./pics/f4.png) 

* **Summary**, se debe revisar que la información de este panel esté acorde según la configuración realizada . (ver imagen)

![proyectWizard](./pics/f4b.png)  -->


# Entregables 

Tener configurado el *framework* según los pasos anteriores.






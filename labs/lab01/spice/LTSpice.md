# Importar modelos en LTSpice


A continuación se detalla el procedimiento para importar modelos en LTSpice, usando como ejemplo las compuertar requeridas en el [lab01](/labs/lab01/).


1. Descargar los modelos ```.cir``` de ambas referencias que se encuentran en la carpeta [spice](/labs/lab01/spice/).

2. Abrir el archivo del modelo usando LTSpice y hacer click derecho sobre la línea donde inicia la definición del subcircuito, por ejemplo, para el caso de IC CD4069UB es:

```
.SUBCKT CD4069UB Y A VCC AGND
```
como se muestra en la siguiente imagen

<div align="center">
    <img src="/pics/CD4069UB_1.png" width="400" height="600">
</div>
<div align="center">
    Figura 1
</div>


3. En le menú que se despliega seleccionar ```Create Symbol``` lo que deberá abrir una nueva ventana en LTSpice con extensión ```.asy```, en donde podrá visualizar el componente como se muestra a continuación:

<div align="center">
    <img src="/pics/CD4069UB.png" width="200" height="200">
</div>

<div align="center">
    Figura 2
</div>


 Si desea crear un simbolo personalizado para el componente siga los pasos del siguiente ítem, de lo contrario guarde el archivo con extesión ```.asy``` en el directorio de componentes generados (```/generated```) de LTSpice, que por lo general se encuentra en la siguiente ubicación:

```
C:\users\*user\Local Settings\Application Data\LTspice\lib\sym\generated/
```

donde ```*user``` es el nombre de la respectiva cuenta de usuario en su pc.

Una vez guardado, en la ventana de LTSpice donde se crean los esquemáticos (con extesión ```.asc```) podrá encontrar el componente en la opción
 ```Component``` en la barra de iconos de LTSpice, u oprimiendo la tecla ```P```, allí deberá encontrar la carpeta ```generated``` como se muestra:

 <div align="center">
    <img src="/pics/ltspice_generated.png" width="600" height="400">
</div>
<div align="center">
    Figura 3
</div>


 y haciendo doble click se encontrará el componente.


 4. Para crear un simbolo personalizado para este componente, en la ventana con extesión ```.asy``` que se muestra en la figura 2, podrá eliminar el recuadro amarillo (no elimine ninguno de los puertos) y con las formas que encontrará en el menú ```View``` podrá crear el simbolo deseado, como se muestra a continuación:

 <div align="center">
    <img src="/pics/simb.png" width="300" height="200">
</div>
<div align="center">
    Figura 4
</div>


Recomendaciones:

* Debe arrastrar los puertos al extremo libre de cada línea correspondiente a cada puerto.

* Cerciorese de que el extremo que queda libre de cada línea correspondiente a cada puerto, coincida con exactitud con uno de los puntos de la grilla.

* Puede eliminar las etiquetas **A** y **Y** de los puertos de entrada y salida, para no saturar el simbolo, haciendo click derecho sobre el puerto y seleccionando ```NONE(Not visible)``` en la ventana ```Pin/Por Properties``` que se despliega. No recomiento eliminar las etiquetas de los puertos ```VCC``` y ```GND```.

Una vez creado el simbolo, guárdelo como se indica en el ítem anterior. 
    


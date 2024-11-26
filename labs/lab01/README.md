# COMPARACIÓN DE TECNOLOGÍA CMOS y TTL

La electrónica digital se encarga del procesamiento de señales eléctricas
mediante circuitos que operan con valores discretos. Sin embargo, estos valores
están representados en diferentes niveles de tensión/corriente, frecuencia, de tal
manera que su aplicación depende en gran medida de la tecnología de fabricación.

Para el desarrollo de esta actividad se estudiará la implementación de una operación
lógica en las tecnologías TTL y CMOS donde se observará las diferencias entre 
su circuito equivalente, tiempo de respuesta, entre otros.


## Objetivos

* Identificar las características de un dispositivo fabricado en diferentes tecnologías.

## Recursos requeridos

* Negador TTL 74LS04
* Negador CMOS CD4069
* Simulador
* Modelos spice
* Datasheets

## Procedimiento

### Parte 1

1. Comparar las especificaciones técnicas de cada uno de los dispositivo mencionados.
2. Determinar el circuito equivalente para cada uno de los dispositivos.
3. Aplicar una señal cuadrada de 1 KHz de tensión adecuada para medir: $V_{out}$ vs $V_{in}$ y a partir de la función de transferencia determinar
   $V_{IH}$, $V_{IL}$, $V_{OH}$, $V_{OL}$.
4. Medir el tiempo de subida ($t_r$), tiempo de bajada ($t_f$), tiempo de retardo ($t_{phl}$ y $t_{plh}$) para cada dispositivo.

### Parte 2

1. Determinar el fan-in y fan-out de cada uno de los dispositivos.
2. Determinar la disipación de potencia.
3. Proponer e implementar un circuito de entrada y de salida para cada uno de los dispositivos teniendo en cuenta los parámetros de cada tecnología para observar el comportamiento del mismo.

### Parte 3

1. Estudie el oscilador en anillo basado en la compuerta NOT.
![ring-osc](./ring-osc.svg)
2. Monte dos osciladores diferentes en anillo con el negador CMOS.
3. Observe de cada uno de ellos tanto la forma de onda como su frecuencia de oscilación.
4. Realice una comparación entre ambos osciladores según lo observado.

## A tener en cuenta


* Simular cada compuerta con su modelo spice variando la frecuencia de la señal de entrada.
* Comparar los resultados de los tiempo medidos en el laboratorio con los obtenidos en la simulación.
* Obtener la característica de $V_{in}$ vs $V_{out}$.
* Simular los osciladores en anillo.
* Comparar las mediciones.

## Entregables

Se requiere la entrega de un informe donde responda cada uno de los apartados teniendo en cuenta simulaciones, especificaciones técnicas de las compuertas utilizadas en esta práctica, mediciones obtenidas en el laboratorio de manera sustentada.

## Referencias

* [Qucs, instalación y ejemplos de uso](https://github.com/johnnycubides/qucs-tutorial-examples)
* [Modelos spices del 74LS04 y CD4069](./spice/)
* [Importar modelos en LTSpice](./spice/LTSpice.md)
* [Vídeo sobre niveles de tensión y corriente para algunas tecnologías de electrónica digital](https://www.youtube.com/watch?v=wCQ2D2S836I)

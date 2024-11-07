# COMPARACIÓN DE TECNOLOGÍA CMOS y TTL

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

1. Observar comparativamente las especificaciones técnicas de cada uno de los dispositivo mencionados.

2. Determinar el circuito equivalente para cada uno de los dispositivos.

3. Aplicar una señal cuadrada de 1 KHz para medir: $V_{out}$ vs $V_{in}$ y a partir de estos gráficos Determinar
   $V_{IH}$, $V_{IL}$, $V_{OH}$, $V_{OL}$.

4. Medir el tiempo de subida, tiempo de bajada, tiempo de retardo, tiempo de almacenamiento para cada dispositivo.

### Parte 2

1. Determinar el fan-in y fan-out de cada uno de los dispositivos.
2. Determinar la disipación de potencia.
3. Proponer e implementar un circuito de entrada y de salida para cada uno de los dispositivos teniendo en cuenta
Los parámetros de cada tecnología para observar el comportamiento del mismo.

## A tener en cuenta


* Simular cada compuerta con su modelo spice variando la frecuencia de la señal de entrada.
* Comparar los resultados de los tiempo medidos en el laboratorio con los obtenidos en la simulación.
* Obtener la característica de $V_{in}$ vs $V_{out}$.
* Comparar las mediciones

## Entrega

Se requiere la entrega de un informe donde responda cada uno de los apartados teniendo en cuenta simulaciones,
especificaciones técnicas de las tecnologías, mediciones obtenidas en el laboratorio de manera sustentada.

## Referencias

* [Qucs, instlación y ejemplos de uso](https://github.com/johnnycubides/qucs-tutorial-examples)

# Laboratorio 03: Visualización del nivel de carga

Índice:

1. [Objetivos de aprendizaje](#objetivos-de-aprendizaje)

2. [Planteamiento del problema](#planteamiento-del-problema)

3. [Requisitos funcionales](#requisitos-funcionales)

4. [Entregables](#entregables)

5. [Documentación de apoyo](#documentación-de-apoyo-necesaria)

*******


# Objetivos de aprendizaje

1. Integrar dispositivos de visualización robustos en un sistema digital, a través de la implementación de un decodificador para lograr dicha visualización en los displays de 7 de segmentos.
2. Implementar conversiones entre formatos binario y BCD.
3. Introducir el concepto de lógica secuencial y determinar las diferencias con la lógica combinacional.
4. Utilizar los pines I/O de la tarjeta de desarrollo para ampliar la entrada de datos.
5. Resolver problemas de adaptación del sistema a nuevas configuraciones de *hardware*.


# Planteamiento del problema

En sistemas digitales, es fundamental garantizar que los resultados de las operaciones realizadas por los circuitos sean fácilmente interpretables por los usuarios. Un ejemplo claro de esto es la necesidad de visualizar el resultado de un sumador binario. En este caso, se busca representar y mostrar los resultados de la suma de lecturas provenientes de sensores instalados en un banco de baterías.

En el laboratorio anterior, se implementó un sumador de 4 bits con dos operandos como parte de un sistema inicial. Sin embargo, el escenario ha cambiado y ahora se debe adaptar el sistema para manejar nuevas configuraciones del banco de baterías:

1. **Banco de 4 baterías**, cada una equipada con un sensor que proporciona una lectura de 4 bits. 

2. **Banco de 2 baterías**, cada una equipada con un sensor que proporciona una lectura de 8 bits.

Para ambos escenarios, el resultado del valor de carga total del banco debe visualizarse en un formato claro y legible, utilizando displays de 7 segmentos.

Adicionalmente, es necesario garantizar que las alarmas diseñadas previamente para alertar sobre niveles críticos o condiciones específicas continúen funcionando correctamente en estos nuevos escenarios. Esto implica adaptar la lógica de control del sistema para manejar los diferentes tamaños de operandos y asegurar la correspondencia adecuada entre los resultados visualizados y las señales de alarma generadas.

El problema radica en cómo implementar una solución que tome la lectura de cada sensor, calcule el valor de carga total del banco, convierta este resultado en Código Decimal Codificado en Binario (BCD) y lo traduzca en señales adecuadas para controlar los displays de 7 segmentos disponibles en la tarjeta de desarrollo. Esto requiere diseñar la lógica necesaria para la conversión de BCD a 7 segmentos, asegurando que cada dígito se visualice de manera precisa y clara en el *hardware* disponible.

# Requisitos funcionales

1. **Diseño del decodificador de 7 segmentos:** El sistema debe incluir un decodificador de 7 segmentos basado en lógica combinacional, el cual debe ser capaz de visualizar números del 0 al 9 en formato decimal y del 0 al F en formato hexadecimal en uno de los displays de 7 segmentos. Este decodificador es el primer paso y debe ser implementado y probado antes de realizar los cálculos necesarios para obtener el valor total de carga y sus respectivas visualizaciones en los siguientes pasos. Para lo anterior es necesario revisar la siguiente [documentación](/labs/lab03/bcd2sseg.md).

2. **Cálculo del valor de carga:** El sistema debe realizar las operaciones necesarias para obtener el valor de carga total del banco, empleando las lecturas proporcionadas por los sensores en dos configuraciones:

    1. Banco de 4 baterías con sensores que arrojan lecturas de 4 bits cada una.
    2. Banco de 2 baterías con sensores que arrojan lecturas de 8 bits cada una.

3. **Conversión a BCD:** El resultado debe ser convertido a BCD para su correcta interpretación.

4. **Visualización en displays de 7 segmentos:** El sistema debe mostrar el resultado del ítem **2** en displays de 7 segmentos, asegurando una representación clara y legible, utilizando el decodificador de 7 segmentos previamente diseñado.

5. **Compatibilidad con alarmas:** El sistema debe garantizar que las alarmas configuradas en el [lab02](/labs/lab02/README.md), para diferentes niveles de carga, funcionen correctamente en los nuevos escenarios del banco de baterías.

6. **Cambio de configuración del banco de baterías:** El sistema debe permitir alternar entre las dos configuraciones del banco de baterías (4 sensores de 4 bits o 2 sensores de 8 bits) sin necesidad de modificaciones manuales en el *hardware*.

7. **Implementación modular escalable:** El diseño completo debe constar de varios módulos para hacer el sistema escalable y claro, lo que facilitará también su validación y verificación. Cada grupo tendrá la libertad de decidir cómo organizar y conectar los módulos.

## Entregables

1. Realice la descripción de la solución a la problemática planteada de acuerdo a las indicaciones que se darán en la clase de laboratorio.

2. Explique el item anterior en su respectivo archivo ```README.md```.

3. Realice la respectiva simulación a la solución planteada y muestre evidencias en su archivo ```README.md```.

4. Implemente la descripción HDL en la tarjeta de desarrollo, empleando la ```IDE Quartus``` y muestre en el laboratorio el funcionamiento, empleando los periféricos que requiera. Para lograr este entregable es necesario revisar la siguiente [documentación](/labs/lab00/proyectoQuartus.md).

## Documentación de apoyo necesaria 

1. [Tutorial de implementación en la FPGA Cyclone IV](/labs/lab00/proyectoQuartus.md)

2. [Decodificador BCD a 7 segmentos](/labs/lab03/bcd2sseg.md)

<!-- 3. [Introducción a la lógica secuencial]() -->


# Instalación de Icarus-Verilog

Icarus-Verilog es un compilador *open source* para Verilog HDL.

Actualice la lista de paquetes de Linux, luego instale Icarus Verilog como se muestra:

```
sudo apt update
```

```
sudo apt install iverilog
```

Para comprobar la instalación basta con ejecutar el siguiente comando para verificar la versión instalada:

```
iverilog -v
```


# Instalación de GTKWave

GTKWave es un visor de formas de onda que funciona con Icarus Verilog para mostrar los resultados de la simulación. Está convenientemente disponible en la lista de paquetes apt de Ubuntu, por lo tanto es posible usar el comando ```apt install``` de nuevo:


```
sudo apt install gtkwave
```

Para verificar la instalación basta con ejecutar el comando ```gtkwave``` en la terminal y deberá ejecutarse el programa.
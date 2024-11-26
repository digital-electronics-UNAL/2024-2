# Ejemplos sencillos de descripciones en HDL


## Ejemplo de implementación *on-off* simple
<p align="center">
<img src="/pics/lab02/on_off.png" alt="alt text" width=800 >
</p>

Código:

```
module on_off (
    input sw,
    output led
  );

  assign led = sw;

endmodule

```

## Ejemplo de implementación puerta NOT
<p align="center">
<img src="/pics/lab02/not_gate.png" alt="alt text" width=800 >
</p>

Código:

```
module not_gate (
    input sw,
    output led
  );

  assign led = ~sw;

endmodule
```

## Simulación para ambos ejemplos con iverilog

```
`timescale 1ps/1ps
`include "path_completo_src.v"

module testbench();

    reg sw_tb;

    wire led_tb;

    nombre_modulo uut (
        .sw(sw_tb),
        .led(led_tb)
    );


    initial begin
        sw_tb = 1'b1;
        #10;
        sw_tb = 1'b0;
    end

    initial begin: TEST_CASE
        $dumpfile("testbench.vcd");
        $dumpvars(-1, uut);
        #20 $finish; 
    end

endmodule
```

donde:

1. ```nombre_modulo``` debe ser reemplazado por el nombre del módulo a simular, por ejemplo ```on_off``` o ```not gate```.

2. ```path_completo_src.v``` debe ser reemplazado por el nombre del *script* con extensión ```.v``` donde se encuentra la descripción HDL del módulo a simular.


# Descripción del diseño

Este proyecto implementa un registro de desplazamiento de 8 bits utilizando 8 Flip-Flops DSR conectados en serie. La salida Q de cada Flip-Flop se conecta a la entrada D del siguiente, y todos comparten la misma señal de reloj.

El circuito recibe los bits de forma secuencial mediante la entrada `in_INPUT`. En cada pulso de reloj, el nuevo bit se almacena y los bits anteriores se desplazan al siguiente Flip-Flop.

Las 8 salidas del registro se conectan a un circuito comparador realizado con compuertas AND y NOT. El número elegido para detectar es **173**, que corresponde a **10101101 en binario**.

Cuando el registro contiene exactamente `10101101`, la salida `out_OUT` toma el valor lógico 1. Para cualquier otra combinación, la salida permanece en 0.

## Cómo testear el diseño

1. Iniciar la simulación en Wokwi.
2. Aplicar un RESET para inicializar los Flip-Flops en 0.
3. Ingresar mediante `in_INPUT` la secuencia de bits: `1 0 1 0 1 1 0 1`.
4. Después de seleccionar cada bit, generar un pulso de reloj.
5. Al completar los 8 pulsos, el registro debe contener `10101101`.
6. En ese momento, `out_OUT` debe cambiar a 1.
7. Si se ingresa cualquier otra secuencia, `out_OUT` debe permanecer en 0.

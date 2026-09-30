# Descripción del diseño

Este proyecto implementa un registro de desplazamiento de 8 bits utilizando 8 Flip-Flops DSR conectados en serie. La salida Q de cada Flip-Flop se conecta a la entrada D del siguiente, y todos comparten la misma señal de reloj.

El circuito recibe los bits de forma secuencial mediante la entrada `in_INPUT`, conectada al interruptor rojo 1. En cada pulso de reloj, el nuevo bit se almacena en el primer Flip-Flop (`flop9`, a la izquierda) y los bits anteriores se desplazan hacia la derecha.

Las 8 salidas del registro se conectan a un comparador realizado con compuertas AND y NOT. El número elegido para detectar es **173**, que corresponde a **10101101 en binario**, leído de izquierda a derecha en el esquema, desde `flop9` hasta `flop7`.

Cuando las salidas muestran exactamente ese patrón, la salida `out_OUT` toma el valor lógico 1 y se enciende el LED. Para cualquier otra combinación almacenada, la salida es 0.

## Cómo testear el diseño

1. Iniciar la simulación en Wokwi y colocar el selector del reloj en modo MANUAL, hacia la derecha.
2. Pulsar y soltar RESET para inicializar los Flip-Flops en 0.
3. Usar únicamente el interruptor rojo 1 para ingresar la secuencia **`1 0 1 1 0 1 0 1`**, en ese orden. ON corresponde a 1 y OFF a 0.
4. Después de seleccionar cada bit, pulsar y soltar Step una vez. Para los dos unos consecutivos, mantener el interruptor en ON y realizar dos pulsos separados.
5. Al completar los 8 pulsos, las salidas del registro deben mostrar **`10101101` de izquierda a derecha**.
6. Verificar que `out_OUT` sea 1 y que el LED esté encendido.
7. Repetir la prueba desde RESET cambiando al menos uno de los ocho bits de la secuencia. Al completar los 8 pulsos, `out_OUT` debe ser 0 y el LED debe estar apagado.

**Importante:** el orden de ingreso es inverso al orden de lectura del registro. El primer bit ingresado termina en el Flip-Flop de la derecha (`flop7`), y el último queda en el de la izquierda (`flop9`). Por eso se ingresa `10110101` para obtener `10101101` en el registro. No se deben configurar los ocho interruptores simultáneamente: los bits se cargan uno por uno mediante el interruptor rojo 1.

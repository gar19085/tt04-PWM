## Descripción General
El código Verilog proporcionado es para un generador simple de PWM (Modulación por Ancho de Pulso) con un ciclo de trabajo variable. 
El ciclo de trabajo se controla mediante dos botones: uno para aumentar y otro para disminuir el ciclo de trabajo. El código también incluye lógica para el anti-rebote de los botones.
    
### Señales de Botones
`increase_duty` y `decrease_duty` son señales que están directamente conectadas a `ui_in[0]` y `ui_in[1]`, respectivamente.
    
### Lógica de Anti-rebote
El código incluye lógica para el anti-rebote de los botones. Utiliza un contador (`counter_debounce`) para generar una señal de habilitación de reloj lento (`slow_clk_enable`). 
Este reloj lento se utiliza para muestrear los estados de los botones y eliminar el rebote.
    
### Lógica de PWM
El código utiliza un contador de 4 bits (`counter_PWM`) para generar una señal PWM. El ciclo de trabajo de la señal PWM está controlado por la variable `DUTY_CYCLE`, 
que puede incrementarse o decrementarse mediante las señales de botones anti-rebote (`duty_inc` y `duty_dec`).

### Módulo DFF_PWM
Este es un simple flip-flop D utilizado para el anti-rebote. Muestrea la entrada `D` cuando la señal de habilitación `en` está en alto.

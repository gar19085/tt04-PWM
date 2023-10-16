![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/wokwi_test/badge.svg)
## General Description
This project focuses on creating a Pulse Width Modulation (PWM) generator using the Verilog hardware description language. 
The main feature of this generator is the ability to vary the duty cycle of the PWM signal, and this adjustment is achieved 
through two buttons: one to increase and one to decrease the duty cycle. The project is designed to operate with a 10 MHz 
clock as its time base.

### Debounce Logic
Debounce logic is used to eliminate the undesired effects of button presses or releases. This is achieved through a counter 
called `counter_debounce`, which generates a slow clock enable signal (`slow_clk_enable`). The slow clock is used to sample 
the states of the buttons and remove any bouncing, which refers to temporary fluctuations in the button's state when pressed 
or released. This ensures that the PWM generator responds only to stable state changes and not transient fluctuations.

### PWM Logic
The PWM generator in this project is based on a 4-bit counter named `counter_PWM`. This counter is used to generate the PWM 
signal, and its duty cycle is controlled by a variable called `DUTY_CYCLE`. This variable can be increased or decreased using 
signals generated by the debounce logic, named `duty_inc` (to increase the duty cycle) and `duty_dec` (to decrease the duty cycle).

## How to Use
To use this variable duty cycle PWM generator project, follow these steps:

### Button Connections:

You should physically connect two buttons to the system. These buttons are used to control the duty cycle of the PWM signal. 

- Connect input pin 0 to one of the buttons. This button is used to increase the duty cycle of the PWM signal. Make sure the button 
has a pull-down resistor connected to ensure a defined logical level when not pressed.
- Connect input pin 1 to the other button. This button is used to decrease the duty cycle of the PWM signal. Just like the first button,
ensure that this one also has a pull-down resistor connected.

### Oscilloscope Connection:

Connect an oscilloscope to output pin 0 of the dedicated outputs of the system. This oscilloscope will allow you to visualize 
the generated PWM signal and observe how the duty cycle changes in response to button actions. Adjust the oscilloscope settings 
to measure and display the PWM signal correctly. This includes configuring the time scale and amplitude appropriately on the 
oscilloscope so that you can observe changes in the duty cycle.

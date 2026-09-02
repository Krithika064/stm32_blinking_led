# stm32_blinking_led
Design and Implementation of an Automatic Sensor-Based LED Control System Using STM32
1. Aim

To interface a digital sensor with an STM32 microcontroller and automatically control an LED according to the sensor output.

2. Objective
To configure PA0 as a digital input.
To configure PA5 as a digital output.
To read the sensor continuously.
To turn the LED ON or OFF according to the sensor output.
3. Hardware Required
S. No.	Component	Quantity
1	STM32 development board	1
2	Digital sensor or push button	1
3	LED	1
4	220–330 Ω resistor	1
5	Breadboard	1
6	Jumper wires	As required

If the STM32 board has an onboard LED connected to PA5, an external LED is not required.

4. Pin Configuration
STM32 pin	Configuration	Connected device	Function
PA0	GPIO input	Sensor output	Reads the sensor state
PA5	GPIO output	LED	Controls the LED
3.3 V	Power supply	Sensor VCC	Powers the sensor
GND	Ground	Sensor GND	Provides common ground
5. Connection Details
Digital sensor connections
Sensor pin	STM32 connection
VCC	3.3 V
GND	GND
OUT	PA0
External LED connection
Connect PA5 to the LED anode through a 220–330 Ω resistor.
Connect the LED cathode to GND.
If the onboard LED is connected to PA5, an external LED is unnecessary.
6. Block Diagram
7. Working Principle

The digital sensor is connected to PA0 of the STM32 microcontroller. The LED is connected to PA5.

The STM32 continuously monitors the sensor output:

When the sensor output is HIGH, PA0 receives a logic HIGH signal. The STM32 makes PA5 HIGH, causing the LED to turn ON.
When the sensor output is LOW, PA0 receives a logic LOW signal. The STM32 makes PA5 LOW, causing the LED to turn OFF.
The sensor condition is checked every 100 milliseconds.
8. Algorithm
Start the system.
Initialize the STM32 microcontroller.
Configure PA0 as a digital input.
Configure PA5 as a digital output.
Read the sensor state from PA0.
Check whether the sensor output is HIGH.
If the sensor output is HIGH, switch ON the LED.
Otherwise, switch OFF the LED.
Wait for 100 milliseconds.
Repeat the sensor-reading process continuously.
9. Flowchart
10. GPIO Configuration
PA0 sensor input

PA0 is configured in GPIO input mode. It receives the digital output produced by the sensor.

PA5 LED output

PA5 is configured in push-pull output mode. It supplies the output signal required to control the LED.

11. Expected Output
Sensor output	LED output	LED condition
LOW	LOW	OFF
HIGH	HIGH	ON
12. Important Correction

In the original program, the sensor-reading and LED-control operations were placed inside the error-handling function.

The error-handling function executes only when an initialization error occurs. Therefore, the sensor-reading and LED-control operations must be placed inside the main infinite loop.

The error handler should only stop the program safely when a clock, GPIO, UART, or peripheral initialization error occurs.

13. Applications
Automatic street-light control
Obstacle-detection systems
Water-level indication
Automatic parking systems
Security and alarm systems
Industrial monitoring systems
Motion-activated lighting
14. Precautions
Use a sensor with a 3.3 V-compatible output.
Connect the sensor ground and STM32 ground together.
Use a current-limiting resistor with an external LED.
Verify the sensor pin configuration before connecting it.
Avoid applying 5 V directly to an STM32 GPIO pin.
Use a pull-up or pull-down resistor if the sensor input is unstable.
Check whether the sensor uses active-HIGH or active-LOW operation.
15. Result

The digital sensor was successfully interfaced with the STM32 microcontroller. The LED connected to PA5 turned ON when the sensor input at PA0 was HIGH and turned OFF when the sensor input was LOW.

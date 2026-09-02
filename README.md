# Automatic Sensor-Based LED Control System Using STM32

## Aim

To interface a digital sensor with an STM32 microcontroller and automatically control an LED according to the sensor output.

## Apparatus Required

| S. No. | Component | Quantity |
|---:|---|---:|
| 1 | STM32 development board | 1 |
| 2 | Digital sensor or push button | 1 |
| 3 | LED | 1 |
| 4 | 220–330 Ω resistor | 1 |
| 5 | Breadboard | 1 |
| 6 | Jumper wires | As required |
| 7 | USB cable | 1 |

## Algorithm

1. Start the system.
2. Initialize the STM32 microcontroller.
3. Configure `PA0` as a GPIO input.
4. Configure `PA5` as a GPIO output.
5. Read the sensor state from `PA0`.
6. Check whether the sensor output is HIGH.
7. If the sensor output is HIGH, set `PA5` HIGH to switch ON the LED.
8. Otherwise, set `PA5` LOW to switch OFF the LED.
9. Wait for 100 milliseconds.
10. Repeat the process continuously.

## Program

```c
#include "main.h"

int main(void)
{
    /* Initialize the HAL library */
    HAL_Init();

    /* Configure the system clock */
    SystemClock_Config();

    /* Initialize the GPIO pins */
    MX_GPIO_Init();

    while (1)
    {
        /* Read the digital sensor connected to PA0 */
        if (HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_0) == GPIO_PIN_SET)
        {
            /* Sensor is HIGH: turn ON the LED */
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        }
        else
        {
            /* Sensor is LOW: turn OFF the LED */
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        }

        /* Check the sensor every 100 milliseconds */
        HAL_Delay(100);
    }
}
```

## Result

The digital sensor was successfully interfaced with the STM32 microcontroller. The LED connected to `PA5` turned ON when the sensor input at `PA0` was HIGH and turned OFF when the sensor input was LOW.

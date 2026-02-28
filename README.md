# DC-motor-7-seg-display

Embedded program for controlling a DC motor and seven-segment display using STM32F103R6 microcontroller (Cortex-M3).

## Hardware

- **Microcontroller**: STM32F103R6 (LQFP64 package)
- **Core**: ARM Cortex-M3
- **Clock**: 8 MHz HSI internal oscillator

## Features

### DC Motor Control
- PWM control via TIM1 Channel 1 (PA8)
- PWM frequency: ~100 Hz (Prescaler: 999, Period: 80)
- Duty cycle: 50%

### Frequency Measurement
- External signal input captured via TIM3 (PA6, PA7)
- Input capture on both rising and falling edges
- Measures frequency from external signal generator (0-100 Hz range)

### Seven-Segment Display
- Common anode 7-segment display
- Segments connected to PC0-PC7
- Displays measured frequency value (0-9)

## Pin Configuration

| Pin | Function |
|-----|----------|
| PA6 | TIM3_CH1 (Input Capture 1) |
| PA7 | TIM3_CH2 (Input Capture 2) |
| PA8 | TIM1_CH1 (PWM Output - Motor) |
| PB0 | GPIO Output (Motor direction) |
| PB1 | GPIO Output (Motor enable) |
| PB2 | External Interrupt (EXTI2) |
| PB3 | GPIO Output |
| PC0-PC7 | 7-Segment Display (Segments A-G, DP) |
| PC8-PC11 | GPIO Outputs |

## Project Structure

```
DC-motor-7-seg-display/
└── cubemx/
    └── code/
        ├── Core/
        │   ├── Inc/        # Header files
        │   └── Src/        # Source files
        ├── Drivers/
        │   ├── CMSIS/      # ARM Cortex-M definitions
        │   └── STM32F1xx_HAL_Driver/
        ├── code.ioc       # STM32CubeMX configuration
        └── Makefile       # Build configuration
```

## Build

Uses Makefile-based build with ARM GCC toolchain:

```bash
cd cubemx/code
make
```

## Author

Created: January 2022

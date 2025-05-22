# ADC Potentiometer Control

This project demonstrates the use of the Analog-to-Digital Converter (ADC) on the STM32L4 Nucleo board to read an analog voltage from a potentiometer and adjust LED brightness accordingly using Pulse Width Modulation (PWM).

## Features

- ADC setup on PA1 (ADC Channel 6)
- Measurement of analog voltage (0–3.3V) from a potentiometer
- Real-time LED brightness control based on measured voltage
- Single-conversion ADC trigger mode (software-triggered)
- ADC monitoring via Logic Analyzer in Keil Debugger

## Hardware Requirements

- STM32L4 Nucleo Board  
- Breadboard & jumper wires  
- 1 kΩ Potentiometer  
- USB cable for STM32 power/debug  
- PC with Keil + Termite (optional for UART)  

## Circuit Setup

| Component     | Connection         |
|---------------|--------------------|
| Potentiometer | VCC, GND, Wiper → PA1 (analog input) |
| LED           | Onboard green LED (GPIO controlled) |

## Configuration Summary

- ADC Input Pin: PA1 (Channel 6)
- Resolution: 12-bit (0–4095)
- Clock: HCLK/1 (8 MHz MSI)
- Sampling Time: 24.5 ADC cycles
- Trigger Mode: Software, single conversion
- PWM Output: Adjusted based on ADC voltage

## Behavior

- When potentiometer = 0V, LED is off
- When potentiometer = 3.3V, LED is full brightness
- Intermediate voltages result in proportionally dimmed LED

## Logic Analyzer Monitoring

1. Use Keil uVision’s Logic Analyzer to monitor the `adc_value` variable.
2. Enable Trace, use Core Clock (e.g., 8 MHz MSI), set timestamp prescaler = 64.
3. Add `adc_value` to Logic Analyzer with range 0–4096.
4. Observe how it changes as the potentiometer is rotated.

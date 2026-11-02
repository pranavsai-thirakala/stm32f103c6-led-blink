# STM32F103C6 LED Blink (Bare-Metal)

Register-level LED blink program for the STM32F103C6, written without HAL
or any library, to understand bare-metal code structure.

## Hardware
- STM32F103C6 [Blue Pill / your board name]
- LED connected to pin [PXx] with [resistor value] resistor
- Programmer: [ST-Link / USB-UART]

## Software
- IDE: [Keil uVision / STM32CubeIDE]
- Language: Embedded C

## How it works
1. Enable the GPIO port clock through the RCC register
2. Configure the pin as output through the CRL/CRH register
3. Toggle the pin in a loop with a delay

## Folder structure
- src/ :
- docs/ : 
<img width="1366" height="768" alt="Proteus Simulation" src="https://github.com/user-attachments/assets/bc717e2b-b725-433c-bfaa-9394de78bf59" />


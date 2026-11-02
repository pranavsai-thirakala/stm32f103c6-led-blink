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
- src/ : #include <stdint.h>
#include"stm32f10x.h"
/*
#define GPIOA_BASE 0x40010800
#define RCC_BASE   0x40021000
*/



/* ================= RCC ================= 

typedef struct
{
    volatile uint32_t RCC_CR;        // 0x00
    volatile uint32_t RCC_CFGR;      // 0x04
    volatile uint32_t RCC_CIR;       // 0x08
    volatile uint32_t RCC_APB2RSTR;  // 0x0C
    volatile uint32_t RCC_APB1RSTR;  // 0x10
    volatile uint32_t RCC_AHBENR;    // 0x14
    volatile uint32_t RCC_APB2ENR;   // 0x18
    volatile uint32_t RCC_APB1ENR;   // 0x1C
    volatile uint32_t RCC_BDCR;      // 0x20
    volatile uint32_t RCC_CSR;       // 0x24
    volatile uint32_t RCC_AHBSTR;    // 0x28
    volatile uint32_t RCC_CFGR2;     // 0x2C
} RCC_Def;

#define RCC ((RCC_Def *)RCC_BASE)



typedef struct
{
    volatile uint32_t CRL;   // 0x00
    volatile uint32_t CRH;   // 0x04
    volatile uint32_t IDR;   // 0x08
    volatile uint32_t ODR;   // 0x0C
    volatile uint32_t BSRR;  // 0x10
    volatile uint32_t BRR;   // 0x14
    volatile uint32_t LCKR;  // 0x18
} GPIO_Def;

#define GPIOA ((GPIO_Def *)GPIOA_BASE)


*/

void delay(uint16_t t)
{
    volatile uint32_t i;

    for(uint16_t j = 0; j < t; j++)
    {
        for(i = 0; i < 6000; i++)
        {
        }
    }
}
int main(void){
RCC->APB2ENR |= (1 << 2);
    GPIOA->CRL &= ~(0xF << 8);
    GPIOA->CRL |=  (0x3 << 8);
    while(1)
    {
        GPIOA->BSRR = (1 << 2);

        delay(100);

        
        GPIOA->BRR = (1 << 2);

        delay(100);
    }
}
- docs/ : 
<img width="1366" height="768" alt="Proteus Simulation" src="https://github.com/user-attachments/assets/bc717e2b-b725-433c-bfaa-9394de78bf59" />


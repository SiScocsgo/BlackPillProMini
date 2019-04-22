# Documentation for the Blackpill Pro Mini

## 1) Introduction
The Blackpill Pro Mini is a 13x7 pinhole sized STM32 LQFP48 breakout board. It can support many classes of STM32 MCUs, such as L,F0,F1,and F3. The default version is equipped with an STM32F103C8T6.

### Main Features
* ARM® 32-bit Cortex®-M3 CPU Core
* 72Mhz clockspeed
* 64kB of flash memory
* 3.3v logic
* 5v tolerant pins

### 1.2) Configurable IO
* 30 IO Pins
* 12 PWM Pins
* 16 Analog Inputs
* 4 GND Pins
* 4 VCC Pins
* 5-15v VIN

### 1.3) Interfaces
* 2 Hardware USARTs
* 2 SPI
* USB 2.0
* 2 IIC
* CAN Bus

## 2) Hardware Description
The hardware on the circuit board are packed very tightly together, as the board surface area is rather small. The STM32F103C8T6 offers so many pins, that some of them had to be placed onto pads on the bottom side of the circuit board. Instead of using pins wit jumper links, the Boot0 and Boot1 signals are accessible on jumper pads. The Boot0 and Boot1 signals are always pulled low with 10k Ohm resistors, which means that when the pads are connected, the Boot0 and Boot1 signals are forced highThe STM32 line of MCUs runs at 3.3v, which means that the whole board can be run directly from a single cell lithium battery. The default version of the Blackpill does not come with a low power oscillator and its load capacitors, but does come with pads for one on the bottom of the pcb. All of the components are placed on the top side of the board, so that the bottom of the board

## 3) Programming Guide
### 3.1) Beginners
#### 3.1.1) Software
For simple programming of the default hardware, the stm32duino plugin for the Arduino IDE can be used.  
In order to get this running you will first need to install the Arduino IDE, which can be found [Here](https://www.arduino.cc/en/Main/Software#download)
#### 3.1.2) Hardware
   Regardless of the bootloader on your Blackpill Pro Mini, you can always program it via the SWD port using an STLink V2. This is likely how you will program your Blackpill for the first time. From here you can install different bootloaders, such as the Maple Serial Driver, which lets you program the Blackpill via the USB port. A tutorial for this installation process can be found [Here](https://circuitdigest.com/microcontroller-projects/programming-stm32f103c8-board-using-usb-port)

### 3.2) Advanced
#### 3.2.1) Software
   For proper development purposes, a text editor should be used alongside a compiler, which also requires the use of STM32CubeMX. 
   This is also the case for development for non F103 cpu equipped Blackpills.
   A great tutorial for setting up VSCode with the compiler by hbfsrobotics can be found here: [hbfsrobotics.com](http://hbfsrobotics.com/blog/configuring-vs-code-arm-development-stm32cubemx)
#### 3.2.2) Hardware
   Regardless of the bootloader on your Blackpill Pro Mini, you can always program it via the SWD port using an STLink V2. This is likely how you will program your Blackpill for the first time. Depending on your use case, you are able to implement reprogramming of it in many different ways. The most common methods of reprogramming are SWD, Serial, and USB.
   The Maple Serial Driver, lets you program the Blackpill via the USB port. A tutorial for this installation process can be found [Here](https://circuitdigest.com/microcontroller-projects/programming-stm32f103c8-board-using-usb-port)

## 4) Hardware Modifications
The Blackpill Pro Mini was built to be modified for special use cases.
### 4.1) Low power
⋅⋅⋅teaw6yduas

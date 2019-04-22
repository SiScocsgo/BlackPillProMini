# Documentation for the Blackpill Pro Mini

## 1) Introduction
The Blackpill Pro Mini is a 13x7 pinhole sized STM32 LQFP48 breakout board. It can support many classes of STM32 MCUs, such as L,F0,F1,and F3. The default version is equipped with an STM32F103C8T6.

### 1.1) Configurable IO
#### 30 IO Pins
#### 12 PWM Pins
#### 16 Analog Inputs
#### 4 GND Pins
#### 4 VCC Pins
#### 5-15v VIN

### 1.2) Interfaces
#### 2 Hardware USARTs
#### 2 SPI
#### USB 2.0
#### 2 IIC
#### CAN Bus


## 2) Hardware Specification
The hardware on the circuit board are packed very tightly together, as the board surface area is rather small. The default version of the Blackpill does not come with a low power oscillator and its load capacitors, but does come with pads for one on the bottom of the pcb. All of the components are placed on the top side of the board, so that the bottom of the board

## 3) Programming Guide
### 3.1) Beginners
For simple programming of the default hardware, the stm32duino plugin for the Arduino IDE can be used.


### 3.2) Advanced
For proper development purposes, a text editor should be used alongside a compiler, which also requires the use of STM32CubeMX. 
This is also the case for development for non F103 cpu equipped Blackpills.
A great tutorial for setting up VSCode with the compiler by hbfsrobotics can be found here:
[hbfsrobotics.com](http://hbfsrobotics.com/blog/configuring-vs-code-arm-development-stm32cubemx)

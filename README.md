# CAN-Based Automotive Dashboard System

## Overview

Developed a CAN-Based Automotive Dashboard System using PIC18F4580 microcontrollers to enable real-time communication between Electronic Control Units (ECUs). The system transmits and displays vehicle parameters such as speed, RPM, gear position, and indicator status over a CAN network.

## Features

* Real-time CAN communication between multiple ECUs
* Vehicle speed monitoring
* Engine RPM monitoring
* Gear position display
* Indicator status monitoring
* CLCD-based dashboard display
* Digital keypad interface
* ADC-based sensor data acquisition
* Event-driven embedded application design

## Hardware Used

* PIC18F4580 Microcontroller
* CLCD Display
* Digital Keypad
* CAN Transceiver
* Potentiometer (Sensor Simulation)
* LEDs and Switches

## Software Used

* Embedded C
* MPLAB X IDE
* XC8 Compiler

## Communication Protocols

* CAN Protocol
* UART
* ADC Interface

## Project Structure

### Model_1

Sensor ECU responsible for acquiring vehicle parameters and transmitting CAN messages.

### Model_2

Dashboard ECU responsible for receiving CAN messages and displaying vehicle information.

### Model_3

Additional ECU for event handling, monitoring, or extended dashboard functionality.

## Skills Demonstrated

* Embedded C Programming
* CAN Protocol Implementation
* PIC18F4580 Microcontroller Programming
* Interrupt Handling
* ADC Interface
* CLCD Interfacing
* Embedded System Design
* Real-Time Data Processing

## Author

Abinand V Nair

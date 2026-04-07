Automatic Rain Detection and Wiper Control System
An autonomous hardware solution that detects rainfall and manages wiper speed through discrete electronic components. This project replaces microcontroller-based logic with a custom-designed circuit using Shift Registers, Multiplexers, and Op-Amp based ADCs.

Overview
The system accurately identifies rainfall via a resistive raindrops module and triggers a mechanical 180-degree wiper sweep. It features a manual/automatic speed control interface with 4 discrete levels, visualized through an LED bar graph and driven by hardware-generated Pulse Width Modulation (PWM).

Hardware Architecture
1. Rain Sensing & ADC (Mixed-Signal Layer)
Sensor: Resistive Raindrops Module (MH-RD).

ADC Design: Instead of an integrated chip, a custom Analog-to-Digital Converter was designed using uA741 Op-Amp ICs acting as comparators.

Function: Converts the analog voltage from the rain sensor into a digital signal to enable/disable the system based on precipitation intensity.

2. PWM Generation (Control Layer)
To control the wiper speed, the system generates four distinct PWM duty cycles without a microprocessor:

Shift Register (SN7495AN): Acts as the sequential timing core to manage signal cycles.

Multiplexer (DM74153N): Selects between the four duty cycles based on the user-defined encoder input or rain intensity.

Visual Interface: A 4-LED array indicates the current speed level (Frequency/Duty Cycle).

3. Mechanical Actuation (Execution Layer)
Drive System: A DC motor coupled with a mechanical linkage system (as seen in the project photos) to convert continuous rotation into a 180-degree oscillatory "sweep" motion.

Chassis: Mounted on a custom acrylic/PVC board featuring a gear-reduction assembly for high-torque wiping.

System Design
Logic & Schematics
The system logic (sketched below) utilizes a clock-driven architecture where bit-patterns (e.g., 1010, 1100) are multiplexed to create variable PWM widths.

Logic High (1): Constant speed.

Logic 0/1 toggles: Variable speeds controlled by the MUX (S1, S0 pins).

Components Used
Integrated Circuits: DM74153N (Dual 4-Input MUX), SN7495AN (4-Bit Shift Register), uA741 (Operational Amplifiers).

Sensors: Raindrops Module (Resistive sensor plate + Comparator).

Passive Components: Resistor ladder for current limiting and voltage division, Potentiometer for sensitivity adjustment.

Mechanical: DC Motor, 9V Battery, Linkage Arm, Gears.

How to Run
Connect a 9V DC Power Supply to the breadboard rails.

Calibrate the ADC Threshold using the Op-Amp potentiometer to define what constitutes "light" vs "heavy" rain.

Observe the LED indicators:

1 LED: Low speed / Light rain.

4 LEDs: Maximum speed / Heavy rain.

The wiper arm will automatically begin its 180-degree sweep upon sensor activation.

🎓 Project Context
Developed as a part of the Kriti 2025 competition at IIT Guwahati. This project demonstrates the ability to implement complex control systems using Discrete Digital ICs, moving away from standard Arduino/ESP32 implementations to understand the fundamental logic of PWM and ADC architectures.

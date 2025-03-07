# Microprocessors Lab  - ATMega328PB IoT Project

This repository contains the work done throughout a university course focused on embedded systems, programming languages (Assembly and C), and microcontroller programming with the ATMega328PB. The course involved completing 8 laboratory exercises, each with specific goals that built upon the previous ones. The final project, Lab 8, integrated all the concepts learned throughout the course to build a networked IoT system.

## Technologies Used:
- **Programming Languages**: Assembly, C
- **Microcontroller**: ATMega328PB
- **IDE**: MPLAB X IDE

## Labs Overview

### Lab 1: Basic Assembly Programming and Time Delays
- Implemented assembly code to create accurate time delays using `rcall` and register pairs.
- Calculated logical functions in a loop with variable increments.
- Simulated a moving cart in assembly using `PORTD` bits, with direction control and stops for 1 second when changing direction.
- Utilized MPLAB X IDE for simulation and testing, including time measurement using the Stopwatch tool.

### Lab 2: External Interrupts and Button Debouncing
- Handled external interrupts (INT0, INT1) in Assembly.
- Implemented button press detection and debounce handling.
- Created a counter implementation with an LED display and time delays.
- Controlled LEDs based on button inputs.
- Automated a light control system using timing mechanisms.
- Developed code in both Assembly and C for flexibility and optimization.

### Lab 3: Lighting Automation and PWM Control
- Used interrupts (INT1, PC5) and Timer1 to control a light that stays on for 4 seconds and resets if triggered again.
- Generated a PWM signal on PB1 to control brightness in 8% steps, based on button presses.
- Controlled PWM frequency (125Hz–1kHz) using Fast PWM mode on Timer1, adjusting frequency via button inputs.

### Lab 4: ADC Handling and CO Gas Detection
- Implemented ADC conversion using both interrupt-driven and polling methods and displayed voltage on an LCD.
- Monitored CO gas levels via an ADC input, updated LEDs, and displayed warnings on an LCD when levels exceeded 70ppm.
- Generated a 5kHz PWM signal on PB1 with duty cycle adjustments (20%-80%) based on button inputs.
- Displayed duty cycle and filtered output voltage on an LCD.

### Lab 5: Logical Functions, I/O Expansion, and Display
- Implemented and displayed logical functions (F0 and F1) based on inputs.
- Lighted up LEDs based on specific button presses.
- Controlled LEDs via an I/O expander (PCA9555) using button inputs.
- Optionally displayed the student's name and surname on an LCD screen.

### Lab 6: Keypad Scanning and Electronic Lock
- Scanned a keypad to detect pressed keys using multiple functions for row checking, keypad scanning, and handling debouncing.
- Mapped pressed keys to corresponding ASCII characters and displayed them on an LCD.
- Simulated an electronic lock that lights up LEDs when the correct 2-digit team number was entered via the keypad.
- Incorporated error handling with LEDs blinking to signal an incorrect team number.
- Implemented debouncing to handle key presses accurately.

### Lab 7: Temperature Sensing and Communication
- Communicated with the DS1820 temperature sensor using the one-wire protocol.
- Triggered temperature measurements, waited for completion, and retrieved temperature data as a 16-bit value with 0.5°C precision.
- Handled error detection by returning a value (0x8000) when no sensor device was found.
- Displayed the measured temperature on an LCD, with precision to three decimal places, in the range of -55°C to +125°C. Displayed "NO Device" if no sensor was detected.

### Lab 8: IoT System Integration (Final Project)
#### ESP8266 Network Connection:
- Wrote code for the ATMega328 to send commands via UART to connect the ESP8266 to a network.
- Read and checked the response from the ESP8266. Displayed "1. Success" on the LCD if successful, otherwise displayed "1. Fail."

#### Set URL Command:
- Sent an HTTP URL command via UART to set the URL to `http://<server_ip>:<port>/data`.
- Displayed "2. Success" if successful, otherwise displayed "2. Fail."

#### Sensor Data Integration:
- **Temperature Sensor (DS18B20)**: Simulated a patient’s temperature (around 36°C) and read temperature data from the DS18B20 sensor.
- **Pressure Sensor (POT0)**: Read data from the POT0 and converted it into a range of 0-20 cm H2O to simulate central venous pressure.

#### Status Logic:
- **NURSE CALL Status**: If the last digit of the team number was pressed, the status was set to "NURSE CALL." Pressing "#" would set the status to "OK," unless there was a temperature or pressure issue.
  - If the pressure was outside the range of 4-12 cm H2O, the status would be set to "CHECK PRESSURE."
  - If the temperature was outside the range of 34°C–37°C, the status would be set to "CHECK TEMP."
  - If the conditions were normal, the status would be set to "OK."

#### Payload Integration:
- Integrated the final status and sensor values (temperature and pressure) into a payload for transmission via the ESP8266 to the server.

## Conclusion

The project integrates various embedded system concepts such as assembly programming, peripheral handling, sensor communication, and IoT connectivity. It provided hands-on experience in both hardware and software aspects of embedded systems design. The final lab, Lab 8, brought together all the knowledge from the previous labs into a fully functional IoT solution, connecting embedded systems with real-time sensor data and network communication.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

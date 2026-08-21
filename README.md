# Smart Room Status Display for Meetings

**By**
1. Adebimpe Saheed Olawale
2. Claudia Asare
3. Amara Chinecherem Metu

We are student from ASHESI UNIVERSITY, GHANA and ETH ZURICH.


## Introduction:
This project is a smart meeting room status display. Its main aim is to manage meeting room status for convenience and privacy, and most importantly, to replace the traditional "Meeting in Progress" paper door display. The system is designed with simplicity in mind, to encourage people to use it. This simplicity is achieved through the use of the STM32F091RC microcontroller. Its working principle is primarily based on a single button which serves as the On/Off control, and in the future, we look forward to integrating a virtual switch via Bluetooth.


## Working Principle:
A single button is used to activate the system. After pressing the button, an LED turns on to notify the user that the system is in the "ON" state, and "Meeting in Progress" is shown on the LCD display for 10 seconds. After 10 seconds, the LCD automatically turns off to conserve power, and the system enters a monitoring phase, though the LED remains on to indicate the system is still active.

During the monitoring phase, if a person approaches within a certain range of the room (approximately 50 cm), as detected by the ultrasonic sensor, the LCD turns on again and displays Meeting in Progress for another 10 seconds before returning to the monitoring state.

We have also programmed the LED to toggle rapidly whenever someone approaches the door, giving the user an idea that someone is nearby.

When the room is no longer in use, pressing the same button turns off all peripherals. While our original intention was to use two buttons to control the system, we decided to go with only one to keep things more convenient for the user.


## Component Used:

| COMPONENTS | PERIPHERAL | PORT | PIN | COMMENT |
| :--- | :--- | :--- | :--- | :--- |
| **Start & Stop Button** | GPIO | Port A (start button) <br> Port A (start button) | Pin 0 <br> Pin 9 | Only start button is used in this project. A single click will on the system and another click off it. |
| **Ultrasonic Sensor** | GPIO | Port C (Echo) <br> Port C (Trig)| Pin 9 (Echo) <br> Pin 8 | In our case, we set it as GPIO instead of using timer as an interrupt. This is our decision is based on our reasoning of how ultrasonic sensor works. Our thinking is that we can be able to measure the time that echo pin goes high and when it goes back low with HAL GetTICK without using a timer |
| **ONBOARD LED** | GPIO| Port A | Pin 5 | — |
| **LCD** | I2C | Port B (SDA) <br> Port B(SCL) | Pin 9 (SDA) <br> Pin 8(SCL) | — |
| **Bluetooth Module.** | UART | Port A (Rx) <br> Port A(Tx)| pin 10(Rx) <br> pin 9(Tx) | We are able to set up our Bluetooth and we tested it by sending a string from our laptop to the connected device. But unfortunately, we are unable to configure it as an interrupt like the way our button operates. |


## Future Improvements
One feature we hope to achieve in the future is to provide even more convenience by enabling remote control. That is why we have introduced a Bluetooth module (HC-05). This module will allow the system to be toggled remotely by mirroring the behavior of the physical On/Off button. Our goal is that pressing the button or sending the corresponding Bluetooth command will turn the system ON (used state), and pressing it again (or sending another command) will turn it OFF. Unfortunately, we are able to set and receive signal from the Bluetooth module, but we didn’t get it to interrupt irrespectively.

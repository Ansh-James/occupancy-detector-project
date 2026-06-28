# Occupancy-detector-project by Ansh Joseph James


A real-time room occupancy detection system using a **PIR (Passive Infrared) motion sensor** and an **Arduino Uno**. The system detects human presence and displays live occupancy status via Serial Monitor, an LED indicator, and optionally a buzzer or LCD display.
<img width="703" height="338" alt="image" src="https://github.com/user-attachments/assets/7b1d7134-ffc7-4c89-834f-c5e9f75deddf" />


Scope

- Detects human presence in real time using PIR motion sensor
- Displays occupancy status on the Serial Monitor
- LED indicator — ON when occupied, OFF when vacant
- Low power consumption
- Easy to set up and extend

---

## Components 

| Component            | Quantity |
|----------------------|----------|
| Arduino Uno          | 1        |
| PIR Sensor (HC-SR501)| 1        |
| LED (any color)      | 1        |
| 220Ω Resistor        | 1        |
| Breadboard           | 1        |
| Jumper Wires         | Several  |
| USB Cable (Type-B)   | 1        |







Prerequisites

- [Arduino IDE](https://www.arduino.cc/en/software) installed on your PC
- Arduino Uno board + USB cable
- All components listed above




**Working**
1. The **PIR sensor** detects infrared radiation emitted by warm bodies
2. When motion is detected, the sensor outputs a high signal to Pin 2
3. The Arduino reads this signal and:
   - Turns the LED ON
   - Prints **"OCCUPIED"** to the Serial Monitor
4. When no motion is detected for the sensor's delay period, it outputs low signal
5. The Arduino then:
   - Turns the LED OFF
   - Prints **"VACANT"** to the Serial Monitor


Future scope
- Add a **16x2 LCD** to show status without a PC
- Log occupancy data to an **SD card module**
- Send data over **WiFi** using an ESP8266 module
- Build a **web dashboard** to monitor occupancy remotely
- Integrate with **Home Assistant** or **MQTT** for smart home use





This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.


Author
Ansh James
- GitHub: https://github.com/Ansh-James

> Made with Arduino, and with the eatchings of L&T EduTech :)

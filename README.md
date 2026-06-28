# occupancy-detector-project


A real-time room occupancy detection system using a **PIR (Passive Infrared) motion sensor** and an **Arduino Uno**. The system detects human presence and displays live occupancy status via Serial Monitor, an LED indicator, and optionally a buzzer or LCD display.
<img width="703" height="338" alt="image" src="https://github.com/user-attachments/assets/7b1d7134-ffc7-4c89-834f-c5e9f75deddf" />


Scope

- Detects human presence in real time using PIR motion sensor
- Displays occupancy status on the Serial Monitor
- LED indicator — ON when occupied, OFF when vacant
- Low power consumption
- Easy to set up and extend

---

## 🛒 Components Required

| Component            | Quantity |
|----------------------|----------|
| Arduino Uno          | 1        |
| PIR Sensor (HC-SR501)| 1        |
| LED (any color)      | 1        |
| 220Ω Resistor        | 1        |
| Breadboard           | 1        |
| Jumper Wires         | Several  |
| USB Cable (Type-B)   | 1        |
| Buzzer *(optional)*  | 1        |
| 16x2 LCD *(optional)*| 1        |



## 🔌 Circuit Diagram


PIR Sensor (HC-SR501)        Arduino Uno
─────────────────────        ───────────
VCC  ──────────────────────► 5V
GND  ──────────────────────► GND
OUT  ──────────────────────► Digital Pin 2

LED
────
Anode (+) ─── 220Ω Resistor ─► Digital Pin 13
Cathode (−) ──────────────────► GND
```


```
realtime-occupancy-pir-arduino/
├── src/
│   └── occupancy_detector.ino   # Main Arduino sketch
├── circuit/
│   └── circuit_diagram.png      # Wiring diagram image
├── docs/
│   └── notes.md                 # Extra notes and references
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- [Arduino IDE](https://www.arduino.cc/en/software) installed on your PC
- Arduino Uno board + USB cable
- All components listed above

### Installation & Upload

1. **Clone this repository:**
   ```bash
   git clone https://github.com/your-username/realtime-occupancy-pir-arduino.git
   cd realtime-occupancy-pir-arduino
   ```

2. **Open the sketch:**
   - Launch Arduino IDE
   - Open `src/occupancy_detector.ino`

3. **Select your board and port:**
   - Go to **Tools → Board → Arduino Uno**
   - Go to **Tools → Port → COM# (Windows) / /dev/ttyUSB0 (Linux/Mac)**

4. **Upload the sketch:**
   - Click the **Upload** button (→ arrow icon)

5. **Open Serial Monitor:**
   - Go to **Tools → Serial Monitor**
   - Set baud rate to `9600`
   - Watch real-time occupancy status!

---

## 💻 Code Overview

```cpp
// occupancy_detector.ino

const int PIR_PIN = 2;    // PIR sensor output pin
const int LED_PIN = 13;   // LED indicator pin

void setup() {
  pinMode(PIR_PIN, INPUT);
  pinMode(LED_PIN, OUTPUT);
  Serial.begin(9600);
  Serial.println("System Ready. Waiting for motion...");
  delay(2000); // Allow PIR sensor to calibrate
}

void loop() {
  int motionDetected = digitalRead(PIR_PIN);

  if (motionDetected == HIGH) {
    digitalWrite(LED_PIN, HIGH);
    Serial.println("Status: OCCUPIED 🔴");
  } else {
    digitalWrite(LED_PIN, LOW);
    Serial.println("Status: VACANT  🟢");
  }

  delay(1000); // Check every 1 second
}
```

---

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



## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.


Author
Ansh James
- GitHub: [@your-username](https://github.com/your-username)

> Made with Arduino, and with the eatchings of L&T EduTech :)

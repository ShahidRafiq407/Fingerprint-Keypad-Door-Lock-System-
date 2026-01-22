# Fingerprint-Keypad-Door-Lock-System-
A dual-security door lock system using Arduino, Fingerprint Sensor, and 4x4 Keypad. Features include LCD status display, Buzzer alerts, and Solenoid Lock control.

# 🔐 Biometric & Keypad Security Door Lock

This project is an **Arduino-based Dual Security System** designed to control a door lock using two authentication methods:
1. **Biometric Scan:** Using an Optical Fingerprint Sensor.
2. **Passcode:** Using a 4x4 Matrix Keypad.

The system features an **I2C LCD** for real-time status updates, a **Relay** to control the electronic lock (Solenoid/Magnetic), and a **Buzzer** for unauthorized access alerts.

## 🚀 Features
* **Dual Authentication:** Unlock using Fingerprint or 4-Digit Password.
* **Active Low Relay Logic:** Compatible with standard Relay Modules.
* **Security Alerts:** Buzzer activates on wrong password or unregistered fingerprint.
* **Status Display:** 16x2 LCD shows messages like "Access Granted," "Wrong Pass," etc.
* **Non-Blocking Code:** System runs smoothly without freezing during scans.

## 🛠️ Hardware Components
* **Microcontroller:** Arduino Uno
* **Biometric Sensor:** Dy50 Fingerprint Sensor (or Adafruit compatible)
* **Input:** 4x4 Membrane Keypad
* **Display:** 16x2 LCD with I2C Module
* **Actuator:** 5V Relay Module (Controls the Solenoid Lock)
* **Alert:** 5V Buzzer
* **5V Lock Solenoid**
* **Power:** 5V Supply (for Solenoid Lock) & 5V (for Arduino)
* Jumper Wires & Breadboard

## 🔌 Pin Configuration (Wiring)

| Component | Arduino Pin | Description |
| :--- | :--- | :--- |
| **Fingerprint TX** | Pin 2 | Green Wire (SoftwareSerial RX) |
| **Fingerprint RX** | Pin 3 | White Wire (SoftwareSerial TX) |
| **Relay Module** | Pin A0 | Controls the Lock (Active Low) |
| **Buzzer** | Pin A1 | Alert Sound (Positive Leg) |
| **LCD SDA** | Pin A4 | I2C Data |
| **LCD SCL** | Pin A5 | I2C Clock |
| **Keypad Row 1** | Pin 11 | Keypad Connection |
| **Keypad Row 2** | Pin 10 | Keypad Connection |
| **Keypad Row 3** | Pin 9 | Keypad Connection |
| **Keypad Row 4** | Pin 8 | Keypad Connection |
| **Keypad Col 1** | Pin 7 | Keypad Connection |
| **Keypad Col 2** | Pin 6 | Keypad Connection |
| **Keypad Col 3** | Pin 5 | Keypad Connection |
| **Keypad Col 4** | Pin 4 | Keypad Connection |

> **Note:** Ensure the Relay and Arduino share a common Ground (GND) if using external power for the lock.

## 📚 Required Libraries
You need to install the following libraries in Arduino IDE:
1.  `Adafruit Fingerprint Sensor Library`
2.  `Keypad`
3.  `LiquidCrystal_I2C`

## ⚙️ How It Works
1.  **System Startup:** The LCD initializes, and the relay is set to HIGH (Locked state).
2.  **Input:** The system waits for either a keypad press or a finger placement.
3.  **Verification:**
    * If **Fingerprint** matches a stored ID -> Door Unlocks.
    * If **Password** (Default: `1234`) is correct -> Door Unlocks.
4.  **Action:**
    * **Success:** LCD shows "Access Granted," Relay turns LOW (Unlock) for 3 seconds, then locks again.
    * **Failure:** LCD shows "Wrong Pass/Finger," and the **Buzzer** beeps for 1 second.

## 📸 Images
<img width="1600" height="1437" alt="image" src="https://github.com/user-attachments/assets/6db2e102-3fe5-497e-8285-301735f09885" />


## 📄 License
This project is open-source and available for educational purposes.

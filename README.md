# Fingerprint-Keypad-Door-Lock-System-
A dual-security door lock system using Arduino, Fingerprint Sensor, and 4x4 Keypad. Features include LCD status display, Buzzer alerts, and Solenoid Lock control.

#  Biometric & Keypad Security Door Lock

This project is an **Arduino-based Dual Security System** designed to control a door lock using two authentication methods:
1. **Biometric Scan:** Using an Optical Fingerprint Sensor.
2. **Passcode:** Using a 4x4 Matrix Keypad.

The system features an **I2C LCD** for real-time status updates, a **Relay** to control the electronic lock (Solenoid/Magnetic), and a **Buzzer** for unauthorized access alerts.

##  Features
* **Dual Authentication:** Unlock using Fingerprint or 4-Digit Password.
* **Active Low Relay Logic:** Compatible with standard Relay Modules.
* **Security Alerts:** Buzzer activates on wrong password or unregistered fingerprint.
* **Status Display:** 16x2 LCD shows messages like "Access Granted," "Wrong Pass," etc.
* **Non-Blocking Code:** System runs smoothly without freezing during scans.

##  Hardware Components
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

## Required Libraries
You need to install the following libraries in Arduino IDE:
1.  `Adafruit Fingerprint Sensor Library`
2.  `Keypad`
3.  `LiquidCrystal_I2C`

##  How It Works
1.  **System Startup:** The LCD initializes, and the relay is set to HIGH (Locked state).
2.  **Input:** The system waits for either a keypad press or a finger placement.
3.  **Verification:**
    * If **Fingerprint** matches a stored ID -> Door Unlocks.
    * If **Password** (Default: `1234`) is correct -> Door Unlocks.
4.  **Action:**
    * **Success:** LCD shows "Access Granted," Relay turns LOW (Unlock) for 3 seconds, then locks again.
    * **Failure:** LCD shows "Wrong Pass/Finger," and the **Buzzer** beeps for 1 second.

##  Images
<img width="1600" height="1437" alt="image" src="https://github.com/user-attachments/assets/6db2e102-3fe5-497e-8285-301735f09885" />


#  Code Installation & Usage Guide

Since the Arduino Uno has limited memory, this project uses a **Two-Step Process**:
1.  **Enrollment Code:** To save fingerprints into the sensor's memory.
2.  **Main System Code:** To run the security system (Keypad + Fingerprint + LCD).

Follow these steps to set up the project code:

###  Step 1: Install Libraries
Open Arduino IDE and install the following libraries via Library Manager:
* `Adafruit Fingerprint Sensor Library`
* `Keypad`
* `LiquidCrystal_I2C`

---

###  Step 2: Enroll Fingerprints
Before using the lock, you must save your fingerprints.

1.  save the given the file **`fingerprint enrolled code`** from this repository.
2.  Upload it to your Arduino.
3.  Open the **Serial Monitor** (Tools > Serial Monitor) and set baud rate to **9600**.
4.  Follow the on-screen instructions:
    * Type an ID number (e.g., `1`) and press Enter.
    * Place your finger on the sensor when asked.
    * Remove and place it again to verify.
    * You will see **"Stored!"** upon success.
5.  Repeat this for as many fingers as you want to save.

> **Note:** Fingerprints are stored inside the sensor, so they won't be deleted when you upload the new code.

---

###  Step 3: Run the Main Security System
Once fingerprints are enrolled, upload the main lock code.

1.  Save the file **`full working lock code file`** from this repository.
2.  Upload it to your Arduino.
3.  The LCD will show **"System Starting"**.
4.  Your system is now ready!

---

###  How to Use
* **Unlock via Fingerprint:** Simply place your enrolled finger on the sensor. If matched, the door unlocks for 3 seconds.
* **Unlock via Password:** Type `1234` (Default) on the keypad and press **`#`**.
* **Clear Input:** Press **`*`** to clear typed digits.
* **Alerts:** If a wrong password or unregistered finger is detected, the **Buzzer** will beep, and the LCD will show an error.

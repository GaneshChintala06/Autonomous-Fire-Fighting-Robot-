# 🔥 ESP32 Fire-Fighting Robot

This project is a **fire-detection and extinguishing robot** built using an **ESP32** microcontroller, **L298N motor driver**, **flame sensors**, a **servo motor**, and a **water pump**.  
It can automatically detect the direction of a fire using digital flame sensors and extinguish it by spraying water using a pump controlled via a relay.

---

## 🧠 Features

- 🔥 Detects fire using **three flame sensors** (Left, Front, Right).  
- 🚗 Controls **two DC motors** via the **L298N motor driver**.  
- 💦 Activates a **water pump** to extinguish the detected fire.  
- ⚙️ Uses a **servo motor** to aim the spray nozzle toward the fire.  
- 🧭 Can be expanded with obstacle detection or autonomous navigation.

---

## ⚙️ Hardware Components

| Component | Description |
|------------|--------------|
| ESP32 | Main microcontroller board |
| L298N Motor Driver | Controls two DC motors |
| Flame Sensors (x3) | Detects the presence of fire |
| Servo Motor | Controls the direction of the spray nozzle |
| Relay Module | Controls the water pump |
| DC Motors (x2) | Enables robot movement |
| Water Pump | Sprays water to extinguish fire |
| Power Supply | 7.4V – 12V Li-ion or similar battery |

---

## 🪛 Pin Configuration

| Function | ESP32 Pin |
|-----------|------------|
| Enable A (PWM) | 2 |
| Motor Input 1 | 14 |
| Motor Input 2 | 15 |
| Motor Input 3 | 13 |
| Motor Input 4 | 12 |
| Enable B (PWM) | 4 |
| Right Flame Sensor | 16 |
| Front Flame Sensor | 0 |
| Left Flame Sensor | 3 |
| Servo Signal | 1 |
| Pump Relay | 33 |

---

## 🧩 Code Overview

### 🔹 Main Functions:
- **`servoWrite(int angle)`** — Generates PWM for servo angle control.  
- **`forward()`, `backward()`, `turnRight()`, `turnLeft()`, `Stop()`** — Motor control functions.  
- **Flame detection logic** — Reads sensors and decides direction of servo sweep and pump activation.

### 🔹 PWM Setup:
- Motor PWM frequency: `5000 Hz`, 8-bit resolution  
- Servo PWM frequency: `50 Hz`, 16-bit resolution (for precise control)

### 🔹 Behavior:
- If a **flame** is detected (sensor reads `LOW`):
  - The robot stops.
  - Activates the **pump**.
  - Sweeps the **servo** toward the flame direction.
- If **no fire** is detected:
  - The pump is off.
  - The robot stays idle or can move to search for fire (customizable).

---

## 🚀 Getting Started

### 1. **Setup Arduino IDE**
- Install **ESP32 board package** (ESP32 Core 3.x recommended).  
- Select **Board → ESP32 Dev Module**.

### 2. **Upload the Code**
- Connect your ESP32 via USB.
- Select the correct **COM port**.
- Upload the code.

### 3. **Power Up**
- Connect motors and sensors as per the pin configuration.
- Power the ESP32 and motor driver with an external battery (7.4V–12V).

---

## 📊 Output Example (Serial Monitor)


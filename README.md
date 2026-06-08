# 🚗 STM32 Automated Driving Platform with Solar Battery Support

## Overview

This project presents a **low-cost embedded automated driving platform** built around the **STM32F103C8T6 microcontroller**. The system supports **Manual**, **Assisted**, and **Autonomous** driving modes for structured indoor environments while integrating **obstacle detection**, **Bluetooth communication**, and a **solar-assisted battery charging system** for sustainable operation.

The platform demonstrates real-time sensor processing, motor control, wireless communication, and energy-efficient power management, making it suitable for educational, research, and industrial automation applications.

---

## ✨ Features

### Operating Modes

#### 📱 Manual Mode

* Bluetooth-controlled navigation through a smartphone application.
* Direct user control over movement and speed.

#### 🛡️ Assisted Mode

* Driver-controlled navigation with sensor-based safety assistance.
* Obstacle detection alerts and intervention support.

#### 🤖 Autonomous Mode

* Fully autonomous movement.
* Real-time obstacle avoidance using ultrasonic and infrared sensors.
* Automatic navigation decisions based on environmental conditions.

---

## 🔧 Key Capabilities

* Real-time obstacle detection using **HC-SR04 Ultrasonic Sensor**
* Side obstacle detection using **Infrared Sensors**
* PWM-based motor speed control
* Wireless Bluetooth communication using **HC-05**
* Solar-assisted battery charging system
* Battery voltage monitoring
* Audio feedback through buzzer melodies
* Visual indicators using LEDs
* Autonomous obstacle avoidance algorithm

---

## 📡 Bluetooth Commands

| Command | Function                      |
| ------- | ----------------------------- |
| `1`     | Move Forward                  |
| `2`     | Stop                          |
| `3`     | Hazard Lights (Blink 3 Times) |
| `4`     | Reverse / Stop Reverse        |
| `5`     | Turn Right (90°)              |
| `6`     | Turn Left (90°)               |
| `0`     | Autonomous Mode               |
| `h`     | Play Nokia Tune               |
| `i`     | Play Happy Birthday           |
| `j`     | Play Airtel Theme             |
| `k`     | Play Merry Christmas          |
| `s`     | Slow Speed (PWM = 100)        |
| `m`     | Medium Speed (PWM = 150)      |
| `f`     | Fast Speed (PWM = 255)        |

---

## 🛠 Hardware Components

| Component                     | Quantity |
| ----------------------------- | -------- |
| STM32F103C8T6 Microcontroller | 1        |
| L298N Motor Driver            | 1        |
| DC Motors                     | 4        |
| HC-SR04 Ultrasonic Sensor     | 1        |
| Infrared Sensors              | 2        |
| HC-05 Bluetooth Module        | 1        |
| Buzzer                        | 1        |
| LEDs                          | 2        |
| 18650 Li-ion Batteries        | 2        |
| Solar Panel / Solar Cell      | 1        |
| TP4056 Charging Module        | 1        |
| LM2596 DC-DC Buck Converter   | 1        |
| AMS1117 Voltage Regulator     | 1        |

---

## 💻 Software Requirements

* Arduino IDE (STM32 Board Package Installed)
* STM32 Cube IDE
* STM32 ST-LINK Utility
* Bluetooth Terminal Application

---

## 📍 Pin Configuration

| Component          | GPIO Port | Pin                |
| ------------------ | --------- | ------------------ |
| LED1               | GPIOB     | PB0                |
| LED2               | GPIOB     | PB1                |
| Onboard LED        | GPIOC     | PC13               |
| Buzzer             | GPIOA     | PA8                |
| IR Sensor 1        | GPIOA     | PA0                |
| IR Sensor 2        | GPIOA     | PA1                |
| Ultrasonic Trigger | GPIOA     | PA2                |
| Ultrasonic Echo    | GPIOA     | PA3                |
| Motor IN1          | GPIOB     | PB5                |
| Motor IN2          | GPIOB     | PB6                |
| Motor IN3          | GPIOB     | PB7                |
| Motor IN4          | GPIOB     | PB8                |
| Motor Enable (PWM) | GPIOA     | Configured PWM Pin |

---

## 🏗 System Architecture

```text
Solar Panel
     │
     ▼
 TP4056 Charger
     │
     ▼
 18650 Battery Pack
     │
     ▼
 LM2596 Buck Converter
     │
     ├────────► STM32F103C8T6
     │
     ├────────► HC-05 Bluetooth Module
     │
     ├────────► Ultrasonic Sensor
     │
     ├────────► IR Sensors
     │
     ├────────► LEDs & Buzzer
     │
     ▼
 L298N Motor Driver
     │
     ▼
 DC Motors
```

---

## 🚦 Navigation Logic

### Ultrasonic Sensor

* Continuously monitors the distance ahead.
* Vehicle stops when an obstacle is detected within the predefined threshold.

### Infrared Sensors

* Detect obstacles on the left and right sides.
* Assist in determining a safe turning direction.

### Autonomous Mode

1. Move forward continuously.
2. Monitor ultrasonic and IR sensors.
3. Stop when an obstacle is detected.
4. Analyze left and right sensor data.
5. Turn toward the safer direction.
6. Resume forward motion.

---

## ⚡ Power Management

The system incorporates a solar-assisted charging mechanism:

* Solar panel charges batteries through the TP4056 module.
* TP4056 provides overcharge and protection features.
* LM2596 regulates voltage for stable system operation.
* AMS1117 supplies regulated voltage to sensors and communication modules.
* Battery status can be monitored during operation.

---

## 🧪 Testing Procedures

### Power System

* Verify TP4056 charging indicators:

  * 🔴 Red LED = Charging
  * 🔵 Blue LED = Fully Charged

### Ultrasonic Sensor

* Check distance measurement accuracy.
* Validate obstacle detection threshold.

### IR Sensors

* Adjust onboard potentiometers.
* Verify:

  * LOW = Obstacle Detected
  * HIGH = No Obstacle

### Motor Driver

* Test:

  * Forward
  * Reverse
  * Left Turn
  * Right Turn
  * PWM Speed Control

### Bluetooth Communication

* Pair HC-05 with smartphone.
* Send commands and monitor serial feedback.

---

## 🚀 Getting Started

### Hardware Setup

1. Assemble components according to the pin mapping table.
2. Verify all wiring connections.
3. Check battery polarity.
4. Verify regulated voltage outputs using a multimeter.
5. Connect sensors, motor driver, and Bluetooth module.

### Software Setup

1. Install STM32 board support package in Arduino IDE.
2. Open the project source code.
3. Select **STM32F103C8T6 (Blue Pill)**.
4. Compile and upload using ST-LINK.
5. Pair smartphone with HC-05.
6. Open a Bluetooth terminal app.
7. Start sending commands.

---

## 🎯 Applications

* Smart logistics and warehouse automation
* Healthcare contactless delivery robots
* Indoor service robots
* Hotel and office assistance systems
* Educational robotics platforms
* Research and prototyping
* Home automation assistance
* Security patrol systems
* Industrial material transportation

---

## 🔍 Challenges Addressed

* Sensor calibration for reliable obstacle detection
* Real-time processing of multiple sensor inputs
* PWM optimization for smooth motor operation
* Stable solar charging integration
* Battery protection and voltage regulation
* Bluetooth communication latency handling

---

## 🔮 Future Enhancements

* Camera-based navigation
* Computer vision integration
* Cloud-based monitoring dashboard
* Mobile application development
* LiDAR integration
* SLAM (Simultaneous Localization and Mapping)
* GPS support for outdoor navigation
* AI-powered path planning

---

## 📄 License

This project is intended for **academic, educational, and research purposes**.

---

## 👨‍💻 Author

**NITHIN V 23BEC1346 – Embedded C Project**

Developed as a low-cost, solar-assisted autonomous driving platform for indoor navigation and robotics research.

---

### ⭐ If you found this project useful, consider giving it a star on GitHub!

# 🤖 Arduino-Based Obstacle Avoiding Robot

The **Obstacle Avoiding Robot** is an **autonomous navigation system** built using the **Arduino Uno R3 microcontroller**.  
It employs an **ultrasonic sensor** mounted on a **servo motor** to detect nearby obstacles and adjusts its direction automatically using an **L298N motor driver**.  
This project demonstrates real-time obstacle detection, decision-making, and motion control — key aspects of embedded and robotic systems.

---

## 🚀 Project Overview

The robot detects obstacles in its path using ultrasonic sound waves and dynamically changes its direction to avoid collisions.  
The combination of sensors, motors, and control logic enables the robot to move intelligently in different environments.

---

## 🧩 Key Features

- 🔊 **Ultrasonic Distance Detection:**  
  Measures the distance to nearby objects using sound waves.  
- 🔄 **Servo-Controlled Scanning:**  
  The ultrasonic sensor rotates via a servo motor to scan the surroundings (left, right, and forward).  
- ⚙️ **DC Motor Control:**  
  Dual DC motors driven by the **L298N motor driver module** for precise movement.  
- 🧠 **Autonomous Navigation:**  
  Real-time decision-making to choose the best direction and avoid obstacles.  
- 🔋 **Low-Cost Embedded Design:**  
  Built entirely from affordable, easily available components.

---

## ⚙️ Hardware Components

| Component | Description |
|------------|-------------|
| **Arduino Uno R3** | Central microcontroller for controlling the system |
| **Ultrasonic Sensor (HC-SR04)** | Measures distance to obstacles |
| **Servo Motor (SG90)** | Rotates the ultrasonic sensor to scan the area |
| **L298N Motor Driver** | Controls the DC motors’ direction and speed |
| **DC Motors (x2)** | Drive the robot’s wheels |
| **Chassis & Wheels** | Base structure and movement mechanism |
| **Jumper Wires & Breadboard** | Circuit connections |
| **Power Supply (9V or Battery Pack)** | Provides operating voltage |

---

## 🧠 Working Principle

1. The **ultrasonic sensor** continuously emits sound waves and measures the time taken for the echo to return.  
2. Based on the distance data, the **Arduino Uno** determines if an obstacle is within a certain threshold.  
3. If an obstacle is detected:
   - The **servo motor** rotates the sensor to check left and right distances.  
   - The **Arduino** selects the direction with more free space.  
   - The **L298N driver** adjusts the motor direction accordingly.  
4. The robot then moves forward, left, or right — avoiding collisions autonomously.

---

## 🔌 Circuit Diagram Overview

**Connections:**

| Component | Arduino Pin |
|------------|-------------|
| Ultrasonic Trigger | D9 |
| Ultrasonic Echo | D10 |
| Servo Motor Signal | D11 |
| L298N IN1 | D2 |
| L298N IN2 | D3 |
| L298N IN3 | D4 |
| L298N IN4 | D5 |
| L298N ENA/ENB | D6 / D7 |
| Power (VCC, GND) | 5V / GND |

---

## 💻 Software & Code

- **Platform:** Arduino IDE  
- **Language:** C/C++  
- **Key Libraries Used:**
  - `Servo.h` – for servo motor control  
  - `NewPing.h` – for efficient ultrasonic distance measurement  

---

### 🧾 Example Pseudocode

```c
// Pseudocode for Obstacle Avoidance Logic
loop() {
  distance = getDistance();
  
  if (distance < threshold) {
    stopMotors();
    scanLeft = measureLeft();
    scanRight = measureRight();
    
    if (scanLeft > scanRight) turnLeft();
    else turnRight();
  } else {
    moveForward();
  }
}

}

---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives
* **Hardware Implementation:** Configure and deploy the ESP32 and ESP32-Cam modules.
* **Cloud Integration:** Implement AWS IoT Core connectivity to publish and subscribe to messages for remote device control.

### Tasks to be carried out this week

| Day | Task Description | Start Date | Completion Date | Reference Material |
| :--- | :--- | :---: | :---: | :--- |
|  2 | Debug and stabilize firmware errors on the ESP32-Cam module. | 15/06/2026 | 15/06/2026 | [CameraWebServer Repository](https://github.com/quannguyenlehai-cell/intership/tree/main/IoT/CameraWebServer) |
|  3 | Wire, program, and test the ESP32 to control an SG90 servo motor. | 16/06/2026 | 16/06/2026 | [Servo Control Sketch](https://github.com/quannguyenlehai-cell/intership/tree/main/IoT/sketch_jun9b) |
|  4 | Develop ESP32 firmware to subscribe and publish to AWS IoT Core topics. | 17/06/2026 | 17/06/2026 | |
|  5 | Troubleshoot and resolve network connection/stability bugs on the ESP32. | 18/06/2026 | 18/06/2026 |  |
|  6 | Integrate AWS IoT Core SDK into the Node.js backend for remote device communication. | 19/06/2026 | 19/06/2026 | [Backend Server Script](https://github.com/quannguyenlehai-cell/intership/blob/main/server/index.mjs) |

---

### Week 3 Achievements
#### 1. Hardware Deployment & Debugging (Successfully Completed)
* **ESP32-Cam Integration:**
  * Configured the Arduino IDE environment with the necessary ESP32 board manager and camera libraries.
  * Successfully flashed and hosted the local CameraWebServer, resolving initial stream dropouts and hardware debugging errors.

* **ESP32 Base Application:**
  * Set up core libraries for hardware control and MQTT communication.
  * Successfully programmed PWM logic to control the SG90 servo motor, ensuring smooth angles and stable hardware operations.

#### 2. Cloud & Backend Integration (In Progress)
* **AWS IoT Core Protocol:**
  * Developed the MQTT publish/subscribe logic on the ESP32 to handle remote command payloads.
  * Built a backend communication gateway using Node.js to bridge server commands to AWS IoT Core, enabling basic remote control over the hardware infrastructure.
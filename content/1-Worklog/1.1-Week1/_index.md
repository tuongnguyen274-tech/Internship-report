---
title: "Week 1 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Define the core concept, scope, and operational flow of the Facial Recognition Door system.
* Research existing open-source projects and industry examples to understand hardware and software requirements.
* Compare local edge processing versus cloud-based facial recognition to finalize the technical stack.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Brainstorm project concept and core features (e.g., live video feed, automated unlocking mechanism, user management system)                                                                                                   | 06/01/2026 | 06/01/2026      |
| 3   | - Research existing facial recognition door projects <br> - Review open-source examples using ESP32, ESP32-CAM, and SERVO SG90                                           | 06/02/2026 | 06/02/2026      | <https://maker.pro/arduino/projects/> <br> <https://www.meegle.com/en_us/topics/face-recognition/> |
| 4   | - Analyze and compare face recognition frameworks: <br>&emsp; + Local frameworks (OpenCV, Dlib, Face_Recognition Python library) <br>&emsp; + Cloud APIs (AWS Rekognition, Azure Face API) | 06/03/2026 | 06/03/2026      | <https://aws.amazon.com/rekognition/> <br> <https://opencv.org/> |
| 5   | - Finalize Hardware Choices: Select the specific microcontrollers (ESP32-CAM + ESP32) and servo (SG90) <br> - Draft a theoretical circuit schematic detailing the power distribution (external 5V) and common ground                           | 06/04/2026 | 06/04/2026      | Component pinout diagrams |
| 6   | - **Environment Preparation:** <br>&emsp; + Install Arduino IDE and configure the ESP32 Board Manager <br>&emsp; + Download necessary libraries (ESP32Servo, camera drivers) <br>&emsp; + Analyze official sample code structures (CameraWebServer)                                                                                  | 06/05/2026 | 06/05/2026      | <https://docs.espressif.com/> |


### Week 1 Achievements:

* Understood the core operational workflow of the Facial Recognition Door system: 
  * Image Capture via ESP32-CAM
  * On-board Face Verification (Edge AI processing)
  * Signal Transfer to ESP32
  * Servo SG90 Latch Rotation for door actuation

* Completed a comparative analysis between cloud APIs (AWS Rekognition) and local edge frameworks to choose an entirely offline, low-latency processing model.

* Finalized the technical Bill of Materials (BOM) without physical procurement, preparing the list of specific components needed.

* Drafted a comprehensive theoretical circuit diagram to address hardware power constraints, including:
  * ESP32-CAM pinout configuration
  * Separate external 5V power supply line for the servo
  * Common ground linkage to avoid signal noise

* Installed and prepared the software development environment on the computer, including:

  * Arduino IDE application setup
  * Espressif ESP32 Board Manager installation
  * Pre-loading the ESP32Servo library
  * Downloading required camera driver dependencies

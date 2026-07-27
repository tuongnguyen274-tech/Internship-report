---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
# INTERNSHIP PROJECT: FACIAL RECOGNITION DOOR LOCK SYSTEM (ESP32-CAM + AWS LAMBDA)

An intelligent access control system combining budget-friendly AI hardware (**Edge-AI**) and Cloud infrastructure (**AWS Serverless**).

## 1. Where did the idea come from? (Real-world Problem)

In practice, existing door locking solutions each have their own drawbacks:

* **Physical Keys & Keycards:** Easily lost, forgotten, or duplicated without authorization.
* **PIN Passwords:** Vulnerable to shoulder surfing or unwanted sharing.
* **Cloud Facial Recognition Locks:** Often expensive and suffer from high latency due to uploading image data to remote servers.

**Project Goal:** 
Build an ultra-affordable facial recognition door unlocking system (hardware cost under **$17 / 400,000 VND**), with ultra-low latency, while enabling administrators to manage access history remotely via a Web interface.

---

## 2. How does this system work?

The architecture is divided into two main components working seamlessly together:

### A. At the Door Device (ESP32-CAM)
* All facial recognition processing is handled directly on the ESP32-CAM microcontroller (**Edge-AI**).
* **Workflow:** Person stands in front of camera → Chip scans face → Data matches → Lock opens instantly (latency under $0.5$ seconds).

### B. On the Cloud (AWS Infrastructure)
Once the door unlocks successfully, the device sends a "report" to the cloud to log access history:

* **AWS IoT Core:** Receives reported messages sent from the edge device.
* **AWS Lambda:** Automatically triggers to process incoming data and store access logs in the database (**Amazon RDS**).
* **AWS Amplify & API Gateway:** Provides a Web dashboard for administrators. Admins can remotely:
  * View real-time access logs.
  * Add/Remove users.
  * Trigger remote door unlocking.

---

## 3. Key Highlights & Takeaways

* **Ultra-Low Latency ($< 500\text{ms}$):** On-device Edge-AI processing triggers the door lock immediately without waiting for server responses.
* **Ultra-Affordable Cost:** Hardware cost for one door setup (ESP32-CAM, servo motor, circuitry...) is only around **$17 (~400,000 VND)** — over 90% cheaper than commercial smart locks.
* **Optimized Cloud Cost:** Leveraging a Serverless backend (**AWS Lambda**, **AWS IoT Core**...), the system scales automatically when used and incurs virtually zero cost when idle.

---

## 4. Conclusion

In just 2 short months, moving from a student new to Cloud concepts, building a hands-on project combining **IoT (ESP32-CAM)** and **Serverless (AWS Lambda)** has deepened my understanding of real-world system architecture.

[Link Facebook](https://www.facebook.com/groups/awsstudygroupfcj/)
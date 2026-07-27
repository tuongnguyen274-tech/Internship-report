---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---


# YOLOHOME-Smartlock

#### Overview

In this hands-on workshop, you will build a complete, cloud-connected smart door access system from scratch. By combining edge hardware (ESP32 microcontrollers and camera modules) with serverless cloud infrastructure on Amazon Web Services (AWS), attendees will learn how to capture biometrics, process real-time authentication pipelines, and control hardware actuators via cloud messaging.

### Workshop Structure & Learning Modules

#### Module 1: Hardware Assembly & Edge Firmware Setup

Objective: Assemble the physical components and configure edge microcontrollers.


- Connect the SG90 Servo Motor to the main ESP32 board using PWM-capable GPIO pins.

- Flash base firmware to the ESP32-Cam to capture video feeds and host local network endpoints.

- Verify hardware operation using the Arduino IDE environment.

#### Module 2: Setting Up the Cloud & Database Engine
Objective: Provision secure relational storage and serverless compute logic on AWS.

- Provision an AWS RDS (MySQL) instance to store registered user profiles and access logs.

- Create an AWS Lambda function containing the core business logic for user authorization.

- Configure IAM roles and environment variables to allow Lambda to talk securely to RDS.

#### Module 3: Building the REST API & Web Dashboard
Objective: Connect the frontend user interface with backend cloud endpoints.


- Build a REST API in AWS API Gateway using a greedy proxy route ({proxy+}) to send request payloads to AWS Lambda.

- Enable CORS (Cross-Origin Resource Sharing) policies for web access.

- Deploy the responsive web application on AWS Amplify for global online access, allowing users to scan faces, register accounts, and trigger manual admin overrides.

#### Module 4: Cloud-to-Hardware Control with AWS IoT Core
Objective: Enable real-time remote physical device control via MQTT.


- Provision an AWS IoT "Thing", attach security policies, and issue X.509 cryptographic certificates.

- Configure AWS Lambda to publish "UNLOCK" command payloads to AWS IoT Core upon successful face verification.

- Flash MQTT client firmware to the main ESP32, allowing it to receive real-time commands over TLS and rotate the SG90 Servo latch to unlock the door.

#### Content

1. [Workshop overview](5.1-Workshop-overview/)
2. [Prerequiste](5.2-Prerequisite/)
3. [Architechture](5.3-Architecture/)
4. [Practice](5.4-Practice/)
5. [Testing](5.6-Testing/)
---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives
* **Hardware Procurement:** Source the required hardware components (ESP32, ESP32-Cam, and SG90 Servo) for the system architecture.
* **Cloud Infrastructure Research:** Develop a foundational understanding of core AWS services, the AWS Management Console, and the AWS Command Line Interface (CLI).

### Tasks to be carried out this week

| Day | Task Description | Start Date | Completion Date | Reference Material |
| :--- | :--- | :---: | :---: | :--- |
|  2 | Research applicable AWS cloud services: IoT Core, Amplify, Lambda, RDS (MySQL), and API Gateway. | 08/06/2026 | 08/06/2026 |  |
|  3 | Deep dive into AWS IoT Core architecture: MQTT protocol, pub/sub messaging, Rule Engine, security policies, and client certificate attachment. | 09/06/2026 | 09/06/2026 | [AWS IoT Core Documentation](https://aws.amazon.com/vi/iot-core/) |
|  4 | Setup AWS development environment: account provisioning, AWS CLI installation, authentication configuration, and command structure practice. | 10/06/2026 | 10/06/2026 | [AWS Free Tier](https://aws.amazon.com/free/) <br> [AWS CLI Setup Guide](https://000011.awsstudygroup.com/vi/3-installcli/) |
|  5 | Source and verify primary hardware components: ESP32 development boards, ESP32-Cam modules, and SG90 micro servos. | 11/06/2026 | 11/06/2026 |  |
|  6 | Initialize local firmware repository and begin baseline development for the ESP32-Cam video streaming server. | 12/06/2026 | 12/06/2026 | [CameraWebServer Firmware](https://github.com/quannguyenlehai-cell/intership/blob/main/IoT/CameraWebServer/CameraWebServer.ino) |

---

### Week 2 Achievements

#### 1. Cloud Infrastructure & Architecture Design
* **Service Mapping:** Defined the core cloud architecture tailored to the project requirements:
  * **AWS IoT Core:** Selected for low-latency MQTT message distribution and direct ESP32 hardware control.
  * **AWS Amplify:** Designated for hosting and deploying the web application frontend.
  * **AWS Lambda:** Selected as the serverless compute engine to handle backend business logic.
  * **AWS API Gateway:** Chosen to manage secure API endpoints connecting the frontend interface to Lambda functions.
  * **AWS RDS (MySQL):** Selected as the relational database engine for persistence layer management.


#### 2. Environment Setup & Toolchain Configuration
* **AWS Environment:** Provisioned and secured an AWS Free Tier tenant structure.
* **CLI Deployment:** Successfully installed the AWS CLI toolchain locally and initialized authentication protocols using secure Access Keys, Secret Keys, and regional targets.
* **Operational Verification:** Mastered basic AWS CLI terminal operations, including configuration audits, regional listings, EC2 querying, and cryptographic key-pair lifecycle management.

#### 3. Hardware Procurement & Initial Testing (In Progress)
* **Inventory Sourcing:** Acquired all primary hardware components (ESP32, ESP32-Cam, SG90 servo) within schedule constraints.
* **Firmware Initialization:** Began setup of the base codebase for the CameraWebServer module to verify camera sensor health and local network attachment capability.
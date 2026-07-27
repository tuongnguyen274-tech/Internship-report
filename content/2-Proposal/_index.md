---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Smart Facial Recognition Door Access System
## An end-to-end edge-AI door control system

### 1. Executive Summary
This proposal outlines an edge-powered smart door access control system utilizing local biometric processing. By executing facial recognition directly on the ESP32-CAM AI-Thinker board and pairing it with a serverless AWS cloud stack (AWS IoT Core, Lambda, RDS, API Gateway, and Amplify), the system achieves near-instant offline door unlocking while providing centralized cloud logging and administration.

### 2. Problem Statement
### What’s the Problem?
Traditional key-based, RFID, or cloud-only biometric systems face several operational hurdles:
* Physical keys and access cards can be lost, stolen, or duplicated.
* PIN keypads are vulnerable to shoulder surfing and credential sharing.
* Standalone biometric hardware is often expensive, hard to update, and lacks centralized remote management.
* Cloud-only face matching introduces latency.

### The Solution
An Edge-AI Access System with cloud management:
* The ESP32-CAM AI-Thinker module captures image frames and runs face detection and recognition models locally.
* Lambda asynchronously publishes access logs, visitor image snapshots, and status updates to AWS IoT Core.
* Upon successful local match, the ESP32 immediately toggles a GPIO relay to unlock the door with minimal latency.
* An AWS Amplify web portal backed by AWS API Gateway, AWS Lambda, and AWS RDS allows administrators to remotely manage enrolled users, trigger manual overrides, and inspect audit logs.

### Benefits and Return on Investment
By processing facial recognition directly on the ESP32-CAM, this system guarantees zero-latency, offline access while completely eliminating recurring cloud AI fees. With hardware costs under $35 per door and a lightweight serverless backend, it reduces overall hardware and operating expenses by up to 90% compared to commercial alternatives—achieving full ROI in under two months.

### 3. Solution Architecture
Below is the system architecture highlighting local edge processing on the ESP32-CAM AI-Thinker board paired with AWS cloud management:

![Project Diagram](/images/2-Proposal/Diagram.jpg)

### AWS Services Used
- **AWS IoT Core**: Receives encrypted MQTT messages containing access attempts, timestamps, user IDs, and optional snapshot images.
- **AWS Lambda**: Serverless computing layer that processes incoming MQTT messages, formats audit events, and handles remote admin command requests.
- **Amazon API Gateway & AWS Amplify**: Provides a responsive dashboard for administrators to:
  + Register new users and push new face models down to the ESP32-CAM devices via MQTT device shadows.
  + Monitor real-time access events, successful entries, and unauthorized access attempts.
  + Execute remote manual door unlocks over secure HTTPS/WebSocket endpoints.
- **Amazon RDS**: Stores user profile data, access permissions, timestamped event logs, and registration records.

### Component Design
- **Edge Devices**: ESP32-CAM module running local facial recognition models, directly connected to a relay lock module for instant offline door control.
- **Data Ingestion**: AWS IoT Core utilizing MQTTS for secure, bidirectional messaging, device shadow state management, and real-time event log routing.
- **Data Storage**: AWS RDS storing relational user metadata, permission levels, timestamped door entry logs, and system audit trails.
- **Data Processing**: AWS Lambda providing serverless backend execution to parse incoming IoT messages, write audit records to AWS RDS, and process administrative commands.
- **Web Interface**: AWS Amplify hosting a responsive single-page admin dashboard for monitoring real-time logs, reviewing access attempts, and issuing remote manual door overrides.
- **User Management**: AWS RDS handling secure administrator authentication, JWT token management, and role-based access control alongside AWS API Gateway.

### 4. Technical Implementation
**Implementation Phases**
This project has two parts—setting up Facial Recognition System and building the platform following 3 phases:
- **Phase 1:** Edge Hardware & Cloud Core Setup (Weeks 1–4)
  + Flash ESP32-CAM AI-Thinker in local flash memory.
  + Connect GPIO relay circuit and verify zero-latency offline lock actuation upon face match.
  + Provision AWS IoT Core, generate device X.509 certificates, and build the MQTTS messaging pipeline.
  + Provision AWS RDS database instances, define schemas, and write AWS Lambda functions to handle IoT telemetry logging.

- **Phase 2:** Web Interface & System Integration (Weeks 5–7)
  + AWS RDS user pools for administrator access and role management.
  + Build and deploy the AWS Amplify web dashboard connected to AWS API Gateway endpoints.
  + Perform end-to-end operational testing across edge matching, relay triggering, and asynchronous cloud event logging.

- **Phase 3:** Technical Report & Documentation (Weeks 8–9)
  + Draft comprehensive technical project documentation, hardware circuit schematics, and system design diagrams.
  + Compile test results, performance analysis metrics, and operational user guides.
  + Finalize and deliver the technical project report.

**Technical Requirements**
- Hardware Component Requirements: ESP32-CAM (AI-Thinker), SERVO SG90, FTDI USB-to-TTL adapter (for flashing firmware), external 5V/2A power supply, and emergency override physical switch.
- Weather Platform: ESP-IDF / Arduino IDE with face detection and recognition library, AWS IoT Core, AWS Lambda (Node.js/Python runtime), AWS RDS (PostgreSQL/MySQL), Amazon API Gateway, AWS Amplify, and Amazon Cognito, MQTTS (MQTT over TLS 1.2/1.3) using X.509 client certificates, HTTPS, and JWT-based API authorization.

### 5. Timeline & Milestones
**Project Timeline**
- Internship (Months 6-8): 2 months.
    - Week 1-3: Study AWS and upgrade hardware.
    - Week 4-7: Design and adjust architecture.
    - Week 8-9: Implement, test, and report.

### 6. Budget Estimation
### Infrastructure Costs
- AWS Services:
    - AWS Lambda: $0.00/month.
    - AWS RDS: $11.405/month.
    - AWS VPC: $4.045/month
    - Others: $0.25/month.
    - AWS Amplify: $0.375/month.
    - AWS EC2 - Compute: $6.69/month
    - AWS EC2 - Other: 0.52/month

Total: $23.285/month.

- Hardware: $17 one-time (ESP-32, ESP-32-CAM, SERVO SG90, ...).

### 7. Risk Assessment
#### Risk Matrix
- Network Outages: low impact, high probability.
- Sensor Failures: high impact, low probability.
- Cost Overruns: medium impact, low probability.

#### Mitigation Strategies
- Network: Perform all matching locally; cache access logs in flash memory and sync asynchronously when restored.
- Sensors: Implement camera register calibration (auto-exposure) and add 5V LED fill lighting.
- Cost: Utilize AWS Free Tier, set budget alerts at 80% threshold, and use micro RDS instances.

#### Contingency Plans
- Network Outages: Utilize circular flash log buffers to prevent data loss during long disconnects.
- Sensor Failures: Retain physical mechanical key bypass and web portal manual unlock override.
- Cost Overruns: Scale down database retention periods to reduce storage costs.

### 8. Expected Outcomes
#### Technical Improvements: 
- Sub-500ms Latency: Local inference triggers relay instantly.
- Resource Efficiency: Serverless backend scales dynamically, minimizing idle cloud costs.
#### Long-term Value
- Low Cost Per Node: ~$10 per lock assembly vs. expensive commercial terminals.
- Enterprise Scalability: Single AWS Amplify dashboard manages multiple door nodes.
- Audit Compliance: Centralized RDS logs provide reliable access history.
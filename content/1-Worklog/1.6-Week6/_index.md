---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives
* **Cloud Infrastructure Optimization:** Complete the integration of AWS IoT Core to enable secure MQTT remote control of the ESP32 and establish user database synchronization.
* **Serverless Architecture Deployment:** Configure runtime environments, gateway routing pipelines, and core business logic within AWS Lambda.

### Tasks to be carried out this week

| Day | Task Description | Start Date | Completion Date | Reference Material |
| :--- | :--- | :---: | :---: | :--- |
| 2 | Debug and stabilize the local Node.js backend integration with the AWS IoT Core MQTT broker. | 06/07/2026 | 06/07/2026 | [Backend Server Script](https://github.com/quannguyenlehai-cell/intership/blob/main/server/index.mjs) |
|  3 | Provision the MySQL database environment and implement core data-access logic inside AWS Lambda functions. | 07/07/2026 | 07/07/2026 | Internal Source |
|  4 | Configure routing, deployment stages, and trigger integrations for AWS Lambda via AWS API Gateway. | 08/07/2026 | 08/07/2026 | Internal Source |
| 5 | Troubleshoot and resolve full-stack networking, routing, and access control exceptions between frontend and backend tiers. | 09/07/2026 | 09/07/2026 | Internal Source |
| 6 | Structure HTTP method requests/responses and configure Cross-Origin Resource Sharing (CORS) policies for secure frontend access. | 10/07/2026 | 10/07/2026 | Internal Source |

---

### Week 6 Achievements

#### 1. Serverless Logic & Database Integration
* **Database Layer Configuration:** Provisioned the relational MySQL data infrastructure and established secure connection pooling workflows within the serverless layer.
* **AWS Lambda Implementation:** Successfully deployed backend business logic to AWS Lambda functions, enabling programmatic database queries and automated synchronization routines with AWS IoT Core.
* **Broker Connectivity:** Resolved local Node.js engine bugs to guarantee reliable, low-latency command publishing from the backend layer directly to the hardware via the MQTT protocol.

#### 2. API Management & Full-Stack Security
* **API Gateway Routing:** Built a structured RESTful entry point using AWS API Gateway, successfully mapping incoming client endpoints to their respective backend AWS Lambda handlers.
* **CORS & Lifecycle Configuration:** Implemented robust Cross-Origin Resource Sharing (CORS) rules across all API Gateway resources, validating frontend-to-backend request headers and preflight handling.
* **Network Modernization:** Successfully diagnosed and resolved cross-tier network bottlenecks, standardizing model request structures on the frontend and response formats on the backend for stable, end-to-end telemetry flow.
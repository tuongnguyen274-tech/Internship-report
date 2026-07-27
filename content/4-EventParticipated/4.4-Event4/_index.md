---
title: "Event 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.4. </b> "
---

# Agentic AI Build Week (FCAJ x BBAW) Showcase

Welcome to the project repository for the **Agentic AI Build Week (FCAJ x BBAW)**. This event showcased production-grade autonomous agent systems, real-time computer vision pipelines, and automated cloud architecture solutions built on Amazon Web Services (AWS).

---

## Featured Projects

### 1. Signal Scout
* **Team**: Dream AI Team
* **Members**: Lê Tấn Lực, Đỗ Hoàng Hiếu, Triệu Quốc Hào, Nguyễn Văn Duy Khiêm, Nguyễn Công Minh, Nguyễn Trần Minh Quân

#### Overview
Signal Scout connects scattered corporate metrics and signals into a clear, verifiable story. It enables early detection of corporate strategic changes and restructuring signals, providing transparent decision support for corporate strategy, risk management, and competitive intelligence teams.

#### Key Features
* **Evidence Validation**: Collects and validates corporate data from public sources.
* **Metric Scenario Building**: Analyzes financial/operational metrics to project strategic scenarios.
* **Actionable Decision Support**: Helps enterprise teams decide whether to *Maintain, Adapt, or Accelerate* strategic postures.

#### Architecture & Tech Stack
* **AI Layer**: Amazon Bedrock, AgentCore Short-Term Memory, AgentCore Runtime
* **Data & Storage**: Amazon DynamoDB, S3 Intelligent-Tiering, Secrets Manager
* **Hosting & Web**: AWS Amplify Hosting, AWS WAF, API Gateway (HTTP), Route53, Amazon Cognito
* **Monitoring & Tooling**: AWS CloudWatch, CloudTrail, AWS Lambda, Langfuse, Apify, TinyFish

---

### 2. S.H.E.P.H.E.R.D.
* **Team**: 3KA
* **Members**: Huỳnh An Khương, Nguyễn Quốc Huy, Ngô Quang Khôi, Hoàng Lê Thành Đức, Đặng Nguyễn Phước Lộc, Đặng Trường Hưng

#### Overview
**S.H.E.P.H.E.R.D.** (*Smart Human-flow Evaluation, Prediction, Hazard Detection, Response, and Dispatch*) converts raw venue camera footage into proactive operational crowd intelligence. Built to solve slow and reactive manual monitoring, it predicts overcrowding pressure and dispatch needs in real time.

#### Key Features
* **Autonomous Monitor**: Continuously tracks crowd density, measures queue conditions, and flags early congestion hazards.
* **Operator Copilot**: Allows operators to query live metrics using natural language and receive automated action recommendations.

#### Architecture & Tech Stack
* **Computer Vision**: YOLO + ByteTrack
* **Inference & AI Agents**: Amazon SageMaker, Amazon Bedrock AgentCore, Strands Agent
* **Interface**: React Monitoring Dashboard

---

### 3. Solution Architect Professional AI Native App
* **Team**: Plan V
* **Members**: Phạm Tiến Thuận Phát, Huỳnh Hoàng Long, Lê Minh Nghĩa, Trần Đại Vĩ, Nguyễn An

#### Overview
An AI-native assistant designed for Solution Architects to eliminate manual analysis of Business Requirements Documents (BRD/PRD). It reads unstructured requirements, drafts compliant hybrid-cloud architecture options, produces Draw.io diagrams with official AWS icons, generates Terraform IaC code, and calculates regional AWS cost estimates.

#### Key Features
* **Automated Requirements Extraction**: Analyzes natural language inputs to surface requirement gaps and assumptions.
* **Diagramming & Code Generation**: Outputs editable Draw.io diagrams and Terraform code automatically.
* **Cost Estimation**: Calculates directional AWS cost estimates (for `ap-southeast-1`).

#### Architecture & Tech Stack
* **Core Compute**: AWS Elastic Container Service (ECS Fargate), PostgreSQL database, Amazon EFS
* **AI & Integration Services**: Amazon Bedrock, Draw.io MCP, AWS Pricing MCP, Knowledge Base
* **Network & Security**: AWS CloudFront, Application Load Balancer (ALB), NAT Gateway, VPC (Public/Private Subnets), Amazon Cognito, AWS CloudWatch, Amazon ECR
* **IaC & Tooling**: Terraform

---

## Summary Comparison

| Project | Domain / Problem Solved | Core AI Models & Frameworks | Key AWS Infrastructure |
| :--- | :--- | :--- | :--- |
| **Signal Scout** | Early Corporate Strategic Change Detection | Amazon Bedrock, AgentCore, Langfuse | DynamoDB, Amplify, AWS Lambda, CloudWatch |
| **S.H.E.P.H.E.R.D.** | Smart Crowd Management & Hazard Alerting | YOLO, ByteTrack, Bedrock AgentCore | Amazon SageMaker, Amazon Bedrock |
| **SA Pro AI Native App** | BRD Analysis, Architecture & IaC Automation | Bedrock, Draw.io MCP, AWS Pricing MCP | ECS Fargate, CloudFront, EFS, PostgreSQL |

---

## Event Lessons & Takeaways

1. **Showing Up Matters**: Taking the leap to participate is half the battle.
2. **Scope Tight & Finish**: Small, working prototypes beat large, broken ideas under tight timelines.
3. **Agentic Workflows**: Utilizing Model Context Protocol (MCP) and Bedrock agents significantly streamlines real-world enterprise tasks.

#### Some event photos
![Event4](Event4.png)
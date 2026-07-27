---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Summary Report: “Cloud Architecture, AI Innovation, and Infrastructure Operations”

### Event Objectives

- Explore real-time cloud backends for game engines.
- Introduce GraphRAG architectures for multi-hop data retrieval.
- Provide a career roadmap from IT helpdesk to DevOps.
- Demonstrate machine learning for network intrusion detection
- Detail container mechanics and Dockerfile optimization.
- Outline frameworks for effective technical teamwork.

### Speakers

- **Nguyen Quoc Bao** – Cloud & Game Backend Developer
- **Viet Phat** – AI Major, Swinburne University of Technology
- **Tran Trung Vinh** – System Administrator, Central Retail Group
- **Le Hoang Gia Dai** – AWS G3 Team, HUTECH University
- **Bao Huynh** – Junior Cloud Native Developer, Endava Vietnam
- **Truong Huy Phuoc** – Team Collaboration Specialist

### Key Highlights

#### Multiplayer Architectures in the Cloud

- **Stateful Routing:** Uses AWS API Gateway WebSockets and route keys for real-time JSON traffic.  
- **Serverless Backend:** Nodes.js 20 Lambda handles payloads; DynamoDB tracks player connection IDs.  
- **Protocol Choice:** UDP for low-latency physics; WebSockets for session states; HTTP for profiles.  
- **Client Integration:** Implemented via Godot 4 WebSocketPeer and processed inside the native _process loop.  

#### Advanced GraphRAG Architectures

- **Graph Indexing:** Replaces basic text vector matching with structural relationship models for multi-hop lookups. 
- **Managed Pathway:** Uses Amazon Bedrock Knowledge Bases for embedding generation and Neptune Analytics for indexing. 
- **Custom Pathway:** Employs LlamaIndex for text-to-graph building and Amazon Neptune for Cypher queries.    

#### Sysadmin & DevOps Career Blueprint

- **Mindset Shift:** Moves from reactive desktop troubleshooting to proactive infrastructure automation and system auditing.  
- **Production Safety:** Enforces a strict rule never to test changes directly in live production environments. 
- **Growth Roadmap:** Steps through networking (CCNA), Linux (RHCSA), cloud scaling, IaC (Terraform), and automated CI/CD. 

#### Machine Learning-Based NIDS

- **Anomaly Detection:** Complements static firewall signatures with ML models to detect Zero-Day vectors.  
- **Data Engineering:** Validates models using CSE-CIC-IDS2018 dataset, data pruning, and a LightGBM Confusion Matrix.  
- **Cloud Remediation:** Streams logs from WAF/ALB via Kinesis Firehose to S3, triggering alerts via GuardDuty and SNS. 

#### Containerization Mechanics with Docker

- **OS Virtualization:** Containers share the host kernel, making them lighter and faster than full Virtual Machines.
- **Layer Optimization:** Every line in a Dockerfile creates an immutable, reusable build layer.
- **Cache Invalidation:** Changing an instruction invalidates the cache for that step and all subsequent layers.

#### Frameworks for Effective Teamwork

- **4 Core Rules:**
  * Establish clear goals
  * Match tasks to individual skills
  * Open communication
  * Ensure personal accountability
- **Digital Tools:** 
  * Uses Trello and ClickUp for tracking
  * Slack and Discord for continuous developer communication  

### Key Takeaways

#### Design Mindset

- **Domain-First:** Architecture must be driven by business requirements, not technology trends.
- **Protocol Strategy:** Align communication tools (Sockets, HTTP, streams) with structural payload requirements.
- **Risk Mitigation:** Build isolated staging tiers and monitoring loops to protect production availability.

#### Technical Architecture

- **Serverless Patterns:** Leverage event-driven compute (Lambda) and managed databases (DynamoDB) to reduce overhead.
- **Efficient Builds:** Structure Dockerfiles strategically to maximize layer caching and minimize image weight.  
- **Relational Context:** Enhance traditional text vector search by mapping data linkages with Graph databases.

#### Modernization Strategy

- **Skill Layering:** Move systematically from operating system fundamentals into automated IaC and container delivery.
- **Task Alignment:** Use agile frameworks to map individual engineering tickets directly to team milestones.

### Applying to Work

- **Deploy WebSockets:** Test serverless AWS WebSocket architectures for apps needing low-latency, real-time data.  
- **Test Graph RAG:** Pilot LlamaIndex and Amazon Neptune to manage highly relational context queries.  
- **Adopt IaC:** Replace manual system configuration by version-controlling environments with Terraform.  
- **Optimize Dockerfiles:** Reorder Dockerfile instructions to leverage caching and shrink container sizes.  
- **Implement ML NIDS:** Stream network logs into ML pipelines to identify hidden behavioral anomalies.  
- **Organize Workspaces:** Standardize team project tracking and sprints using ClickUp or Trello boards. 

### Event Experience

Event 1 delivered highly practical insights covering cloud networks, advanced AI, behavioral security, and engineering workflows.

#### Learning from highly skilled speakers
- Industry experts presented actionable, production-proven architectural strategies for cloud and container scaling.
- Presenters shared clear professional roadmaps for transitioning into high-impact DevOps and Sysadmin roles.

#### Hands-on technical exposure
- Analyzed the mechanics of setting up real-time serverless sockets, functions, and stateful databases.
- Studied data preprocessing, ML model matrix validation, and automated cloud incident reporting pipelines.
- Explored container layers and runtime caching to see exactly how commands affect build efficiency.

#### Leveraging modern tools
- Compared managed vs. custom AI pipelines using graph indexing for advanced context searches. 
- Reviewed project tracking software configurations designed to keep agile teams aligned.

#### Networking and discussions
- The sessions highlighted that continuous documentation and shared vocabulary bridge the gap between business and dev teams.  

#### Lessons learned
- Scalability requires matching protocols to the use case and decoupling services with serverless parts.
- System reliability relies on shifting from manual fixes to automated IaC, layer optimization, and proactive ML monitoring.

#### Some event photos
*Add your event photos here*  

>Overall, Event 1 provided a strong combination of technical architectures, optimization patterns, and actionable career strategies for modern cloud environments.

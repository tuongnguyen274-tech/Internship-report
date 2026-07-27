---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# AWS LAMBDA SELF-STUDY REPORT FOR BEGINNERS

## 1. Introduction

For newcomers to Cloud Computing, navigating hundreds of services alongside complex technical jargon can often feel overwhelming and daunting. However, through hands-on practice with **AWS Lambda**, the core concepts of the cloud model gradually become much more intuitive and accessible.

---

## 2. Core Features of AWS Lambda

Based on practical experience, AWS Lambda offers three key advantages that significantly streamline the application development process:

### 2.1. Serverless Model (No Server Management)
* **Traditional Approach vs. Lambda:** When working on capstone or major school projects, developers usually have to manually run and maintain a local server (Node.js, Python, etc.) 24/7 to listen for incoming requests.
* **AWS Lambda Mechanism:** Users simply upload their source code to the cloud. AWS automatically handles the entire underlying infrastructure, including operating system installations, system patching, and auto-scaling during high traffic.

### 2.2. Event-Driven Architecture
A Lambda function does not run continuously; instead, it only "wakes up" when triggered by an event:
* **Common Triggers:**
  * A new image file is uploaded to the system.
  * A user clicks a button on a Web/App interface.
  * New data is written or updated in a database.
* **Execution Lifecycle:** Event occurs → Lambda executes code → Returns results → Automatically releases resources (turns off).

### 2.3. Cost Optimization
* **Pricing Model:** Charges are strictly based on the exact number of milliseconds the code actually runs.
* **Student Project Advantage:** When the application receives no traffic, the cost is **$0**. Combined with the **AWS Free Tier**, learners can freely experiment with school projects without worrying about unexpected charges.

---

## 3. Practical Lessons Learned (Best Practices)

| Initial Mistake | Solution & Fix |
| :--- | :--- |
| Packaging a large monolithic backend application into a single Lambda function, resulting in slow execution and difficult maintenance. | **Break Down Tasks (Microservices / Single Responsibility):** Split the application into smaller functions, each handling a single responsibility (e.g., 1 function for user registration, 1 function for saving data). |

> **Key Takeaway:** Modularizing functionality allows the system to remain flexible, makes bug isolation significantly easier, and simplifies maintenance throughout development.

---

## 4. Conclusion

AWS Lambda is an ideal starting point for students and cloud beginners because it eliminates the barrier of server and network infrastructure management. Users can focus solely on writing correct business logic to successfully deploy their products.

[Link Facebook](https://www.facebook.com/groups/awsstudygroupfcj/)
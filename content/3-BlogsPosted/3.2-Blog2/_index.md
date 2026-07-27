---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
WHAT HAVE I LEARNED AFTER EXPERIENCING AWS IOT CORE?

Lately, I've had time to delve deeper into researching and applying AWS IoT Core to hardware and embedded systems (IoT) projects. I have to admit that since switching from traditional MQTT brokers to AWS IoT Core, my approach to IoT system development has changed significantly! 

Here are some perspectives and lessons learned from the implementation process:

1. MQTT Protocol & Ultra-Low Latency 
Working with microcontrollers like the ESP32, hardware resources and network bandwidth are always major obstacles. AWS IoT Core supports the MQTT protocol, which is extremely optimized for low-power devices, allowing for almost instantaneous telemetry payload sending and actuator control commands (such as servos and relays) without consuming excessive resources.

2. Security is no longer a nightmare (X.509 Certificates & IAM Policy) 
Previously, personal IoT projects were often concerned about security, but AWS has standardized this very well. Each device (thing) requires:

A unique X.509 Cryptographic Certificate.

Amazon Root CA.

Fine-grained IAM Policies to precisely limit which devices are allowed to publish or subscribe to which topics.

Thanks to mTLS (Mutual TLS), I am completely confident in the system's closedness and security.

3. Excellent Serverless Ecosystem Synchronization 
The true power of AWS IoT Core lies in its seamless connectivity with other Serverless services:

IoT Rules Engine: Directly sends data to AWS Lambda for backend logic processing without needing a 24/7 server.

Database & Frontend Integration: Easily integrate with AWS RDS (MySQL) to store user information and push interfaces to AWS Amplify.
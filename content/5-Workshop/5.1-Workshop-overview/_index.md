---
title : "Introduction"
date : 2024-01-01 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

### Reason to choose AWS Service

#### AWS Amplify (Frontend Hosting)

- Automated CI/CD: Connects directly to Git repositories to automatically build and deploy the web dashboard whenever code is updated.

- Global Distribution: Serves the frontend via Amazon CloudFront's global Content Delivery Network (CDN), offering low-latency web access for administrative controls and user registration.

- Managed SSL: Automatically handles HTTPS certificates for secure web access without complex web server management.

#### AWS API Gateway (API Management)


Decoupled Architecture: Acts as a secure, managed entry point to route HTTP traffic cleanly between the frontend interface and backend serverless compute functions.

Greedy Proxy & CORS Handling: Simplifies endpoint setup through flexible proxy routing ({proxy+}) and provides native preflight CORS management to protect cross-origin browser requests.

Built-in Security & Throttling: Protects backend services from traffic spikes or Denial-of-Service (DoS) attacks.


#### AWS Lambda (Serverless Compute)

- Event-Driven & Cost-Effective: Executes business and verification logic only when triggered by incoming API calls, eliminating the cost and maintenance overhead of running dedicated $24/7$ servers.

- Seamless SDK Integration: Natively connects with AWS RDS for database queries and the AWS IoT Data Plane SDK to publish real-time hardware commands.

- Scalability: Handles sudden spikes in access requests effortlessly by auto-scaling compute capacity on demand.
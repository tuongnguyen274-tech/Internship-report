---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* **Backend & Database Management:** Resolve backend integration issues between the web database Lambda and the MQTT IoT Core handler; fix user registration bugs inside the unified database table to separate admin and guest requirements.
* **Frontend Responsiveness:** Optimize UI layouts for small viewports to resolve navbar scaling and table text compression issues.
* **Cloud Hosting Migration:** Migrate the static client interface from a localized environment to an internet-accessible architecture using AWS Amplify.
* **Full-Stack API Integration:** Establish secure, decoupled communication between the hosted frontend layer and the serverless backend via an operational REST API Gateway.

### Tasks to be carried out this week:
| Day | Task Description | Start Date | Completion Date | Reference Material |
| :---: | :--- | :---: | :---: | :--- |
| **2** | **Dual Backend Migration & Cloud Deployment:**<br>• Attempted merging web/database Lambda with local MQTT IoT handler; pivoted to isolating MQTT onto its own cloud architecture.<br>• Restructured legacy static frontend assets and executed cloud deployment via AWS Amplify. | 07/20/2026 | 07/27/2026 | AWS IoT Core / AWS Amplify Docs |
| **3** | **API Gateway REST Integration:**<br>• Established explicit frontend-to-backend interface logic utilizing AWS API Gateway REST endpoints to secure decoupled backend communications. | 07/21/2026 | 07/28/2026 | AWS API Gateway Developer Guide |
| **4** | **Greedy Proxy & Route Handling:**<br>• Configured standard `POST` integration methods and implemented greedy proxy routing (`{proxy+}`) for dynamic request dispatching to AWS Lambda. | 07/22/2026 | 07/29/2026 | AWS API Gateway Proxy Docs |
| **5** | **User Directory Patch & Network Diagnostics:**<br>• Modified registration routing logic to trigger password requirements conditionally based on security role.<br>• Diagnosed, traced, and resolved network anomalies, timeout parameters, and communication blocks across the stack. | 07/23/2026 | 07/30/2026 | Python Conditional Statements / CloudWatch Docs |
| **6** | **Mobile UI Optimization & CORS Security:**<br>• Fixed layout compression causing navbar downscaling; added horizontal scrollbar container (`overflow-x: auto`) for user directory tables.<br>• Structured unified request payloads/headers and enforced Cross-Origin Resource Sharing (CORS) rules. | 07/24/2026 | 07/31/2026 | MDN Web Design / W3C CORS Standards |
### Week 8 Achievements:

* **Backend Isolation & Code Safety:** Deployed the MQTT module onto a separate cloud instance after local communication merge attempts failed. Preserved the unused `handle_remote_override` function within the active code block as a safety measure against pipeline breakages.
* **User Directory Bugfix:** Resolved a verification flaw where standard passengers could not register due to global password requirements in the unified database table. Refactored logic to enforce strict password rules exclusively for the admin role.

* **Navbar Scaling:** Corrected layout math to prevent navigation bars from over-compressing on mobile viewports.
* **Overflow Controls:** Applied `overflow-x: auto` specifically to the Authorized Users Directory table container, providing a horizontal scrollbar for wide data while maintaining page rigidity.

* **Amplify Migration:** Decoupled user interface from localized environments, deploying the application to production tiers via AWS Amplify for high availability and global access.
* **Build Stability:** Configured base deployment parameters, ensuring proper loading of asset routes, static file links, and scripts across the public domain.

* **Greedy Proxy Architecture:** Provisioned an AWS API Gateway proxy integration (`{proxy+}` routing), allowing all client requests to hit a unified endpoint and route into the AWS Lambda compute stack.
* **Data Transport Layer:** Deployed secure `POST` submission methods, enabling reliable dispatch of access credentials, image data payloads, and administrative commands.

* **CORS Resolution:** Neutralized browser security blocks by establishing Cross-Origin Resource Sharing (CORS) rules on API Gateway, validating both preflight options and specific domain header matching.
* **Pipeline Synchronization:** Standardized frontend request schemas and backend response parameters to eliminate integration mismatches and maintain low-latency API communication loops.
---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Finalize video frames and canvas layout overlays
* Deploy an Amazon RDS MySQL database schema managed by a central Python AWS Lambda function.
* Validate end-to-end baseline communication using unhashed cleartext parameters.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2-3 | - **Media Layout Adjustment:** <br>&emsp; + Finish basic layout work for enroll.html and index.html <br>&emsp; + Align HTML5 canvas overlay boundaries over live video stream wrappers | 06/29/2026 | 06/30/2026 | HTML Canvas API |
| 4 | -Connect basic web form inputs to asynchronous API fetch routines without security wrappers | 07/01/2026 | 07/01/2026 | JavaScript Fetch API |
| 5 | - Deploy Python-driven AWS Lambda engine to build database tables | 07/02/2026 | 07/02/2026 | Python PyMySQL Driver Docs |
| 6 | - Build a 2500ms cyclical query testing loop inside index.html <br> - Test entry transfers using cleartext rows | 07/03/2026 | 07/03/2026 | AWS Lambda Action Routings |

### Week 5 Achievements:

* Completed Basic Multi-Page Web Interface:
  * Finalized layout structures for all 5 core frontend prototype files to prepare for future integrations.
  * Resolved responsive canvas alignment shifts over active video display containers.

* Deployed Relational Database Core Service Stack:
  * Programmed a Python AWS Lambda handler to initialize primary tracking tables inside Amazon RDS MySQL.
  * Used an internal query configuration (COALESCE) to automatically recycle cleared primary key row IDs.

* Verified End-to-End Communication Pipelines:
  * Pushed unhashed text entries from basic web forms directly into cloud database rows to verify fetch pathways.
  * Validated user directory table population logic and confirmed steady execution of the 2500ms kiosk terminal loop.
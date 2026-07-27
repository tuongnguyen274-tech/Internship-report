---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Integrate server-side password hashing and complex validation parameters for admin credentials.
* Deploy automated login session timeout and cleanup routines to prevent unauthorized access.
* Refine CSS layout structures and element alignments across all system web forms.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Fine-tune CSS layouts and fix flexbox centering on login.html, register_admin.html, and the dashboard     | 07/13/2026 | 07/13/2026      | CSS Flexbox & Grid Guide |
| 3-4   | - Password Hashing Integration: <br>&emsp; + Update the Python backend with PBKDF2-HMAC-SHA256 password hashing modules <br>&emsp; + Implement regex-based strength validation rules forcing complex character requirements on administrative sign-ups                                             | 07/14/2026 | 07/15/2026      | Python Hashlib Documentation |
| 5   | - Set up sessionStorage tracking via YOLO_ADMIN_SECURE_TOKEN_2026 <br> - Code auto-logout scripts to wipe tokens if idle or when the browser window exits                          | 07/16/2026 | 07/16/2026      | JavaScript Web Storage APIs |
| 6   | - Build password input visibility toggles (eye-icon text switches) <br> - Fix layout shifting bugs caused by dynamic DOM modifications            | 07/17/2026 | 07/17/2026      | DOM Element Properties |


### Week 7 Achievements:

* Deployed Robust Cryptographic Controls: 
  * Replaced cleartext database storage with a secure PBKDF2 hashing pipeline using 16-byte hex salts and 100,000 rounds.
  * Enforced rigid backend password complexity rules requiring at least 8 characters with mixed-case, numbers, and symbols.

* Hardened Administrative Access & Session Routines:
  * Locked internal administrative views behind active YOLO_ADMIN_SECURE_TOKEN_2026 storage check validations.
  * Configured an automated logout script that destroys active token credentials upon page exit or tab closure.

* Optimized UI Component Layouts & Visual Alignment:
  * Realigned global flex elements to keep interactive forms centered across different screen sizes.
  * Embedded a JavaScript toggle utility to show/hide password fields safely without shifting nearby DOM wrappers.
  * Fixed table horizontal overflow issues inside the primary dashboard event log grid.

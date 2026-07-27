---
title : "Testing"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Uncomment  ``` #define CAM_MODEL_AI_THINKER ```, press the upload button to upload the code.

![endpoint](/5-Workshop/5.6-Testing/Images/enable_cam.png)

After upload the code, in **Serial Monitor**, copy ip link.
![endpoint](/5-Workshop/5.6-Testing/Images/get_cam_ip.png)

Upload code to esp32.
![endpoint](/5-Workshop/5.6-Testing/Images/confirm_esp32.png)

Open browser and paste copied link to make sure esp32-cam is working.
![endpoint](/5-Workshop/5.6-Testing/Images/check_cam.png)

Log in as administrator.
![endpoint](/5-Workshop/5.6-Testing/Images/check_ad.png)

Enter ESP32-Cam copied link. Then press **go to door terminal**.
![endpoint](/5-Workshop/5.6-Testing/Images/add_link.png)

Test face-recognition. If the user in the database, the system inform **Welcome "user_name". Door unlocked**
![endpoint](/5-Workshop/5.6-Testing/Images/opening.png)

![endpoint](/5-Workshop/5.6-Testing/Images/process_face.png)

![endpoint](/5-Workshop/5.6-Testing/Images/recog-suc.png)

If not, the system inform **Access denied: face not recognized**

![endpoint](/5-Workshop/5.6-Testing/Images/fail.png)
Go back to admin dashboard and press **FORCE UNLOCK**. It sent message **Response: Send unlock command**
![endpoint](/5-Workshop/5.6-Testing/Images/force_unlock.png)

Press **FORCE UNLOCK**. It sent message **Response: Sent lock command**
![endpoint](/5-Workshop/5.6-Testing/Images/force_lock.png)

Press **Resgister Passenger** to register user.
![endpoint](/5-Workshop/5.6-Testing/Images/reg_pas.png)

Scan face for registration.
Enter name and transitGroup Classification.
![endpoint](/5-Workshop/5.6-Testing/Images/reg_face.png)

Press **Scan Face Biometrics** to change user scaned face.
![endpoint](/5-Workshop/5.6-Testing/Images/change_face.png)



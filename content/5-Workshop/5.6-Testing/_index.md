---
title : "Testing"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Uncomment  ``` #define CAM_MODEL_AI_THINKER ```, press the upload button to upload the code.

![endpoint](enable_cam.png)

After upload the code, in **Serial Monitor**, copy ip link.
![endpoint](get_cam_ip.png)

Upload code to esp32.
![endpoint](confirm_esp32.png)

Open browser and paste copied link to make sure esp32-cam is working.
![endpoint](check_cam.png)

Log in as administrator.
![endpoint](check_ad.png)

Enter ESP32-Cam copied link. Then press **go to door terminal**.
![endpoint](add_link.png)

Test face-recognition. If the user in the database, the system inform **Welcome "user_name". Door unlocked**
![endpoint](opening.png)

![endpoint](process_face.png)

![endpoint](recog-suc.png)

If not, the system inform **Access denied: face not recognized**

![endpoint](fail.png)
Go back to admin dashboard and press **FORCE UNLOCK**. It sent message **Response: Send unlock command**
![endpoint](force_unlock.png)

Press **FORCE UNLOCK**. It sent message **Response: Sent lock command**
![endpoint](force_lock.png)

Press **Resgister Passenger** to register user.
![endpoint](reg_pas.png)

Scan face for registration.
Enter name and transitGroup Classification.
![endpoint](reg_face.png)

Press **Scan Face Biometrics** to change user scaned face.
![endpoint](change_face.png)



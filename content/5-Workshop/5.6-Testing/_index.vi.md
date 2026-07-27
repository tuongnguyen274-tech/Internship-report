---
title : "Kiểm thử"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Bỏ comment ``` #define CAM_MODEL_AI_THINKER ```, Nhấn nút tải lên để tải code lên.

![endpoint](enable_cam.png)

Sau khi tải mã lên, trong **Serial Monitor**, hãy sao chép liên kết IP.
![endpoint](get_cam_ip.png)

Tải code lên esp32.
![endpoint](confirm_esp32.png)

Mở trình duyệt và dán đường dẫn đã sao chép để kiểm tra xem esp32-cam có hoạt động hay không.
![endpoint](check_cam.png)

Đăng nhập với tư cách quản trị viên.
![endpoint](check_ad.png)

Nhập đường dẫn ESP32-Cam đã sao chép. Sau đó nhấn **go to door terminal**.
![endpoint](add_link.png)

Kiểm tra khả năng nhận diện khuôn mặt. Nếu người dùng có trong cơ sở dữ liệu, hệ thống sẽ thông báo. **Welcome "user_name". Door unlocked**
![endpoint](opening.png)

![endpoint](process_face.png)

![endpoint](recog-suc.png)

Nếu không, hệ thống sẽ thông báo **Access denied: face not recognized**

![endpoint](fail.png)
Quay lại trang quản trị và nhấn **FORCE UNLOCK**. Hệ thống sẽ gửi thông báo **Respone: Sent unlock command**
![endpoint](force_unlock.png)

Nhấn **FORCE UNLOCK**. Hệ thống sẽ gửi thông báo **Respone: Sent lock command**
![endpoint](force_lock.png)

Nhấn **Resgister Passenger** để đăng ký người dùng.
![endpoint](reg_pas.png)

Quét khuôn mặt để đăng ký.
Nhập tên và phân loại nhóm quá cảnh.
![endpoint](reg_face.png)

Nhấn **Scan Face Biometrics** đổi khuôn mặt người dùng.
![endpoint](change_face.png)



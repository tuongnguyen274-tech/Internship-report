---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu Tuần 3
* **Triển khai Phần cứng:** Cấu hình và triển khai các module ESP32 và ESP32-Cam.
* **Tích hợp Điện toán Đám mây:** Triển khai kết nối AWS IoT Core để xuất bản (publish) và đăng ký nhận (subscribe) tin nhắn phục vụ điều khiển thiết bị từ xa.

### Các nhiệm vụ thực hiện trong tuần này

| Ngày | Mô tả nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :---: | :---: | :--- |
|  2 | Sửa lỗi (debug) và ổn định lỗi firmware trên module ESP32-Cam. | 15/06/2026 | 15/06/2026 | [Kho lưu trữ CameraWebServer](https://github.com/quannguyenlehai-cell/intership/tree/main/IoT/CameraWebServer) |
|  3 | Đấu dây, lập trình và kiểm thử ESP32 để điều khiển động cơ servo SG90. | 16/06/2026 | 16/06/2026 | [Mã nguồn điều khiển Servo](https://github.com/quannguyenlehai-cell/intership/tree/main/IoT/sketch_jun9b) |
|  4 | Phát triển firmware ESP32 để đăng ký (subscribe) và xuất bản (publish) tới các topic của AWS IoT Core. | 17/06/2026 | 17/06/2026 | |
|  5 | Khắc phục sự cố và xử lý các lỗi về kết nối/độ ổn định mạng trên ESP32. | 18/06/2026 | 18/06/2026 |  |
|  6 | Tích hợp AWS IoT Core SDK vào backend Node.js để giao tiếp và điều khiển thiết bị từ xa. | 19/06/2026 | 19/06/2026 | [Script Server Backend](https://github.com/quannguyenlehai-cell/intership/blob/main/server/index.mjs) |

---

### Kết quả đạt được trong Tuần 3
#### 1. Triển khai & Sửa lỗi Phần cứng (Đã hoàn thành)
* **Tích hợp ESP32-Cam:**
  * Cấu hình môi trường Arduino IDE với trình quản lý bo mạch (board manager) ESP32 và các thư viện camera cần thiết.
  * Nạp code thành công và khởi chạy CameraWebServer cục bộ, khắc phục sự cố gián đoạn luồng video ban đầu và các lỗi phần cứng.

* **Ứng dụng cơ sở trên ESP32:**
  * Thiết lập các thư viện cốt lõi cho việc điều khiển phần cứng và giao tiếp MQTT.
  * Lập trình thành công logic PWM để điều khiển động cơ servo SG90, đảm bảo chuyển động góc mượt mà và vận hành phần cứng ổn định.

#### 2. Tích hợp Đám mây & Backend (Đang thực hiện)
* **Giao thức AWS IoT Core:**
  * Phát triển logic xuất bản/đăng ký (publish/subscribe) MQTT trên ESP32 để xử lý dữ liệu lệnh từ xa.
  * Xây dựng gateway giao tiếp backend bằng Node.js để kết nối các lệnh từ server đến AWS IoT Core, cho phép điều khiển từ xa cơ bản đối với hạ tầng phần cứng.



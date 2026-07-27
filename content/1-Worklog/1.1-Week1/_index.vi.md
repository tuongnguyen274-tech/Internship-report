---
title: "Worklog Tuần 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu Tuần 1:

* Xác định khái niệm cốt lõi, phạm vi và luồng vận hành của hệ thống Cửa nhận diện khuôn mặt (Facial Recognition Door).
* Nghiên cứu các dự án mã nguồn mở hiện có và các ví dụ thực tế trong ngành để hiểu rõ các yêu cầu về phần cứng và phần mềm.
* So sánh giữa xử lý cục bộ tại biên (local edge) và nhận diện khuôn mặt dựa trên điện toán đám mây (cloud-based) để chốt tập công nghệ (technical stack).

### Các nhiệm vụ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Thảo luận ý tưởng dự án và các tính năng cốt lõi (ví dụ: phát trực tiếp video, cơ chế mở khóa tự động, hệ thống quản lý người dùng) | 06/01/2026 | 06/01/2026      |
| 3   | - Nghiên cứu các dự án cửa nhận diện khuôn mặt hiện có <br> - Tham khảo các ví dụ mã nguồn mở sử dụng ESP32, ESP32-CAM và SERVO SG90 | 06/02/2026 | 06/02/2026      | <https://maker.pro/arduino/projects/> <br> <https://www.meegle.com/en_us/topics/face-recognition/> |
| 4   | - Phân tích và so sánh các framework nhận diện khuôn mặt: <br>&emsp; + Các framework cục bộ (OpenCV, Dlib, thư viện Python Face_Recognition) <br>&emsp; + Các Cloud API (AWS Rekognition, Azure Face API) | 06/03/2026 | 06/03/2026      | <https://aws.amazon.com/rekognition/> <br> <https://opencv.org/> |
| 5   | - Chốt lựa chọn phần cứng: Chọn các vi điều khiển cụ thể (ESP32-CAM + ESP32) và động cơ servo (SG90) <br> - Phác thảo sơ đồ nguyên lý mạch lý thuyết chi tiết về phân phối nguồn điện (nguồn 5V ngoài) và nối đất chung (common ground) | 06/04/2026 | 06/04/2026      | Sơ đồ chân linh kiện (Component pinout diagrams) |
| 6   | - **Chuẩn bị môi trường:** <br>&emsp; + Cài đặt Arduino IDE và cấu hình ESP32 Board Manager <br>&emsp; + Tải các thư viện cần thiết (ESP32Servo, trình điều khiển camera) <br>&emsp; + Phân tích cấu trúc mã nguồn mẫu chính thức (CameraWebServer) | 06/05/2026 | 06/05/2026      | <https://docs.espressif.com/> |


### Kết quả đạt được trong Tuần 1:

* Hiểu rõ luồng vận hành cốt lõi của hệ thống Cửa nhận diện khuôn mặt: 
  * Chụp ảnh qua ESP32-CAM
  * Xác thực khuôn mặt trực tiếp trên bo mạch (Xử lý Edge AI)
  * Truyền tín hiệu đến ESP32
  * Động cơ Servo SG90 xoay chốt để mở cửa

* Hoàn thành phân tích so sánh giữa các Cloud API (AWS Rekognition) và các framework xử lý cục bộ tại biên để lựa chọn mô hình xử lý ngoại tuyến (offline) hoàn toàn với độ trễ thấp.

* Chốt danh mục vật tư kỹ thuật (BOM) mà chưa cần mua sắm thực tế, chuẩn bị danh sách các linh kiện cụ thể cần thiết.

* Phác thảo sơ đồ mạch lý thuyết toàn diện nhằm giải quyết các giới hạn về nguồn điện phần cứng, bao gồm:
  * Cấu hình chân cắm (pinout) của ESP32-CAM
  * Đường cấp nguồn 5V riêng biệt từ bên ngoài cho động cơ servo
  * Nối đất chung (common ground) để tránh nhiễu tín hiệu

* Cài đặt và chuẩn bị môi trường phát triển phần mềm trên máy tính, bao gồm:
  * Thiết lập ứng dụng Arduino IDE
  * Cài đặt Espressif ESP32 Board Manager
  * Cài đặt sẵn thư viện ESP32Servo
  * Tải các thư viện phụ thuộc của trình điều khiển camera



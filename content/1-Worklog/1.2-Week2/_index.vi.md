---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* **Thu mua phần cứng:** Tìm kiếm và chuẩn bị các linh kiện phần cứng cần thiết (ESP32, ESP32-Cam và Servo SG90) cho kiến trúc hệ thống.
* **Nghiên cứu hạ tầng điện toán đám mây:** Xây dựng nền tảng kiến thức cơ bản về các dịch vụ cốt lõi của AWS, AWS Management Console và AWS Command Line Interface (CLI).

### Các công việc cần triển khai trong tuần này:
| Ngày | Mô tả công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :---: | :---: | :--- |
|  2 | Nghiên cứu các dịch vụ đám mây AWS áp dụng cho dự án: IoT Core, Amplify, Lambda, RDS (MySQL) và API Gateway. | 08/06/2026 | 08/06/2026 |  |
|  3 | Tìm hiểu sâu về kiến trúc AWS IoT Core: giao thức MQTT, cơ chế nhắn tin pub/sub, Rule Engine, các chính sách bảo mật (security policies) và đính kèm chứng chỉ client (client certificate attachment). | 09/06/2026 | 09/06/2026 | [Tài liệu AWS IoT Core](https://aws.amazon.com/vi/iot-core/) |
|  4 | Thiết lập môi trường phát triển AWS: cấp phát tài khoản, cài đặt AWS CLI, cấu hình xác thực và thực hành cấu trúc câu lệnh. | 10/06/2026 | 10/06/2026 | [Gói miễn phí AWS (AWS Free Tier)](https://aws.amazon.com/free/) <br> [Hướng dẫn cài đặt AWS CLI](https://000011.awsstudygroup.com/vi/3-installcli/) |
|  5 | Tìm kiếm và kiểm tra các linh kiện phần cứng chính: bo mạch phát triển ESP32, module ESP32-Cam và động cơ micro servo SG90. | 11/06/2026 | 11/06/2026 |  |
|  6 | Khởi tạo kho lưu trữ firmware cục bộ và bắt đầu phát triển mã nguồn cơ bản cho máy chủ phát video trực tiếp (video streaming server) ESP32-Cam. | 12/06/2026 | 12/06/2026 | [Mã nguồn CameraWebServer](https://github.com/quannguyenlehai-cell/intership/blob/main/IoT/CameraWebServer/CameraWebServer.ino) |



### Kết quả đạt được tuần 2:

#### 1. Thiết kế hạ tầng đám mây & Kiến trúc hệ thống
* **Ánh xạ dịch vụ (Service Mapping):** Định hình kiến trúc đám mây cốt lõi phù hợp với các yêu cầu của dự án:
  * **AWS IoT Core:** Được chọn để phân phối tin nhắn MQTT độ trễ thấp và điều khiển trực tiếp phần cứng ESP32.
  * **AWS Amplify:** Được chỉ định để lưu trữ (hosting) và triển khai giao diện người dùng (frontend) ứng dụng web.
  * **AWS Lambda:** Được chọn làm công cụ tính toán không máy chủ (serverless) để xử lý logic nghiệp vụ phía backend.
  * **AWS API Gateway:** Được chọn để quản lý các đầu cuối API bảo mật, kết nối giao diện frontend với các hàm Lambda.
  * **AWS RDS (MySQL):** Được chọn làm hệ quản trị cơ sở dữ liệu quan hệ cho tầng lưu trữ dữ liệu bền vững.

#### 2. Thiết lập môi trường & Cấu hình chuỗi công cụ (Toolchain)
* **Môi trường AWS:** Đã khởi tạo và bảo mật cấu trúc tài khoản AWS Free Tier.
* **Triển khai CLI:** Cài đặt thành công chuỗi công cụ AWS CLI trên máy cục bộ và khởi tạo các giao thức xác thực bằng Access Key, Secret Key bảo mật và các khu vực mục tiêu (regional targets).
* **Xác minh vận hành:** Thành thạo các thao tác lệnh AWS CLI cơ bản, bao gồm kiểm tra cấu hình, liệt kê khu vực, truy vấn EC2 và quản lý vòng đời cặp khóa mã hóa (key-pair).

#### 3. Thu mua phần cứng & Thử nghiệm ban đầu (Đang tiến hành)
* **Thu thập linh kiện:** Đã sở hữu tất cả các linh kiện phần cứng chính (ESP32, ESP32-Cam, servo SG90) đúng tiến độ.
* **Khởi tạo Firmware:** Bắt đầu thiết lập mã nguồn cơ sở cho module CameraWebServer nhằm kiểm tra tình trạng cảm biến camera và khả năng kết nối mạng cục bộ.




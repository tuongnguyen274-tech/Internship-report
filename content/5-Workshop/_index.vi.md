---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### Tổng quan

Trong workshop thực hành này, bạn sẽ tự tay xây dựng một hệ thống truy cập cửa thông minh hoàn chỉnh, kết nối đám mây từ đầu. Bằng cách kết hợp phần cứng biên (vi điều khiển ESP32 và mô-đun camera) với cơ sở hạ tầng đám mây không máy chủ trên Amazon Web Services (AWS), người tham dự sẽ học cách thu thập dữ liệu sinh trắc học, xử lý các quy trình xác thực thời gian thực và điều khiển các thiết bị chấp hành phần cứng thông qua tin nhắn đám mây.

### Cấu trúc hội thảo & Các mô-đun học tập

#### Mô-đun 1: Lắp ráp phần cứng & Thiết lập phần mềm biên

Mục tiêu: Lắp ráp các thành phần vật lý và cấu hình vi điều khiển biên.

- Kết nối động cơ servo SG90 với bo mạch ESP32 chính bằng các chân GPIO hỗ trợ PWM.

- Nạp phần mềm cơ bản vào ESP32-Cam để thu video và lưu trữ các điểm cuối mạng cục bộ.

- Kiểm tra hoạt động của phần cứng bằng môi trường Arduino IDE.

#### Mô-đun 2: Thiết lập đám mây & Công cụ cơ sở dữ liệu

Mục tiêu: Cung cấp bộ nhớ quan hệ an toàn và logic tính toán không máy chủ trên AWS.

- Cấp phát một instance AWS RDS (MySQL) để lưu trữ hồ sơ người dùng đã đăng ký và nhật ký truy cập.

- Tạo một hàm AWS Lambda chứa logic nghiệp vụ cốt lõi cho việc ủy ​​quyền người dùng.

- Cấu hình các vai trò IAM và biến môi trường để cho phép Lambda giao tiếp an toàn với RDS.

#### Module 3: Xây dựng API REST & Bảng điều khiển Web
Mục tiêu: Kết nối giao diện người dùng frontend với các điểm cuối đám mây backend.

- Xây dựng API REST trong AWS API Gateway sử dụng tuyến proxy tham lam ({proxy+}) để gửi tải trọng yêu cầu đến AWS Lambda.

- Kích hoạt chính sách CORS (Chia sẻ tài nguyên đa nguồn gốc) cho truy cập web.

- Triển khai ứng dụng web đáp ứng trên AWS Amplify để truy cập trực tuyến toàn cầu, cho phép người dùng quét khuôn mặt, đăng ký tài khoản và kích hoạt ghi đè quản trị thủ công.

#### Module 4: Điều khiển từ đám mây đến phần cứng với AWS IoT Core
Mục tiêu: Cho phép điều khiển thiết bị vật lý từ xa theo thời gian thực thông qua MQTT.

- Cấp phát một "Thing" AWS IoT, gắn các chính sách bảo mật và cấp chứng chỉ mã hóa X.509.

- Cấu hình AWS Lambda để gửi lệnh "UNLOCK" đến AWS IoT Core sau khi xác minh khuôn mặt thành công.

- Nạp firmware máy khách MQTT vào ESP32 chính, cho phép nó nhận lệnh thời gian thực qua TLS và xoay chốt servo SG90 để mở khóa cửa.

#### Nội dung

1. [Tổng quan về hội thảo](5.1-Workshop-overview/)
2. [Điều kiện tiên quyết](5.2-Prerequisite/)
3. [Kiến trúc](5.3-Architecture/)
4. [Thực hành](5.4-Practice/)
5. [Kiểm tra](5.6-Testing/)
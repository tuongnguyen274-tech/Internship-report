---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu Tuần 6
* **Tối ưu hóa cơ sở hạ tầng đám mây (Cloud Infrastructure Optimization):** Hoàn thành tích hợp AWS IoT Core để cho phép điều khiển từ xa ESP32 qua giao thức MQTT an toàn và thiết lập đồng bộ hóa cơ sở dữ liệu người dùng.
* **Triển khai kiến trúc Serverless (Serverless Architecture Deployment):** Cấu hình môi trường thực thi (runtime), các đường ống định tuyến API (gateway routing pipelines) và logic nghiệp vụ cốt lõi (core business logic) trong AWS Lambda.

### Các công việc thực hiện trong tuần

| Ngày | Mô tả công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :---: | :---: | :--- |
| 2 | Sửa lỗi (debug) và ổn định kết nối backend Node.js cục bộ với MQTT broker của AWS IoT Core. | 06/07/2026 | 06/07/2026 | [Backend Server Script](https://github.com/quannguyenlehai-cell/intership/blob/main/server/index.mjs) |
| 3 | Khởi tạo môi trường cơ sở dữ liệu MySQL và triển khai logic truy cập dữ liệu cốt lõi bên trong các hàm AWS Lambda. | 07/07/2026 | 07/07/2026 | Nguồn nội bộ |
| 4 | Cấu hình định tuyến (routing), các giai đoạn triển khai (deployment stages) và tích hợp trình kích hoạt (trigger) cho AWS Lambda thông qua AWS API Gateway. | 08/07/2026 | 08/07/2026 | Nguồn nội bộ |
| 5 | Khắc phục sự cố và xử lý các ngoại lệ về mạng full-stack, định tuyến và kiểm soát truy cập giữa tầng frontend và backend. | 09/07/2026 | 09/07/2026 | Nguồn nội bộ |
| 6 | Cấu trúc các yêu cầu/phản hồi phương thức HTTP và cấu hình chính sách Chia sẻ tài nguyên giữa các nguồn gốc (CORS) để frontend truy cập an toàn. | 10/07/2026 | 10/07/2026 | Nguồn nội bộ |

---

### Kết quả đạt được trong Tuần 6

#### 1. Logic Serverless & Tích hợp Cơ sở dữ liệu
* **Cấu hình tầng cơ sở dữ liệu (Database Layer Configuration):** Khởi tạo hạ tầng dữ liệu quan hệ MySQL và thiết lập quy trình quản lý kết nối (connection pooling) an toàn trong tầng serverless.
* **Triển khai AWS Lambda (AWS Lambda Implementation):** Triển khai thành công logic nghiệp vụ backend lên các hàm AWS Lambda, cho phép truy vấn cơ sở dữ liệu qua mã lập trình và thực hiện các quy trình đồng bộ hóa tự động với AWS IoT Core.
* **Kết nối Broker (Broker Connectivity):** Khắc phục các lỗi trong môi trường Node.js cục bộ nhằm đảm bảo khả năng phát lệnh đáng tin cậy, độ trễ thấp từ tầng backend trực tiếp đến phần cứng thông qua giao thức MQTT.

#### 2. Quản lý API & Bảo mật Full-Stack
* **Định tuyến API Gateway (API Gateway Routing):** Xây dựng điểm truy cập RESTful có cấu trúc bằng AWS API Gateway, ánh xạ thành công các điểm cuối (endpoints) từ client đến các trình xử lý AWS Lambda tương ứng ở backend.
* **Cấu hình CORS & Vòng đời (CORS & Lifecycle Configuration):** Thiết lập các quy tắc Chia sẻ tài nguyên giữa các nguồn gốc (CORS) chặt chẽ trên toàn bộ tài nguyên API Gateway, xác thực các tiêu đề yêu cầu (request headers) từ frontend đến backend và xử lý kiểm tra sơ bộ (preflight).
* **Tối ưu hóa kết nối mạng (Network Modernization):** Chẩn đoán và xử lý thành công các nút thắt mạng giữa các tầng, chuẩn hóa cấu trúc yêu cầu mô hình ở frontend và định dạng phản hồi ở backend nhằm đảm bảo luồng dữ liệu đo đạc từ xa (telemetry flow) ổn định từ đầu đến cuối (end-to-end).



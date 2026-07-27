---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
# ĐỒ ÁN THỰC TẬP: HỆ THỐNG MỞ CỬA BẰNG KHUÔN MẶT (ESP32-CAM + AWS LAMBDA)

Hệ thống kiểm soát cửa ra vào thông minh kết hợp giữa phần cứng AI giá rẻ (**Edge-AI**) và hạ tầng Đám mây (**AWS Serverless**).

## 1. Ý tưởng bắt đầu từ đâu? (Vấn đề thực tế)

Trong thực tế, các giải pháp khóa cửa hiện tại đều có những nhược điểm riêng:

* **Chìa khóa cơ & Thẻ từ:** Dễ mất, dễ quên hoặc bị copy trái phép.
* **Mật khẩu PIN:** Dễ bị nhìn lén hoặc chia sẻ ngoài ý muốn.
* **Khóa quét mặt trên đám mây:** Thường đắt đỏ, bị trễ do phụ thuộc băng thông truyền tải hình ảnh lên server.

**Mục tiêu dự án:** 
Tạo ra một hệ thống quét mặt mở cửa siêu rẻ (tiền phần cứng chưa tới **400.000 VNĐ**), độ trễ cực thấp, đồng thời hỗ trợ quản trị viên quản lý lịch sử ra vào từ xa qua giao diện Web.

---

## 2. Hệ thống này hoạt động như thế nào?

Mô hình được chia làm 2 phần chính hoạt động ăn ý với nhau:

### A. Tại thiết bị ở cửa (ESP32-CAM)
* Mọi việc nhận diện khuôn mặt đều được xử lý trực tiếp ngay trên con chip ESP32-CAM (Edge-AI).
* **Quy trình:** Người đứng trước camera $
ightarrow$ Chip quét mặt $
ightarrow$ Khớp dữ liệu $
ightarrow$ Khóa mở ngay lập tức (độ trễ chưa tới $0.5$ giây).

### B. Tại Đám mây (Hạ tầng AWS)
Sau khi cửa mở thành công, thiết bị mới gửi "báo cáo" lên đám mây để lưu vết lịch sử ra vào:

* **AWS IoT Core:** Nhận tin nhắn báo cáo từ thiết bị gửi lên.
* **AWS Lambda:** Tự động "thức dậy" nhận dữ liệu và lưu lịch sử ra vào vào cơ sở dữ liệu (**Amazon RDS**).
* **AWS Amplify & API Gateway:** Tạo một trang Web cho quản trị viên. Admin có thể ngồi từ xa:
  * Xem ai vừa ra vào theo thời gian thực.
  * Thêm/Xóa người dùng mới.
  * Bấm nút mở cửa từ xa.

---

## 3. Những điểm "xịn xò" đúc kết từ dự án

* **Độ trễ siêu thấp ($< 500	ext{ms}$):** Việc xử lý AI ngay tại thiết bị đầu cuối giúp kích hoạt khóa mở ngay lập tức mà không phải chờ phản hồi từ Server.
* **Giá thành siêu hạt dẻ:** Chi phí phần cứng cho một cụm cửa (ESP32-CAM, động cơ servo, mạch...) chỉ khoảng **17 USD (~400.000 VNĐ)** — rẻ hơn 90% so với các bộ khóa thông minh thương mại.
* **Tối ưu chi phí Cloud:** Nhờ dùng backend Serverless (**AWS Lambda**, **AWS IoT Core**...), hệ thống tự động mở rộng khi có người dùng và gần như không tốn chi phí khi nhàn rỗi.

---

## 4. Lời kết

Chỉ sau 2 tháng ngắn ngủi, từ một sinh viên còn bỡ ngỡ với khái niệm Cloud, việc tự tay xây dựng một dự án kết hợp giữa **IoT (ESP32-CAM)** và **Serverless (AWS Lambda)** đã giúp mình hiểu hơn rất nhiều về kiến trúc hệ thống thực tế.

[Link Facebook](https://www.facebook.com/groups/awsstudygroupfcj/)
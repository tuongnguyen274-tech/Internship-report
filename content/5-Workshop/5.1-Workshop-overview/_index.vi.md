---
title : "Giới thiệu"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

### Lý do nên chọn dịch vụ AWS

#### AWS Amplify (Máy chủ Frontend)

- CI/CD tự động: Kết nối trực tiếp với kho lưu trữ Git để tự động xây dựng và triển khai bảng điều khiển web mỗi khi mã được cập nhật.

- Phân phối toàn cầu: Phục vụ giao diện người dùng thông qua Mạng phân phối nội dung (CDN) toàn cầu của Amazon CloudFront, cung cấp quyền truy cập web độ trễ thấp cho các điều khiển quản trị và đăng ký người dùng.

- SSL được quản lý: Tự động xử lý chứng chỉ HTTPS để truy cập web an toàn mà không cần quản lý máy chủ web phức tạp.

#### AWS API Gateway (Quản lý API)

Kiến trúc tách rời: Hoạt động như một điểm truy cập an toàn, được quản lý để định tuyến lưu lượng HTTP một cách gọn gàng giữa giao diện người dùng và các chức năng điện toán phi máy chủ ở phía máy chủ.

Proxy tham lam & Xử lý CORS: Đơn giản hóa việc thiết lập điểm cuối thông qua định tuyến proxy linh hoạt ({proxy+}) và cung cấp quản lý CORS preflight gốc để bảo vệ các yêu cầu trình duyệt khác nguồn gốc.

Bảo mật & Giới hạn tích hợp: Bảo vệ các dịch vụ phụ trợ khỏi các đột biến lưu lượng truy cập hoặc các cuộc tấn công từ chối dịch vụ (DoS).

#### AWS Lambda (Điện toán phi máy chủ)

- Hướng sự kiện & Tiết kiệm chi phí: Chỉ thực thi logic nghiệp vụ và xác minh khi được kích hoạt bởi các cuộc gọi API đến, loại bỏ chi phí và gánh nặng bảo trì của việc vận hành các máy chủ chuyên dụng 24/7.

- Tích hợp SDK liền mạch: Kết nối trực tiếp với AWS RDS để truy vấn cơ sở dữ liệu và AWS IoT Data Plane SDK để xuất bản các lệnh phần cứng theo thời gian thực.

- Khả năng mở rộng: Xử lý các đột biến về yêu cầu truy cập một cách dễ dàng bằng cách tự động mở rộng dung lượng điện toán theo yêu cầu.
---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu Tuần 8:

* **Quản lý Backend & Cơ sở dữ liệu:** Giải quyết các sự cố tích hợp backend giữa Lambda cơ sở dữ liệu web và bộ xử lý MQTT IoT Core; sửa các lỗi đăng ký người dùng trong bảng cơ sở dữ liệu hợp nhất để phân biệt các yêu cầu dành cho quản trị viên (admin) và khách (guest).
* **Độ tương thích Giao diện người dùng (Frontend Responsiveness):** Tối ưu hóa bố cục giao diện (UI) cho các màn hình kích thước nhỏ nhằm khắc phục sự cố co giãn thanh điều hướng (navbar) và nén văn bản trong bảng.
* **Chuyển đổi sang Lưu trữ Đám mây (Cloud Hosting Migration):** Chuyển đổi giao diện người dùng tĩnh (static client interface) từ môi trường cục bộ sang kiến trúc truy cập Internet sử dụng AWS Amplify.
* **Tích hợp API Full-Stack:** Thiết lập giao tiếp bảo mật, độc lập (decoupled) giữa tầng frontend được lưu trữ trên mây và backend serverless thông qua REST API Gateway.

### Các nhiệm vụ thực hiện trong tuần này:
| Ngày | Mô tả Nhiệm vụ | Ngày Bắt đầu | Ngày Hoàn thành | Tài liệu Tham khảo |
| :---: | :--- | :---: | :---: | :--- |
| **2** | **Chuyển đổi Backend Kép & Triển khai Đám mây:**<br>• Thử nghiệm hợp nhất Lambda web/cơ sở dữ liệu với bộ xử lý MQTT IoT cục bộ; chuyển hướng sang tách biệt MQTT trên kiến trúc đám mây riêng.<br>• Tái cấu trúc các tài nguyên tĩnh frontend cũ và thực hiện triển khai đám mây qua AWS Amplify. | 07/20/2026 | 07/27/2026 | Tài liệu AWS IoT Core / AWS Amplify |
| **3** | **Tích hợp API Gateway REST:**<br>• Thiết lập logic giao diện rõ ràng giữa frontend và backend bằng các endpoint REST của AWS API Gateway nhằm bảo mật giao tiếp backend độc lập. | 07/21/2026 | 07/28/2026 | Hướng dẫn Lập trình viên AWS API Gateway |
| **4** | **Xử lý Proxy Tự do (Greedy Proxy) & Điều hướng Tuyến:**<br>• Cấu hình các phương thức tích hợp `POST` chuẩn và triển khai định tuyến proxy tự do (`{proxy+}`) để điều phối yêu cầu động đến AWS Lambda. | 07/22/2026 | 07/29/2026 | Tài liệu Proxy AWS API Gateway |
| **5** | **Vá lỗi Danh mục Người dùng & Chẩn đoán Mạng:**<br>• Chỉnh sửa logic định tuyến đăng ký để kích hoạt các yêu cầu mật khẩu theo điều kiện dựa trên vai trò bảo mật.<br>• Chẩn đoán, truy vết và khắc phục các bất thường về mạng, tham số thời gian chờ (timeout) và các nghẽn giao tiếp trên toàn bộ hệ thống. | 07/23/2026 | 07/30/2026 | Câu lệnh Điều kiện Python / Tài liệu CloudWatch |
| **6** | **Tối ưu hóa Giao diện Di động & Bảo mật CORS:**<br>• Sửa lỗi nén bố cục gây thu nhỏ thanh điều hướng; thêm khung chứa cuộn ngang (`overflow-x: auto`) cho các bảng danh mục người dùng.<br>• Cấu trúc các tiêu đề/tải trọng yêu cầu (payload/header) hợp nhất và áp dụng quy tắc Chia sẻ Tài nguyên Khác Nguồn (CORS). | 07/24/2026 | 07/31/2026 | Thiết kế Web MDN / Tiêu chuẩn W3C CORS |

### Thành tựu Tuần 8:

* **Cô lập Backend & An toàn Mã nguồn:** Triển khai module MQTT lên một thể hiện (instance) đám mây riêng biệt sau khi các nỗ lực hợp nhất giao tiếp cục bộ thất bại. Duy trì hàm `handle_remote_override` chưa sử dụng trong khối mã hoạt động như một biện pháp an toàn chống đứt gãy đường ống tích hợp (pipeline).
* **Sửa lỗi Danh mục Người dùng:** Giải quyết lỗi xác thực khiến hành khách thông thường không thể đăng ký do các yêu cầu mật khẩu toàn cục trong bảng cơ sở dữ liệu hợp nhất. Tái cấu trúc (refactor) logic để chỉ áp dụng các quy tắc mật khẩu nghiêm ngặt dành riêng cho vai trò quản trị viên.

* **Co giãn Thanh điều hướng (Navbar Scaling):** Sửa lại phép tính bố cục để ngăn thanh điều hướng bị nén quá mức trên màn hình di động.
* **Kiểm soát Tràn hiển thị (Overflow Controls):** Áp dụng `overflow-x: auto` riêng cho khung chứa bảng Danh mục Người dùng Hợp lệ, cung cấp thanh cuộn ngang cho dữ liệu rộng trong khi vẫn giữ nguyên tính ổn định của trang.

* **Chuyển đổi sang Amplify:** Tách rời giao diện người dùng khỏi môi trường cục bộ, triển khai ứng dụng lên các tầng sản xuất (production) thông qua AWS Amplify để đạt khả năng sẵn sàng cao và truy cập toàn cầu.
* **Tính Ổn định của Bản dựng (Build Stability):** Cấu hình các tham số triển khai cơ sở, đảm bảo tải đúng các tuyến tài nguyên, liên kết tệp tĩnh và kịch bản (script) trên miền công cộng.

* **Kiến trúc Proxy Tự do (Greedy Proxy Architecture):** Khởi tạo tích hợp proxy AWS API Gateway (định tuyến `{proxy+}`), cho phép tất cả yêu cầu từ client đến một endpoint hợp nhất và điều hướng vào tầng tính toán AWS Lambda.
* **Tầng Truyền tải Dữ liệu (Data Transport Layer):** Triển khai các phương thức gửi `POST` bảo mật, cho phép truyền tải tin cậy các thông tin xác thực truy cập, tải trọng dữ liệu hình ảnh và các lệnh quản trị.

* **Xử lý Sự cố CORS:** Vô hiệu hóa các rào cản bảo mật trình duyệt bằng cách thiết lập các quy tắc Chia sẻ Tài nguyên Khác Nguồn (CORS) trên API Gateway, xác thực cả các tùy chọn preflight và khớp tiêu đề tên miền cụ thể.
* **Đồng bộ hóa Đường ống Tích hợp (Pipeline Synchronization):** Chuẩn hóa schema yêu cầu từ frontend và tham số phản hồi từ backend nhằm loại bỏ các sai lệch tích hợp và duy trì các vòng giao tiếp API có độ trễ thấp.


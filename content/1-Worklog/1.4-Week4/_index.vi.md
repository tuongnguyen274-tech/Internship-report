---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:

* Bắt đầu phác thảo bố cục cấu trúc trên các tệp ứng dụng bằng các thuộc tính CSS tùy chỉnh, đơn giản.
* Xây dựng các biểu mẫu HTML cơ bản cho việc nhập liệu thử nghiệm quản trị (login.html, register_admin.html) mà không cần kiểm soát truy cập.
* Lập thiết kế sơ bộ cho lưới theo dõi người dùng và khung phát video cơ bản, lên kế hoạch cho các điều chỉnh bố cục mở rộng.

### Các công việc thực hiện trong tuần này:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2 | - Phác thảo khung bố cục ứng dụng bằng các biến CSS sơ bộ <br> - Soạn thảo các biểu mẫu HTML cơ bản cho login.html và register_admin.html | 06/22/2026 | 06/22/2026 | Tài liệu tham khảo Biến CSS |
| 3 | - Liên kết các đường dẫn điều hướng cơ bản, không hạn chế trên các trang mẫu thử cục bộ để kiểm tra định tuyến người dùng | 06/23/2026 | 06/23/2026 | Hướng dẫn về Liên kết HTML |
| 4 | - Xây dựng bảng bố cục cơ sở bên trong dashboard.html <br> - Lập trình một đoạn mã đơn giản để thêm các chuỗi văn bản thô vào thanh điều hướng nhằm kiểm tra tên người dùng | 06/24/2026 | 06/24/2026 | Thao tác DOM với JavaScript |
| 5-6 | - **Phác thảo khung giao diện (Wireframing):** <br>&emsp; + Xây dựng các khung chứa phần tử video trống cho enroll.html <br>&emsp; + Xây dựng ranh giới bố cục cho giao diện thiết bị đầu cuối khóa công khai index.html | 06/25/2026 | 06/26/2026 | Hướng dẫn Phần tử Media trên MDN |

### Kết quả đạt được trong Tuần 4:

* Khởi tạo cấu trúc bố cục nền tảng:
  * Cấu hình các biến hệ thống toàn cục cơ bản cho định dạng nền, viền và thẻ (card).
  * Thiết kế các thành phần bảng cơ bản nhằm hiển thị các mục dữ liệu thô trong các mốc phát triển sau.
  * Tạo các trường bố cục biểu mẫu linh hoạt cho phép nhập dữ liệu văn bản tự do mà không cần xác thực phức tạp tại chỗ.

* Triển khai quy trình điều hướng cơ sở:
  * Thiết lập các luồng truy cập mở tạm thời giữa các giao diện hệ thống, cho phép điều hướng ngay lập tức mà không bị chặn xác thực.
  * Ánh xạ các trình xử lý văn bản tạm thời để đọc dữ liệu chuỗi thô nhằm hiển thị tên người dùng thử nghiệm cơ bản trực tiếp trên thanh điều hướng của ứng dụng.

* Phác thảo các khung xem camera cốt lõi:
  * Đặt các thành phần video HTML5 tiêu chuẩn làm vị trí chờ (placeholder) cho các luồng truyền trực tiếp sắp tới.
  * Gặp phải các lỗi ban đầu về căn chỉnh và kích thước khung chứa khi bố trí các trường truyền thông trên trang web linh hoạt (responsive).



---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:

* Tích hợp băm mật khẩu phía máy chủ (server-side password hashing) và các tham số xác thực phức tạp cho thông tin đăng nhập của quản trị viên.
* Triển khai các quy trình tự động đăng xuất do hết giờ phiên (session timeout) và dọn dẹp phiên làm việc nhằm ngăn chặn truy cập trái phép.
* Tối ưu hóa cấu trúc bố cục CSS và căn chỉnh các phần tử trên tất cả các biểu mẫu web của hệ thống.

### Các nhiệm vụ thực hiện trong tuần:
| Thứ | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Tinh chỉnh bố cục CSS và sửa lỗi căn giữa flexbox trên login.html, register_admin.html và dashboard | 13/07/2026 | 13/07/2026 | Hướng dẫn CSS Flexbox & Grid |
| 3-4 | - Tích hợp băm mật khẩu (Password Hashing Integration): <br>&emsp; + Cập nhật backend Python với các module băm mật khẩu PBKDF2-HMAC-SHA256 <br>&emsp; + Triển khai các quy tắc xác thực độ mạnh mật khẩu dựa trên Regex, bắt buộc yêu cầu ký tự phức tạp khi đăng ký tài khoản quản trị | 14/07/2026 | 15/07/2026 | Tài liệu Python Hashlib |
| 5 | - Thiết lập theo dõi sessionStorage qua YOLO_ADMIN_SECURE_TOKEN_2026 <br> - Lập trình script tự động đăng xuất để xóa token khi không hoạt động hoặc khi đóng cửa sổ trình duyệt | 16/07/2026 | 16/07/2026 | Các API JavaScript Web Storage |
| 6 | - Xây dựng tính năng ẩn/hiện mật khẩu (nút bật/tắt biểu tượng con mắt) <br> - Sửa lỗi dịch chuyển bố cục (layout shifting) do thay đổi DOM động | 17/07/2026 | 17/07/2026 | Thuộc tính phần tử DOM |


### Kết quả đạt được trong Tuần 7:

* Triển khai các cơ chế kiểm soát mã hóa vững chắc:
  * Thay thế việc lưu trữ mật khẩu dạng văn bản thuần (cleartext) trong cơ sở dữ liệu bằng quy trình băm PBKDF2 an toàn, sử dụng salt hex 16-byte và 100.000 vòng lặp (rounds).
  * Áp dụng các quy tắc phức tạp về mật khẩu nghiêm ngặt ở phía backend, yêu cầu tối thiểu 8 ký tự bao gồm chữ hoa, chữ thường, chữ số và ký tự đặc biệt.

* Thắt chặt truy cập quản trị & quy trình phiên làm việc:
  * Bảo vệ các trang xem quản trị nội bộ bằng việc kiểm tra xác thực trạng thái lưu trữ của YOLO_ADMIN_SECURE_TOKEN_2026.
  * Cấu hình script đăng xuất tự động nhằm hủy các token phiên đang hoạt động khi thoát trang hoặc đóng tab.

* Tối ưu hóa bố cục thành phần UI & Căn chỉnh giao diện:
  * Căn chỉnh lại các phần tử flex tổng thể để giữ cho các biểu mẫu tương tác luôn nằm ở trung tâm trên nhiều kích thước màn hình khác nhau.
  * Tích hợp tiện ích bật/tắt hiển thị mật khẩu bằng JavaScript để ẩn/hiện các trường mật khẩu một cách an toàn mà không làm dịch chuyển các phần tử DOM xung quanh.
  * Sửa lỗi tràn chiều ngang (horizontal overflow) của bảng bên trong lưới nhật ký sự kiện (event log grid) tại màn hình dashboard chính.



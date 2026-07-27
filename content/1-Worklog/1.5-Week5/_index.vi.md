---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:

* Hoàn thiện khung hình video và lớp phủ bố cục (canvas overlays)
* Triển khai sơ đồ cơ sở dữ liệu Amazon RDS MySQL được quản lý bởi hàm Python AWS Lambda trung tâm.
* Xác minh giao tiếp cơ bản toàn trình (end-to-end) sử dụng các tham số văn bản thuần không mã hóa (unhashed cleartext).

### Các nhiệm vụ thực hiện trong tuần này:
| Thứ | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2-3 | - **Điều chỉnh Bố cục Truyền thông (Media Layout):** <br>&emsp; + Hoàn thành công việc bố cục cơ bản cho enroll.html và index.html <br>&emsp; + Căn chỉnh ranh giới lớp phủ HTML5 canvas trên các khung chứa luồng video trực tiếp | 06/29/2026 | 06/30/2026 | HTML Canvas API |
| 4 | - Kết nối các đầu vào biểu mẫu web cơ bản với các quy trình gọi API bất đồng bộ (fetch) mà không có lớp bảo mật | 07/01/2026 | 07/01/2026 | JavaScript Fetch API |
| 5 | - Triển khai công cụ AWS Lambda chạy bằng Python để khởi tạo các bảng cơ sở dữ liệu | 07/02/2026 | 07/02/2026 | Tài liệu PyMySQL Driver cho Python |
| 6 | - Xây dựng vòng lặp kiểm thử truy vấn chu kỳ 2500ms bên trong index.html <br> - Kiểm thử việc truyền dữ liệu nhập sử dụng các hàng văn bản thuần (cleartext) | 07/03/2026 | 07/03/2026 | Luồng định tuyến hành động AWS Lambda |

### Kết quả đạt được trong Tuần 5:

* Hoàn thành Giao diện Web Đa trang Cơ bản:
  * Hoàn thiện cấu trúc bố cục cho toàn bộ 5 tệp mẫu giao diện (frontend prototype) cốt lõi để chuẩn bị cho các tích hợp tương lai.
  * Khắc phục sự lệch căn chỉnh canvas co giãn (responsive) trên các khung hiển thị video đang hoạt động.

* Triển khai Cụm Dịch vụ Cốt lõi Cơ sở Dữ liệu Quan hệ:
  * Lập trình hàm xử lý Python AWS Lambda để khởi tạo các bảng theo dõi chính trong Amazon RDS MySQL.
  * Sử dụng cấu hình truy vấn nội bộ (COALESCE) để tự động tái sử dụng các ID hàng khóa chính đã xóa.

* Xác minh Các Đường truyền Giao tiếp Toàn trình (End-to-End):
  * Đẩy các dữ liệu văn bản không mã hóa từ biểu mẫu web cơ bản trực tiếp vào các hàng cơ sở dữ liệu đám mây để xác minh đường truyền dữ liệu (fetch).
  * Kiểm tra hợp lệ logic chèn dữ liệu bảng danh mục người dùng và xác nhận việc thực thi ổn định vòng lặp trạm kiosk 2500ms.

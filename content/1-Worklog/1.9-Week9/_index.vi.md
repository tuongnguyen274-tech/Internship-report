---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
### Mục tiêu Tuần 9
* **Kiểm thử Phần cứng & Thiết bị Biên:** Thực hiện kiểm thử tích hợp toàn trình (end-to-end) cho vi điều khiển ESP32 thông qua các khung truyền MQTT từ xa và đánh giá độ chính xác của mô hình nhận diện khuôn mặt thời gian thực trên thiết bị biên.
* **Xác thực Full-Stack & Dữ liệu Từ xa (Telemetry):** Kiểm thử tính năng điều khiển ghi đè (override) đóng/mở cửa trên giao diện web và kiểm tra quy trình đăng ký người dùng xuống lớp lưu trữ dữ liệu MySQL.
* **Báo cáo Tiến độ Tổng hợp:** Tổng hợp các cột mốc lịch sử của dự án thành các báo cáo có cấu trúc từ Tuần 1 đến Tuần 12 và các sự kiện kỹ thuật đã tham gia.
* **Sản phẩm Bàn giao & Hoàn tất Dự án:** Hoàn thiện đề xuất dự án (proposal), xuất bản 3 bài viết blog kỹ thuật, tổ chức một buổi workshop kỹ thuật, hoàn thành tự đánh giá và thực hiện các buổi ghi nhận phản hồi.

### Các công việc đã thực hiện trong tuần

| Ngày | Mô tả công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :--- | :--- | :---: | :---: | :--- |
| 2 | - Thực hiện kiểm thử tích hợp trên phần cứng ESP32 thông qua chuỗi lệnh MQTT từ xa trên AWS IoT Core.<br>- Lập báo cáo tiến độ dự án cho Tuần 1 đến Tuần 3.<br>- Hoàn thiện và hoàn tất Đề xuất dự án tổng thể. | 27/07/2026 | 27/07/2026 | |
| 3 | - Đánh giá hiệu năng (benchmark) quy trình nhận diện khuôn mặt trên thiết bị biên để xác thực khả năng kích hoạt chốt cửa tin cậy.<br>- Lập báo cáo tiến độ dự án cho Tuần 4 đến Tuần 6.<br>- Viết và xuất bản 3 bài viết Blog kỹ thuật. | 28/07/2026 | 28/07/2026 | |
| 4 | - Chạy các bài kiểm thử telemetry để thực hiện thao tác khóa/mở khóa từ xa từ ứng dụng web.<br>- Lập báo cáo tiến độ dự án cho Tuần 7 đến Tuần 9.<br>- Chuẩn bị nội dung và chủ trì buổi Workshop kỹ thuật. | 29/07/2026 | 29/07/2026 | |
| 5 | - Xác thực quy trình đăng ký người dùng và kiểm tra tính toàn vẹn lưu trữ dữ liệu xuống lớp MySQL.<br>- Hoàn thành tài liệu Tự đánh giá cuối kỳ. | 30/07/2026 | 30/07/2026 | |
| 6 | - Thực hiện UAT trên các tính năng quản trị (ghi đè thủ công, xoay vòng thông tin xác thực, trạng thái phiên làm việc).<br>- Lập báo cáo tổng kết cho 3 sự kiện kỹ thuật đã tham gia.<br>- Tổ chức buổi Chia sẻ kiến thức và thu thập Phản hồi từ giảng viên hướng dẫn/nhóm. | 31/07/2026 | 31/07/2026 | |

---

### Kết quả đạt được trong Tuần 9

* **Tích hợp Tầm nhìn Máy tính & Thiết bị Biên:** Kiểm thử thành công khả năng kích hoạt vi điều khiển ESP32 qua AWS IoT Core mà không bị mất gói tin MQTT nào, đồng thời xác thực khả năng kích hoạt chốt cửa bằng nhận diện khuôn mặt thời gian thực với độ chính xác cao.
* **Điều khiển Giao diện & Lưu trữ Dữ liệu:** Đạt được sự xác thực telemetry full-stack cho việc ghi đè khóa/mở khóa từ xa qua giao diện web và xác minh tính toàn vẹn lưu trữ dữ liệu trên lớp MySQL.
* **Quyền Kiểm soát Quản trị:** Hoàn thành UAT cho các chế độ ghi đè thủ công của quản trị viên, chu kỳ xoay vòng thông tin xác thực và các cơ chế an toàn xử lý phiên làm việc.

* **Kiểm toán Tiến độ Lịch sử:** Hoàn thành 4 báo cáo tiến độ hệ thống hóa các cột mốc dự án từ Tuần 1 đến Tuần 12.
* **Sản phẩm Bàn giao Core:** Xuất bản 3 bài viết blog kỹ thuật tóm tắt các bài học kinh nghiệm của dự án và hoàn thiện đề xuất dự án tổng thể.

* **Lan tỏa Sự kiện & Workshop:** Tóm tắt các bài học chính từ 3 sự kiện kỹ thuật đã tham dự và chủ trì thành công một buổi workshop kỹ thuật.
* **Tự Đánh giá & Xem xét:** Hoàn thành toàn bộ tài liệu tự đánh giá và thu thập các phản hồi mang tính xây dựng trong buổi chia sẻ kiến thức với nhóm và giảng viên hướng dẫn.
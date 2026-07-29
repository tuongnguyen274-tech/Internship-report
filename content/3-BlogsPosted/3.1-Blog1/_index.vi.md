---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# TỰ HỌC AWS LAMBDA CHO NGƯỜI MỚI BẮT ĐẦU

## 1. Mở đầu

Đối với người mới nhập môn Điện toán đám mây (Cloud Computing), việc tiếp cận hàng trăm dịch vụ cùng thuật ngữ chuyên ngành phức tạp thường gây ra cảm giác ngợp và khó khăn. Tuy nhiên, qua quá trình thực hành trực tiếp với **AWS Lambda**, các khái niệm cốt lõi của mô hình Cloud dần trở nên trực quan và dễ tiếp cận hơn.

---

## 2. Các đặc tính cốt lõi của AWS Lambda

Dựa trên trải nghiệm thực tế, AWS Lambda mang lại 3 ưu điểm quan trọng giúp tối ưu hóa quá trình phát triển ứng dụng:

### 2.1. Mô hình Serverless (Không cần quản lý máy chủ)
* **Khác biệt so với truyền thống:** Khi làm đồ án hoặc bài tập lớn, lập trình viên thường phải tự khởi chạy và duy trì server local (Node.js, Python,...) liên tục 24/7 để chờ nhận yêu cầu.
* **Cơ chế của AWS Lambda:** Người dùng chỉ cần tải mã nguồn (code) lên đám mây. AWS sẽ tự động đảm nhận toàn bộ hạ tầng bên dưới bao gồm: cài đặt hệ điều hành, vá lỗi hệ thống và tự động mở rộng (scaling) khi tải tăng cao.

### 2.2. Cơ chế thực thi theo sự kiện (Event-driven Architecture)
Hàm Lambda không chạy liên tục mà chỉ "thức dậy" khi nhận được tín hiệu kích hoạt (Trigger):
* **Các dạng Trigger phổ biến:**
  * Có file ảnh mới được tải lên hệ thống.
  * Người dùng thực hiện thao tác click trên giao diện Web/App.
  * Dữ liệu mới được ghi hoặc cập nhật vào cơ sở dữ liệu.
* **Chu kỳ hoạt động:** Khi có sự kiện -> Lambda kích hoạt code -> Trả về kết quả -> Tự động giải phóng tài nguyên (tắt hàm).

### 2.3. Tối ưu hóa chi phí
* **Mô hình tính phí:** Chỉ tính tiền dựa trên số mili-giây mà mã nguồn thực sự hoạt động.
* **Tối ưu dự án sinh viên:** Khi ứng dụng không có lưu lượng truy cập, chi phí phát sinh là **0 đồng**. Kết hợp với gói **AWS Free Tier**, người học có thể thoải mái thử nghiệm đồ án mà không lo bị tính phí ngoài ý muốn.

---

## 3. Bài học kinh nghiệm thực tế (Best Practices)

| Sai lầm ban đầu | Giải pháp & Cách khắc phục |
| :--- | :--- |
| Đưa toàn bộ ứng dụng Backend lớn (Monolithic) vào một hàm Lambda duy nhất, khiến code xử lý chậm và khó bảo trì. | **Chia nhỏ công việc (Microservices / Single Responsibility):** Tách ứng dụng thành các hàm nhỏ đảm nhận duy nhất một chức năng (ví dụ: 1 hàm đăng ký tài khoản, 1 hàm lưu dữ liệu). |

> **Kinh nghiệm rút ra:** Việc chia nhỏ chức năng giúp hệ thống hoạt động linh hoạt, dễ khoanh vùng lỗi và bảo trì thuận tiện hơn trong quá trình phát triển.

---

## 4. Kết luận

AWS Lambda là điểm khởi đầu lý tưởng cho sinh viên và người mới học Cloud nhờ loại bỏ rào cản về quản lý hạ tầng máy chủ và mạng. Người dùng chỉ cần tập trung vào việc viết đúng logic nghiệp vụ của mã nguồn là có thể triển khai sản phẩm thành công.

[Link Facebook](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2225735151524778/?rdid=LGtwaQotLkeDI1a7#)
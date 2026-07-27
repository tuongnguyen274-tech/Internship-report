---
title: "Event 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---
# Báo Cáo Tổng kết: "Event GameDay 8 đội tranh hùng"

### Mục Tiêu Sự Kiện

- Kiểm tra kiến thức thực hành và lý thuyết của người tham gia về các dịch vụ đám mây cốt lõi của AWS.
- Thúc đẩy sự hợp tác trong đội, đạt được sự đồng thuận nhanh chóng và đưa ra quyết định chiến thuật dưới áp lực thời gian.
- Nhận diện các hiểu lầm phổ biến về kiến trúc và lỗ hổng kiến thức thông qua việc giải quyết vấn đề mang tính cạnh tranh.
- Khuyến khích sự tham gia tương tác của cộng đồng thông qua giải đấu loại trực tiếp (bracket tournament) được game hóa, đối đầu trực tiếp.

### Thể Lệ & Cơ Chế Sự Kiện
Sự kiện được tổ chức theo hình thức thi đấu loại trực tiếp gồm 8 đội, được thiết kế để mô phỏng việc đưa ra quyết định nhanh chóng trên điện toán đám mây theo hình thức đối đầu trực tiếp:

*   **Hệ Thống Bảng Đấu (Bracket System)**: 8 đội bước vào cây thi đấu loại trực tiếp (Tứ kết → Bán kết → Chung kết).
*   **Các Trận Đối Đầu Trực Tiếp**: Trong mỗi vòng, 2 đội đối đầu trực tiếp với nhau, trả lời cùng một bộ câu hỏi giống hệt nhau.
*   **Cơ Chế Tính Điểm**:
    *   **Câu Trả Lời Đúng**: Nhận điểm cộng (+).
    *   **Câu Trả Lời Sai**: Bị trừ điểm (-).
    *   **Đội Chiến Thắng Trận Đấu**: Đội có tổng điểm ròng (net score) cao hơn vào cuối vòng đấu sẽ giành quyền vào vòng tiếp theo của bảng đấu.
*   **Phạm Vi Câu Hỏi**: Trải dài từ các dịch vụ nền tảng (IAM, EC2, S3, VPC) đến các mô hình thiết kế đám mây nâng cao (Serverless, Bảo mật, Tối ưu hóa chi phí và Khôi phục sau thảm họa - Disaster Recovery).
---

## Những Điểm Nổi Bật Chính
### 1. Tính Điểm Áp Lực Cao & Quản Lý Rủi Ro
Vì cả hai đội đối đầu đều trả lời mọi câu hỏi cùng một lúc, thành công phụ thuộc rất lớn vào việc đánh giá rủi ro. Với quy định trừ điểm khi trả lời sai, các đội phải cân nhắc kỹ giữa sự tự tin và rủi ro: việc gửi một câu trả lời sai không chỉ làm mất đi điểm số tiềm năng—mà còn trực tiếp dâng thế dẫn điểm cho đội đối thủ.

### 2. Các Lĩnh Vực Kỹ Thuật Cốt Lõi Được Kiểm Tra
*   **Quản Lý Định Danh & Truy Cập (IAM)**: Phân biệt giữa các vai trò (roles), chính sách (policies) và quyền hạn của thành phần chính (principal permissions) trong môi trường đa tài khoản (multi-account).
*   **Mạng & Bảo Mật VPC**: Hiểu rõ sự khác biệt giữa Security Groups và Network ACLs, NAT Gateways, cũng như cấu hình định tuyến quá cảnh (transit routing).
*   **Điện Toán & Serverless**: Đánh giá sự đánh đổi giữa các loại instance EC2, đóng gói container với ECS/EKS, và các trình kích hoạt sự kiện (event triggers) của AWS Lambda.
*   **Kiến Trúc Cơ Sở Dữ Liệu & Lưu Trữ**: Lựa chọn giữa DynamoDB, Aurora và các tầng lưu trữ S3 dựa trên mô hình nhất quán (consistency models) và giới hạn chi phí.

### 3. Diễn Tiến Bảng Đấu & Trận Chung Kết
*   **Tứ Kết (8 Đội / 4 Trận)**: Các câu hỏi đố vui kỹ thuật nền tảng tốc độ cao nhằm kiểm tra phản xạ và thuật ngữ AWS cốt lõi giữa từng cặp đội.
*   **Bán Kết (4 Đội / 2 Trận)**: Độ phức tạp của câu hỏi tăng lên, liên quan đến các kịch bản kiến trúc đa dịch vụ và xử lý các trường hợp ngoại lệ (edge cases).
*   **Chung Kết (2 Đội Xuất Sắc Nhất)**: Vòng thi đầy áp lực tập trung vào các trụ cột của Khung Kiến Trúc Tối Ưu (Well-Architected Framework), tính toán hiệu quả chi phí và khôi phục sự cố thực tế để tìm ra nhà vô địch.

## Những Bài Học Quan Trọng

### Bài Học Chiến Lược & Vận Hành
- **Sự Chính Xác Quan Trọng Hơn Việc Đoán Mờ**: Trong môi trường có hình phạt cho thất bại (trừ điểm), kiến thức kỹ thuật được xác thực luôn đánh bại những dự đoán cảm tính.
- **Đồng Thuận Đội Dưới Áp Lực**: Các đội thành công đã phân công vai trò chuyên môn nội bộ—tận dụng điểm mạnh của từng thành viên (ví dụ: Bảo mật, Serverless) để thống nhất câu trả lời trước khi hết giờ.
- **Phát Hiện Các Bẫy Thường Gặp**: Các câu hỏi hóc húa đã làm nổi bật những khía cạnh mà các kỹ sư thường xuyên nhầm lẫn như cấu hình mặc định của dịch vụ, giới hạn mềm (soft limits), hoặc mô hình định giá.

---

## Áp Dụng Vào Công Việc & Học Tập

- **Nâng Cao Kỹ Năng Có Mục Tiêu**: Sử dụng các câu hỏi làm sai trong bài kiểm tra như một giáo trình cá nhân ngay lập tức để chuẩn bị cho các chứng chỉ AWS chính thức (ví dụ: Solutions Architect / Developer Associate).
- **Xác Thực Kiến Trúc**: Áp dụng phương pháp "tạm dừng và xác thực" khi đưa ra các quyết định về hạ tầng trong các dự án thực tế, tránh các giả định có thể dẫn đến gián đoạn hệ thống (downtime) hoặc cấu hình sai.
- **Kiểm Tra Kiến Thức Nội Bộ**: Áp dụng các buổi ôn tập đố vui đối đầu ngắn trong các buổi họp đội (team syncs) hoặc nhóm học tập để giữ cho kiến thức dịch vụ luôn sắc bén và cập nhật.
---

## Trải Nghiệm Sự Kiện

Hình thức loại trực tiếp đối đầu đã biến việc học đám mây tiêu chuẩn thành một màn trình diễn sôi động, đầy năng lượng.

#### Bầu Không Khí Cộng Đồng Cạnh Tranh
Thể thức bảng đấu tạo ra một môi trường tương tác, nơi khán giả theo dõi tiến trình trận đấu trên màn hình lớn trong khi các đội thi đấu thảo luận gay gắt về câu trả lời ngay bên cạnh nhau.

#### Học Tập Chủ Động Thay Vì Bài Giảng Thụ Động
Khác với các bài thuyết trình slide truyền thống, bài trắc nghiệm đồng thời buộc người tham gia phải truy xuất kiến thức một cách linh hoạt và bảo vệ lập luận kỹ thuật của mình trước đồng đội chỉ trong vài giây.

#### Một số hình ảnh sự kiện
![Event3](Event3.png)

> Việc game hóa các khái niệm kiến trúc AWS thông qua các trận đấu loại đối đầu đồng thời đã chứng minh là một phương pháp hiệu quả để kiểm tra sự hiểu biết kỹ thuật thực sự, đồng thời xây dựng tinh thần đồng đội.
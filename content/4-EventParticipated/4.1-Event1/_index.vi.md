---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Báo cáo Tổng kết: “Kiến trúc Đám mây, Đổi mới AI và Vận hành Hạ tầng”

### Mục tiêu Sự kiện

- Khám phá backend đám mây thời gian thực cho game engine.
- Giới thiệu kiến trúc GraphRAG phục vụ truy xuất dữ liệu đa chặng (multi-hop).
- Cung cấp lộ trình phát triển sự nghiệp từ IT helpdesk lên DevOps.
- Trình bày giải pháp học máy cho việc phát hiện xâm nhập mạng.
- Đi sâu vào cơ chế container và tối ưu hóa Dockerfile.
- Khái quát các khung làm việc (framework) để hợp tác nhóm kỹ thuật hiệu quả.

### Diễn giả

- **Nguyễn Quốc Bảo** – Cloud & Game Backend Developer
- **Việt Phát** – AI Major, Swinburne University of Technology
- **Trần Trung Vinh** – System Administrator, Central Retail Group
- **Lê Hoàng Gia Đại** – AWS G3 Team, HUTECH University
- **Bảo Huỳnh** – Junior Cloud Native Developer, Endava Vietnam
- **Trương Huy Phước** – Team Collaboration Specialist

### Điểm nổi bật Chính

#### Kiến trúc Nhiều người chơi trên Đám mây

- **Định tuyến Stateful:** Sử dụng AWS API Gateway WebSockets và route keys cho lưu lượng JSON thời gian thực.  
- **Backend Serverless:** Node.js 20 Lambda xử lý payload; DynamoDB theo dõi connection ID của người chơi.  
- **Lựa chọn Giao thức:** UDP cho tính toán vật lý độ trễ thấp; WebSockets cho trạng thái phiên; HTTP cho hồ sơ người dùng.  
- **Tích hợp phía Client:** Triển khai qua Godot 4 WebSocketPeer và xử lý bên trong vòng lặp native _process.  

#### Kiến trúc GraphRAG Nâng cao

- **Đánh chỉ mục Đồ thị:** Thay thế khớp vector văn bản cơ bản bằng các mô hình mối quan hệ cấu trúc cho truy xuất đa chặng. 
- **Quy trình Quản lý (Managed Pathway):** Sử dụng Amazon Bedrock Knowledge Bases để tạo embedding và Neptune Analytics để đánh chỉ mục. 
- **Quy trình Tùy chỉnh (Custom Pathway):** Sử dụng LlamaIndex để xây dựng từ văn bản sang đồ thị và Amazon Neptune cho các truy vấn Cypher.    

#### Lộ trình Sự nghiệp Sysadmin & DevOps

- **Chuyển đổi Tư duy:** Chuyển từ xử lý sự cố máy tính thụ động sang tự động hóa hạ tầng chủ động và kiểm toán hệ thống.  
- **An toàn Môi trường Thực tế:** Áp dụng quy tắc nghiêm ngặt là không bao giờ kiểm thử các thay đổi trực tiếp trên môi trường live production. 
- **Lộ trình Phát triển:** Từng bước qua Mạng máy tính (CCNA), Linux (RHCSA), Mở rộng Đám mây, IaC (Terraform), và CI/CD tự động. 

#### Hệ thống Phát hiện Xâm nhập Mạng (NIDS) dựa trên Học máy

- **Phát hiện Bất thường:** Bổ sung cho các chữ ký tường lửa tĩnh bằng mô hình ML để phát hiện các mối đe dọa Zero-Day.  
- **Kỹ thuật Dữ liệu:** Kiểm chứng mô hình bằng bộ dữ liệu CSE-CIC-IDS2018, tinh lọc dữ liệu và Ma trận Nhầm lẫn (Confusion Matrix) của LightGBM.  
- **Xử lý Sự cố trên Đám mây:** Truyền log từ WAF/ALB qua Kinesis Firehose tới S3, kích hoạt cảnh báo qua GuardDuty và SNS. 

#### Cơ chế Đóng gói Container với Docker

- **Ảo hóa Hệ điều hành:** Các container chia sẻ kernel của máy host, giúp chúng nhẹ hơn và nhanh hơn so với Máy ảo (VM) đầy đủ.
- **Tối ưu hóa Lớp:** Mỗi dòng trong Dockerfile sẽ tạo ra một lớp build bất biến và có thể tái sử dụng.
- **Vô hiệu hóa Bộ nhớ tạm:** Thay đổi một chỉ thị sẽ làm mất hiệu lực bộ nhớ tạm (cache) cho bước đó và tất cả các lớp tiếp theo.

#### Khung làm việc cho Hoạt động Nhóm Hiệu quả

- **4 Quy tắc Cốt lõi:**
  * Thiết lập mục tiêu rõ ràng
  * Phân công công việc phù hợp với kỹ năng cá nhân
  * Giao tiếp cởi mở
  * Đảm bảo trách nhiệm cá nhân
- **Công cụ Kỹ thuật số:** 
  * Sử dụng Trello và ClickUp để theo dõi công việc
  * Slack và Discord để lập trình viên duy trì giao tiếp liên tục  

### Bài học Cốt lõi

#### Tư duy Thiết kế

- **Ưu tiên Nghiệp vụ:** Kiến trúc phải được dẫn dắt bởi yêu cầu kinh doanh, không phải xu hướng công nghệ.
- **Chiến lược Giao thức:** Phối hợp các công cụ truyền thông (Sockets, HTTP, streams) phù hợp với yêu cầu cấu trúc của payload.
- **Giảm thiểu Rủi ro:** Xây dựng các môi trường kiểm thử (staging) cô lập và vòng lặp giám sát để bảo vệ tính sẵn sàng của môi trường production.

#### Kiến trúc Kỹ thuật

- **Mô hình Serverless:** Tận dụng tính toán theo sự kiện (Lambda) và cơ sở dữ liệu managed (DynamoDB) để giảm chi phí vận hành.
- **Build Hiệu quả:** Cấu trúc Dockerfile một cách chiến lược để tối đa hóa bộ nhớ tạm của các lớp và thu nhỏ dung lượng image.  
- **Bối cảnh Quan hệ:** Nâng cao khả năng tìm kiếm vector văn bản truyền thống bằng cách ánh xạ các liên kết dữ liệu với Cơ sở dữ liệu Đồ thị.

#### Chiến lược Hiện đại hóa

- **Nâng cấp Kỹ năng Theo Lớp:** Nâng cao trình độ một cách hệ thống từ nền tảng hệ điều hành lên IaC tự động và phân phối container.
- **Đồng bộ Công việc:** Sử dụng các khung làm việc Agile để ánh xạ trực tiếp các nhiệm vụ kỹ thuật cá nhân tới các mốc quan trọng của đội ngũ.

### Ứng dụng vào Thực tế

- **Triển khai WebSockets:** Thử nghiệm kiến trúc Serverless AWS WebSocket cho các ứng dụng yêu cầu dữ liệu thời gian thực, độ trễ thấp.  
- **Thử nghiệm Graph RAG:** Thử nghiệm LlamaIndex và Amazon Neptune để quản lý các truy vấn bối cảnh có tính quan hệ cao.  
- **Áp dụng IaC:** Thay thế cấu hình hệ thống thủ công bằng cách quản lý phiên bản môi trường với Terraform.  
- **Tối ưu hóa Dockerfile:** Sắp xếp lại các chỉ thị trong Dockerfile để tận dụng bộ nhớ tạm và thu nhỏ kích thước container.  
- **Triển khai ML NIDS:** Truyền luồng log mạng vào các pipeline ML để phát hiện các bất thường hành vi bị ẩn giấu.  
- **Tổ chức Không gian Làm việc:** Chuẩn hóa việc theo dõi dự án và các kỳ sprint của nhóm bằng bảng ClickUp hoặc Trello. 

### Trải nghiệm tại Sự kiện

Sự kiện 1 mang đến những góc nhìn rất thực tế bao gồm mạng đám mây, AI nâng cao, bảo mật hành vi và quy trình làm việc kỹ thuật.

#### Học hỏi từ các diễn giả giàu kinh nghiệm
- Các chuyên gia trong ngành đã trình bày những chiến lược kiến trúc thực thi được, đã qua kiểm chứng sản xuất cho việc mở rộng đám mây và container.
- Diễn giả chia sẻ lộ trình chuyên môn rõ ràng để chuyển dịch sang các vai trò DevOps và Sysadmin có tác động cao.

#### Tiếp cận kỹ thuật thực tế
- Phân tích cơ chế thiết lập socket serverless thời gian thực, hàm serverless và cơ sở dữ liệu lưu trạng thái.
- Nghiên cứu tiền xử lý dữ liệu, kiểm chứng ma trận mô hình ML, và pipeline tự động báo cáo sự cố trên đám mây.
- Tìm hiểu các lớp container và cơ chế cache khi runtime để hiểu rõ cách các câu lệnh ảnh hưởng đến hiệu quả build.

#### Tận dụng các công cụ hiện đại
- So sánh pipeline AI quản lý vs. tùy chỉnh sử dụng đánh chỉ mục đồ thị cho các tìm kiếm bối cảnh nâng cao. 
- Xem xét cấu hình phần mềm theo dõi dự án được thiết kế để giữ các đội ngũ agile luôn đồng bộ.

#### Kết nối và Thảo luận
- Các phiên thảo luận nhấn mạnh rằng việc tài liệu hóa liên tục và ngôn ngữ chung giúp thu hẹp khoảng cách giữa đội ngũ kinh doanh và phát triển.  

#### Bài học rút ra
- Khả năng mở rộng yêu cầu việc khớp các giao thức với từng trường hợp sử dụng và tách biệt các dịch vụ bằng các thành phần serverless.
- Độ tin cậy hệ thống dựa vào việc chuyển từ sửa chữa thủ công sang IaC tự động, tối ưu hóa lớp và giám sát ML chủ động.

#### Một số hình ảnh tại sự kiện
*Thêm ảnh sự kiện của bạn vào đây*  

> Nhìn chung, Sự kiện 1 mang lại sự kết hợp mạnh mẽ giữa kiến trúc kỹ thuật, các mô hình tối ưu hóa và chiến lược phát triển sự nghiệp thực tế cho các môi trường đám mây hiện đại.
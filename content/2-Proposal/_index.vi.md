---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
# Hệ thống kiểm soát cửa ra vào bằng nhận diện khuôn mặt thông minh
## Hệ thống kiểm soát cửa tích hợp AI tại thiết bị đầu cuối (Edge-AI) toàn diện

### 1. Tóm tắt dự án
Đề xuất này trình bày chi tiết về hệ thống kiểm soát truy cập cửa thông minh ứng dụng AI tại thiết bị đầu cuối (Edge-AI), xử lý dữ liệu sinh trắc học trực tiếp trên thiết bị. Bằng cách thực hiện nhận diện khuôn mặt ngay trên bo mạch ESP32-CAM AI-Thinker và kết hợp với hạ tầng đám mây AWS serverless (AWS IoT Core, Lambda, RDS, API Gateway và Amplify), hệ thống đạt được khả năng mở khóa cửa tức thì không cần kết nối mạng internet (offline), đồng thời vẫn cung cấp tính năng quản trị và ghi nhật ký tập trung trên đám mây.

### 2. Đặt vấn đề
### Vấn đề hiện tại là gì?
Các hệ thống kiểm soát sinh trắc học truyền thống sử dụng chìa khóa cơ, thẻ RFID hoặc phụ thuộc hoàn toàn vào đám mây đang gặp phải nhiều rào cản vận hành:
* Chìa khóa cơ và thẻ từ có thể bị thất lạc, mất cắp hoặc sao chép trái phép.
* Bàn phím nhập mã PIN dễ bị nhìn lén (shoulder surfing) và chia sẻ thông tin đăng nhập.
* Phần cứng sinh trắc học độc lập thường đắt đỏ, khó nâng cấp và thiếu tính năng quản lý từ xa tập trung.
* Việc đối soát khuôn mặt hoàn toàn trên đám mây gây ra độ trễ cao.

### Giải pháp
Hệ thống kiểm soát cửa Edge-AI kết hợp quản lý đám mây:
* Bo mạch ESP32-CAM AI-Thinker chụp hình ảnh và chạy các mô hình phát hiện, nhận diện khuôn mặt trực tiếp tại chỗ.
* Lambda gửi bất đồng bộ nhật ký truy cập, ảnh chụp khách truy cập và cập nhật trạng thái lên AWS IoT Core.
* Khi xác thực khuôn mặt thành công, ESP32 lập tức kích hoạt rơ-le GPIO để mở khóa cửa với độ trễ tối thiểu.
* Cổng thông tin web AWS Amplify được hỗ trợ bởi AWS API Gateway, AWS Lambda và AWS RDS cho phép quản trị viên quản lý người dùng từ xa, kích hoạt mở cửa thủ công và kiểm tra nhật ký hệ thống.

### Lợi ích và Tỷ suất hoàn vốn (ROI)
Bằng cách xử lý nhận diện khuôn mặt trực tiếp trên ESP32-CAM, hệ thống đảm bảo độ trễ bằng 0, khả năng truy cập ngoại tuyến hoàn toàn mà không phát sinh chi phí xử lý AI định kỳ trên đám mây. Với chi phí phần cứng dưới $35 cho mỗi cửa cùng hệ thống backend serverless tinh gọn, giải pháp giúp giảm tới 90% chi phí phần cứng và vận hành so với các giải pháp thương mại tương đương — đạt điểm hòa vốn (ROI) trong vòng dưới 2 tháng.

### 3. Kiến trúc giải pháp
Dưới đây là kiến trúc hệ thống thể hiện quá trình xử lý AI tại thiết bị đầu cuối trên bo mạch ESP32-CAM AI-Thinker kết hợp với quản lý đám mây AWS:

![Sơ đồ dự án](/images/2-Proposal/Diagram.jpg)

### Các dịch vụ AWS được sử dụng
- **AWS IoT Core**: Tiếp nhận các thông điệp MQTT mã hóa chứa lịch sử truy cập, dấu thời gian (timestamp), ID người dùng và ảnh chụp tùy chọn.
- **AWS Lambda**: Tầng tính toán serverless xử lý các thông điệp MQTT gửi đến, định dạng sự kiện kiểm toán và xử lý các yêu cầu lệnh quản trị từ xa.
- **Amazon API Gateway & AWS Amplify**: Cung cấp giao diện bảng điều khiển (dashboard) đa nền tảng cho quản trị viên nhằm:
  + Đăng ký người dùng mới và đẩy dữ liệu đặc trưng khuôn mặt (face embeddings) xuống thiết bị ESP32-CAM thông qua MQTT Device Shadows.
  + Giám sát các sự kiện truy cập theo thời gian thực, các lượt ra vào thành công và các nỗ lực truy cập trái phép.
  + Thực hiện lệnh mở khóa cửa thủ công từ xa qua các điểm cuối HTTPS/WebSocket bảo mật.
- **Amazon RDS**: Lưu trữ dữ liệu hồ sơ người dùng, phân quyền truy cập, nhật ký sự kiện có gắn dấu thời gian và bản ghi đăng ký.

### Thiết kế các thành phần
- **Thiết bị đầu cuối (Edge Devices)**: Mô-đun ESP32-CAM chạy mô hình nhận diện khuôn mặt cục bộ, kết nối trực tiếp với mô-đun rơ-le khóa cửa để kiểm soát cửa tức thì mà không cần mạng.
- **Thu nhận dữ liệu (Data Ingestion)**: AWS IoT Core sử dụng MQTTS cho việc truyền nhận thông điệp hai chiều bảo mật, quản lý trạng thái Device Shadow và định tuyến nhật ký sự kiện theo thời gian thực.
- **Lưu trữ dữ liệu (Data Storage)**: AWS RDS lưu trữ dữ liệu quan hệ người dùng, cấp độ quyền hạn, nhật ký ra vào cửa theo thời gian và nhật ký kiểm toán hệ thống.
- **Xử lý dữ liệu (Data Processing)**: AWS Lambda đóng vai trò backend serverless để phân tích thông điệp IoT gửi đến, ghi bản ghi kiểm toán vào AWS RDS và xử lý lệnh từ quản trị viên.
- **Giao diện Web (Web Interface)**: AWS Amplify lưu trữ bảng điều khiển quản trị trang đơn (SPA) đáp ứng responsive để theo dõi nhật ký thời gian thực, xem xét các lượt truy cập và phát lệnh mở khóa thủ công từ xa.
- **Quản lý người dùng (User Management)**: AWS RDS xử lý xác thực quản trị viên an toàn, quản lý mã thông báo JWT và kiểm soát truy cập dựa trên vai trò (RBAC) kết hợp cùng AWS API Gateway.

### 4. Triển khai kỹ thuật
**Các giai đoạn triển khai**
Dự án được chia thành hai phần — Thiết lập hệ thống nhận diện khuôn mặt và Phát triển nền tảng theo 3 giai đoạn:
- **Giai đoạn 1:** Phần cứng Edge & Thiết lập nòng cốt Đám mây (Tuần 1–4)
  + Nạp phần mềm (flash) cho ESP32-CAM AI-Thinker vào bộ nhớ flash cục bộ.
  + Kết nối mạch rơ-le GPIO và xác minh khả năng kích hoạt khóa không độ trễ khi khuôn mặt khớp dữ liệu ngoại tuyến.
  + Khởi tạo AWS IoT Core, tạo chứng chỉ X.509 cho thiết bị và xây dựng đường truyền thông điệp MQTTS.
  + Khởi tạo cơ sở dữ liệu AWS RDS, định nghĩa lược đồ (schema) và viết các hàm AWS Lambda để xử lý ghi nhật ký dữ liệu IoT.

- **Giai đoạn 2:** Giao diện Web & Tích hợp hệ thống (Tuần 5–7)
  + AWS RDS cho quyền truy cập và quản lý vai trò của quản trị viên.
  + Xây dựng và triển khai bảng điều khiển web AWS Amplify kết nối với các điểm cuối AWS API Gateway.
  + Thực hiện kiểm thử toàn trình (end-to-end) từ nhận diện tại thiết bị, kích hoạt rơ-le đến ghi nhật ký bất đồng bộ trên đám mây.

- **Giai đoạn 3:** Báo cáo kỹ thuật & Tài liệu hóa (Tuần 8–9)
  + Soạn thảo tài liệu kỹ thuật chi tiết của dự án, sơ đồ nguyên lý mạch phần cứng và sơ đồ thiết kế hệ thống.
  + Tổng hợp kết quả kiểm thử, các chỉ số phân tích hiệu năng và hướng dẫn sử dụng cho người vận hành.
  + Hoàn thiện và bàn giao báo cáo kỹ thuật dự án.

**Yêu cầu kỹ thuật**
- **Yêu cầu thành phần phần cứng**: ESP32-CAM (AI-Thinker), SERVO SG90, Mạch chuyển đổi FTDI USB-to-TTL (để nạp firmware), nguồn điện bên ngoài 5V/2A và công tắc cơ mở cửa khẩn cấp.
- **Nền tảng phát triển & Nền tảng Cloud**: ESP-IDF / Arduino IDE với thư viện phát hiện và nhận diện khuôn mặt, AWS IoT Core, AWS Lambda (môi trường Node.js/Python), AWS RDS (PostgreSQL/MySQL), Amazon API Gateway, AWS Amplify và Amazon Cognito, giao thức MQTTS (MQTT qua TLS 1.2/1.3) sử dụng chứng chỉ X.509 client, HTTPS và ủy quyền API dựa trên JWT.

### 5. Tiến độ & Các cột mốc
**Tiến độ dự án**
- Thực tập (Tháng 6-8): 2 tháng.
    - Tuần 1-3: Nghiên cứu AWS và nâng cấp phần cứng.
    - Tuần 4-7: Thiết kế và tinh chỉnh kiến trúc.
    - Tuần 8-9: Triển khai, kiểm thử và viết báo cáo.

### 6. Ước tính ngân sách

### Chi phí hạ tầng
- Các dịch vụ AWS:
    - AWS Lambda: $0.00/tháng.
    - AWS RDS: $11.405/tháng.
    - AWS VPC: $4.045/tháng.
    - Khác: $0.25/tháng.
    - AWS Amplify: $0.375/tháng.
    - AWS EC2 - Compute: $6.69/tháng.
    - AWS EC2 - Khác: $0.52/tháng.

Tổng cộng: $23.285/tháng.

- Phần cứng: $17 chi phí một lần (ESP-32, ESP-32-CAM, SERVO SG90, ...).

### 7. Đánh giá rủi ro 
#### Ma trận rủi ro
- Gián đoạn mạng (Network Outages): Tác động thấp, xác suất cao.
- Lỗi cảm biến/Cảm biến hỏng (Sensor Failures): Tác động cao, xác suất thấp.
- Bội chi chi phí (Cost Overruns): Tác động trung bình, xác suất thấp.

#### Chiến lược giảm thiểu
- Mạng: Thực hiện toàn bộ việc đối soát tại thiết bị cục bộ; lưu tạm nhật ký ra vào vào bộ nhớ flash và đồng bộ bất đồng bộ khi có mạng trở lại.
- Cảm biến: Cấu hình hiệu chuẩn thanh ghi camera (tự động phơi sáng) và bổ sung đèn LED 5V trợ sáng.
- Chi phí: Tận dụng gói AWS Free Tier, cài đặt cảnh báo ngân sách khi đạt ngưỡng 80% và sử dụng các thể hiện (instance) RDS micro.

#### Kế hoạch dự phòng
- Gián đoạn mạng: Sử dụng bộ đệm ghi vòng (circular buffer) trên bộ nhớ flash để tránh mất dữ liệu khi mất kết nối kéo dài.
- Lỗi cảm biến: Duy trì cơ chế khóa cơ vật lý dự phòng và tính năng mở khóa thủ công qua cổng thông tin web.
- Bội chi chi phí: Giảm thời gian lưu trữ dữ liệu trên cơ sở dữ liệu để giảm chi phí lưu trữ.

### 8. Kết quả dự kiến
#### Cải tiến về mặt kỹ thuật:
- Độ trễ dưới 500ms: Việc suy luận cục bộ kích hoạt rơ-le ngay lập tức.
- Tối ưu hóa tài nguyên: Backend serverless tự động mở rộng linh hoạt, giảm thiểu chi phí khi hệ thống nhàn rỗi.
#### Giá trị lâu dài
- Chi phí trên mỗi nút thấp: ~$10 cho mỗi cụm khóa so với các thiết bị thương mại đắt tiền.
- Khả năng mở rộng quy mô doanh nghiệp: Bảng điều khiển AWS Amplify duy nhất có thể quản lý nhiều nút cửa khác nhau.
- Tuân thủ kiểm toán: Nhật ký RDS tập trung cung cấp lịch sử ra vào đáng tin cậy.
---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
MÌNH ĐÃ HỌC ĐƯỢC GÌ SAU KHỊ TRẢI NGHIỆM AWS IOT CORE?

Dạo gần đây mình có thời gian đào sâu nghiên cứu và áp dụng AWS IoT Core vào các dự án phần cứng & hệ thống nhúng (IoT). Phải công nhận là từ lúc chuyển từ các MQTT Broker truyền thống sang AWS IoT Core, tư duy làm hệ thống IoT của mình đã thay đổi khá nhiều! 

Dưới đây là một vài góc nhìn và bài học rút ra sau quá trình thực thi:

1. Giao thức MQTT & Độ trễ siêu thấp 
Làm việc với các dòng vi điều khiển như ESP32, tài nguyên phần cứng và băng thông mạng luôn là rào cản lớn. AWS IoT Core hỗ trợ giao thức MQTT cực kỳ tối ưu cho các thiết bị công suất thấp, giúp việc gửi payload telemetry hay nhận lệnh điều khiển actuator (như Servo, Rơ-le) diễn ra gần như ngay lập tức mà không bị ngốn tài nguyên.

2. Bảo mật không còn là cơn ác mộng (X.509 Certificates & IAM Policy) 
Trước đây làm IoT cá nhân hay ngại khoản bảo mật, nhưng AWS chuẩn hóa việc này rất tốt. Mỗi thiết bị (Thing) khi kết nối đều cần có:

X.509 Cryptographic Certificate riêng biệt.

Amazon Root CA.

Fine-grained IAM Policies để giới hạn chính xác thiết bị nào được phép Publish hay Subscribe vào Topic nào.
Nhờ mTLS (Mutual TLS), mình hoàn toàn yên tâm về tính đóng kín và an toàn của hệ thống.

3. Hệ sinh thái Serverless đồng bộ tuyệt vời 
Sức mạnh thực sự của AWS IoT Core nằm ở khả năng kết nối không khoảng cách với các dịch vụ Serverless khác:

IoT Rules Engine: Bắn dữ liệu thẳng về AWS Lambda để xử lý logic backend mà không cần dựng server 24/7.

Database & Frontend Integration: Dễ dàng kết hợp với AWS RDS (MySQL) để lưu trữ thông tin người dùng và đẩy giao diện lên AWS Amplify.

[Link Facebook](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2225794871518806/?rdid=73emzcpWlVnQ2ms6#)
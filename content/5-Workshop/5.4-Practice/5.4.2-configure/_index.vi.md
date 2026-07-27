---
title : "Cài đặt dịch vụ Đám mây"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

**Cho AWS IOT Core**

 Trong bảng điêyf khiển, chọn All devices -> Things. Nhấp **Create things**

![endpoint](thing.png)

Chọn **Create single thing**.

![endpoint](create_thing.png)


Nhập **Thing name**.

![endpoint](a.png)

Chọn **Auto-generate a new certificate (recommended).**

![endpoint](auto_gen.png)

Đính kèm Policies to Certificate. Click **Create Thing**.

![endpoint](attach_poly.png)


Chọn **Download all** để lấy Device Certificate, Private Key File, Private Key File, Amazon Root CA 1.

![endpoint](download.png)



**For AWS Amplify**

Mở bảng điều khiển AWS Management và điều hướng tới AWS Amplify. Bấm **Create new app** (hoặc Host web app).

![endpoint](create_app.png)


Chọn git source code provider:

![endpoint](choose_git.png)

Ủy quyền AWS Amplify để truy cập vào tài khoản và chọn Repository và default target Branch.

![endpoint](select_branch.png)

Xem lại thông số kỹ thuật bản dựng để đảm bảo các thư mục đầu ra khớp với các tạo phẩm bản dựng của bạn (ví dụ: dist, build hoặc ./ cho HTML thô).

![endpoint](click_yaml.png)

Chỉnh sửa baseDirectory (if need).

![endpoint](edit_folder.png)

Bấm **Next**, sau đó **Save and deploy**

![endpoint](click_next.png)



**For AWS Lambda**
Tạo một tệp index.mjs. Tệp này sẽ xử lý logic cho phần backend.

```
/**
 * YOLO Home — Express + MySQL Backend  (v2)
 * Chạy: node server/index.js
 */

import express from 'express'
import mysql   from 'mysql2/promise'
import cors    from 'cors'
import dotenv  from 'dotenv'
import { IoTDataPlaneClient, PublishCommand } from '@aws-sdk/client-iot-data-plane'
import serverlessExpress from '@codegenie/serverless-express' 
dotenv.config()

const app  = express()
const PORT = process.env.PORT || 3306

// AWS IoT Core config
const AWS_IOT_ENDPOINT = process.env.AWS_IOT_ENDPOINT
const AWS_REGION      = process.env.AWS_REGION || 'ap-southeast-1'
const SERVO_TOPIC     = process.env.AWS_IOT_SERVO_TOPIC || 'servo/control'
const AUTH_TOPIC      = process.env.AWS_IOT_AUTH_TOPIC || 'auth/trigger'

const awsIot = AWS_IOT_ENDPOINT
  ? new IoTDataPlaneClient({
      region: AWS_REGION,
      endpoint: `https://${AWS_IOT_ENDPOINT}`,
    })
  : null

app.use(cors())
app.use(express.json())

app.use((req, res, next) => {
  req.url = req.url.replace('/Yolohome-backend', '');
  next();
});


// ── DB POOL ────────────────────────────────────────────────────────
let pool = null

async function getPool() {
  if (pool) return pool;

  if (!process.env.DB_HOST || !process.env.DB_USER || !process.env.DB_NAME) {
    console.error("Missing DB_HOST, DB_USER, or DB_NAME in .env. Please configure your database connection.");
    process.exit(1); 
  }

  pool = mysql.createPool({
    host:               process.env.DB_HOST,
    port:               parseInt(process.env.DB_PORT) || 3306,
    user:               process.env.DB_USER,
    password:           process.env.DB_PASS, 
    database:           process.env.DB_NAME,
    waitForConnections: true,
    connectionLimit:    10,
    connectTimeout:     10000,
  })
  return pool
}

async function query(sql, params = []) {
  const db = await getPool()
  const [rows] = await db.query(sql, params)
  return rows
}

...

```

Trong Visual Studio Code, mở dự án, sau đó mở terminal và chạy:
```
npm install 
npm install @codegenie/serverless-express
```

Sẽ có bốn đối tượng.

![endpoint](inside_folder.png)

Nén dự án lại.

Mở Bảng điều khiển AWS Lambda và nhấp vào **Create function**.

![endpoint](Lam_con.png)

Chọn **Author from scratch**, Đặt **Function name**, để  **Runtime** thành Node.js 24.x. Sau đó nhấn **Create function**.

![endpoint](setting_lam.png)

Nhấn **Update** -> **Update from a .zip file**.

![endpoint](update_func.png)

Chọn dự án đã nén ở bước cuối cùng và nhấp vào **Update**.

![endpoint](opopo.png)


**For AWS Gateway**

Trên bảng điều khiển AWS Lambda, Bấm **Configuration**. Chọn **Trigger**. Nhấn **Add trigger**.

![endpoint](triggier.png)

Select **API Gateway**.

![endpoint](api_confi.png)

Tạo API mới, chọn **REST API** và bảo mật **OPEN**, sau đó nhấp vào **Add**.

![endpoint](rest_api.png)


Bấm vào **Yolohome_backend-A-API**.

![endpoint](click_api.png)

Bấm vào **Resources**.

![endpoint](click_res.png)

Nhấn **Create resource**.

![endpoint](create_res.png)


Chọn **Proxy resource**, Chọn **Resource path**, Nhập **Resource name** và check **CORS (Cross Orgin Resource Sharing)**. Sau đó nhấn **Create resource**.

![endpoint](set_res.png)


Chọn **Create method**.

![endpoint](create_met.png)

Chọn **Method type** và **Lamda Proxy** là **Integration type**.

![endpoint](choose_met.png)

Chọn **Lambda function** tạo trước đó. 


![endpoint](choose_lam.png)

Chọn **Create method**.

![endpoint](click_create.png)

Thực hiện như trên cho các đường dẫn khác, sau đó nhấn **Deploy API**.

![endpoint](the_same.png)

Chọn **default**, bấm **Deploy**.

![endpoint](/Deploy.png)

Giờ đây, điểm cuối (hoạt động như một API REST) ​​có thể được sử dụng để kết nối giữa giao diện người dùng (AWS Amplify) và máy chủ (AWS Lambda).

![endpoint](use_end.png)


**Cho AWS RDS**

Mở bảng điều khiển Aurora và RDS, sau đó chọn **CREATE** trong **Create with full configuration**

![endpoint](choose_create.png)

Chọn **Engine type** (in this case is MySQL). Chọn **Easy create**.
![endpoint](clickmysql.png)


Cuộn xuống cuối trang và nhấp vào **Create database**.
![endpoint](fix_create.png)

Nhấp vào cơ sở dữ liệu đã tạo.

![endpoint](create_data.png)

Tìm **Connectivity & security**.

![endpoint](vpc.png)
Bấm **CIDR/IP-Inbound**.

![endpoint](click_ib.png)
Bấm **Security group ID** link.

![endpoint](group_ip.png)
Bấm **Edit inbound rules**.

![endpoint](edit_ib.png)
Chọn **My IP**. Sau đó **Save rules**.

![endpoint](my_ip.png)
Quay lại hàm Lambda đã tạo và tìm **Configuration** -> **Environment variables** để thêm các biến môi trường cho AWS IOT Core vá AWS RDS.

![endpoint](return.png)
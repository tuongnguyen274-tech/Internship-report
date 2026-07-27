---
title : "Cài đặt dịch vụ Đám mây"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

**Cho AWS IOT Core**

 Trong bảng điêyf khiển, chọn All devices -> Things. Nhấp **Create things**

![endpoint](/5-Workshop/5.4-Practice/Image/thing.png)

Chọn **Create single thing**.

![endpoint](/5-Workshop/5.4-Practice/Image/create_thing.png)


Nhập **Thing name**.

![endpoint](/5-Workshop/5.4-Practice/Image/a.png)

Chọn **Auto-generate a new certificate (recommended).**

![endpoint](/5-Workshop/5.4-Practice/Image/auto_gen.png)

Đính kèm Policies to Certificate. Click **Create Thing**.

![endpoint](/5-Workshop/5.4-Practice/Image/attach_poly.png)


Chọn **Download all** để lấy Device Certificate, Private Key File, Private Key File, Amazon Root CA 1.

![endpoint](/5-Workshop/5.4-Practice/Image/download.png)



**For AWS Amplify**

Mở bảng điều khiển AWS Management và điều hướng tới AWS Amplify. Bấm **Create new app** (hoặc Host web app).

![endpoint](/5-Workshop/5.4-Practice/Image/create_app.png)


Chọn git source code provider:

![endpoint](/5-Workshop/5.4-Practice/Image/choose_git.png)

Ủy quyền AWS Amplify để truy cập vào tài khoản và chọn Repository và default target Branch.

![endpoint](/5-Workshop/5.4-Practice/Image/select_branch.png)

Xem lại thông số kỹ thuật bản dựng để đảm bảo các thư mục đầu ra khớp với các tạo phẩm bản dựng của bạn (ví dụ: dist, build hoặc ./ cho HTML thô).

![endpoint](/5-Workshop/5.4-Practice/Image/click_yaml.png)

Chỉnh sửa baseDirectory (if need).

![endpoint](/5-Workshop/5.4-Practice/Image/edit_folder.png)

Bấm **Next**, sau đó **Save and deploy**

![endpoint](/5-Workshop/5.4-Practice/Image/click_next.png)



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

![endpoint](/5-Workshop/5.4-Practice/Image/inside_folder.png)

Nén dự án lại.

Mở Bảng điều khiển AWS Lambda và nhấp vào **Create function**.

![endpoint](/5-Workshop/5.4-Practice/Image/Lam_con.png)

Chọn **Author from scratch**, Đặt **Function name**, để  **Runtime** thành Node.js 24.x. Sau đó nhấn **Create function**.

![endpoint](/5-Workshop/5.4-Practice/Image/setting_lam.png)

Nhấn **Update** -> **Update from a .zip file**.

![endpoint](/5-Workshop/5.4-Practice/Image/update_func.png)

Chọn dự án đã nén ở bước cuối cùng và nhấp vào **Update**.

![endpoint](/5-Workshop/5.4-Practice/Image/opopo.png)


**For AWS Gateway**

Trên bảng điều khiển AWS Lambda, Bấm **Configuration**. Chọn **Trigger**. Nhấn **Add trigger**.

![endpoint](/5-Workshop/5.4-Practice/Image/triggier.png)

Select **API Gateway**.

![endpoint](/5-Workshop/5.4-Practice/Image/api_confi.png)

Tạo API mới, chọn **REST API** và bảo mật **OPEN**, sau đó nhấp vào **Add**.

![endpoint](/5-Workshop/5.4-Practice/Image/rest_api.png)


Bấm vào **Yolohome_backend-A-API**.

![endpoint](/5-Workshop/5.4-Practice/Image/click_api.png)

Bấm vào **Resources**.

![endpoint](/5-Workshop/5.4-Practice/Image/click_res.png)

Nhấn **Create resource**.

![endpoint](/5-Workshop/5.4-Practice/Image/create_res.png)


Chọn **Proxy resource**, Chọn **Resource path**, Nhập **Resource name** và check **CORS (Cross Orgin Resource Sharing)**. Sau đó nhấn **Create resource**.

![endpoint](/5-Workshop/5.4-Practice/Image/set_res.png)


Chọn **Create method**.

![endpoint](/5-Workshop/5.4-Practice/Image/create_met.png)

Chọn **Method type** và **Lamda Proxy** là **Integration type**.

![endpoint](/5-Workshop/5.4-Practice/Image/choose_met.png)

Chọn **Lambda function** tạo trước đó. 


![endpoint](/5-Workshop/5.4-Practice/Image/choose_lam.png)

Chọn **Create method**.

![endpoint](/5-Workshop/5.4-Practice/Image/click_create.png)

Thực hiện như trên cho các đường dẫn khác, sau đó nhấn **Deploy API**.

![endpoint](/5-Workshop/5.4-Practice/Image/the_same.png)

Chọn **default**, bấm **Deploy**.

![endpoint](../Image/Deploy.png)

Giờ đây, điểm cuối (hoạt động như một API REST) ​​có thể được sử dụng để kết nối giữa giao diện người dùng (AWS Amplify) và máy chủ (AWS Lambda).

![endpoint](/5-Workshop/5.4-Practice/Image/use_end.png)


**Cho AWS RDS**

Mở bảng điều khiển Aurora và RDS, sau đó chọn **CREATE** trong **Create with full configuration**

![endpoint](/5-Workshop/5.4-Practice/Image/choose_create.png)

Chọn **Engine type** (in this case is MySQL). Chọn **Easy create**.
![endpoint](/5-Workshop/5.4-Practice/Image/clickmysql.png)


Cuộn xuống cuối trang và nhấp vào **Create database**.
![endpoint](/5-Workshop/5.4-Practice/Image/fix_create.png)

Nhấp vào cơ sở dữ liệu đã tạo.

![endpoint](/5-Workshop/5.4-Practice/Image/create_data.png)

Tìm **Connectivity & security**.

![endpoint](/5-Workshop/5.4-Practice/Image/vpc.png)
Bấm **CIDR/IP-Inbound**.

![endpoint](/5-Workshop/5.4-Practice/Image/click_ib.png)
Bấm **Security group ID** link.

![endpoint](/5-Workshop/5.4-Practice/Image/group_ip.png)
Bấm **Edit inbound rules**.

![endpoint](/5-Workshop/5.4-Practice/Image/edit_ib.png)
Chọn **My IP**. Sau đó **Save rules**.

![endpoint](/5-Workshop/5.4-Practice/Image/my_ip.png)
Quay lại hàm Lambda đã tạo và tìm **Configuration** -> **Environment variables** để thêm các biến môi trường cho AWS IOT Core vá AWS RDS.

![endpoint](/5-Workshop/5.4-Practice/Image/return.png)
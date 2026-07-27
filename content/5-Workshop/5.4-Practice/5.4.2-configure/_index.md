---
title : "Cloud configure"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

**For AWS IOT Core**

In the console navigation pane, select All devices -> Things. Click **Create things**

![endpoint](../Image/thing.png)

Select **Create single thing**.

![endpoint](../Image/create_thing.png)


Enter **Thing name**.

![endpoint](../Image/a.png)

Choose **Auto-generate a new certificate (recommended).**

![endpoint](../Image/auto_gen.png)

Attach Policies to Certificate. Click **Create Thing**.

![endpoint](../Image/attach_poly.png)


Click **Download all** to get Device Certificate, Private Key File, Private Key File, Amazon Root CA 1.

![endpoint](../Image/download.png)



**For AWS Amplify**

Open the AWS Management Console and navigate to AWS Amplify. Click **Create new app** (or Host web app).

![endpoint](../Image/create_app.png)


Select your git source code provider:

![endpoint](../Image/choose_git.png)

Authorize AWS Amplify to access your account and select the project Repository and default target Branch.

![endpoint](../Image/select_branch.png)

Review the build specification to ensure output directories match your build artifacts (e.g., dist, build, or ./ for raw HTML).

![endpoint](../Image/click_yaml.png)

Change baseDirectory (if need).

![endpoint](../Image/edit_folder.png)

Click **Next**, then click **Save and deploy**

![endpoint](../Image/click_next.png)



**For AWS Lambda**
Make a index.mjs file. This file will handle the logic for backend.

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

In Visual Studio Code, open the project, then open terminal and run:

```
npm install 
npm install @codegenie/serverless-express
```

It will has four object.

![endpoint](../Image/inside_folder.png)

Zip the project. 

Open the AWS Lambda Console and click **Create function**.

![endpoint](../Image/Lam_con.png)

Choose **Author from scratch**, enter **Function name**, set **Runtime** to Node.js 24.x. Then click **Create function**.

![endpoint](../Image/setting_lam.png)

Click **Update** -> **Update from a .zip file**.

![endpoint](../Image/update_func.png)

Choose the zipped project in last step and Click **Update**.

![endpoint](../Image/opopo.png)


**For AWS Gateway**

On the AWS Lambda console, Click **Configuration**. Then choose **Trigger**. Click **Add trigger**.

![endpoint](../Image/triggier.png)

Select **API Gateway**.

![endpoint](../Image/api_confi.png)

Create a new API, choose **REST API** and security **Open** then click **Add**.

![endpoint](../Image/rest_api.png)


Click on **Yolohome_backend-A-API**.

![endpoint](../Image/click_api.png)

Click on **Resources**.

![endpoint](../Image/click_res.png)

Click **Create resource**.

![endpoint](../Image/create_res.png)


Choose **Proxy resource**, Select **Resource path**, Enter **Resource name** and Check **CORS (Cross Orgin Resource Sharing)**. Then click **Create resource**.

![endpoint](../Image/set_res.png)


Click **Create method**.

![endpoint](../Image/create_met.png)

Choose **Method type** and **Lamda Proxy** as **Integration type**.

![endpoint](../Image/choose_met.png)

Choose **Lambda function** created before. 


![endpoint](../Image/choose_lam.png)

Click **Create method**.

![endpoint](../Image/click_create.png)

Do the same for the others path, then click **Deploy API**.

![endpoint](../Image/the_same.png)

Choose **default**, then click **Deploy**.

![endpoint](../Image/Deploy.png)

Now the endpoint (act as an REST API) can be used to connect between frontend (AWS Amplify) and backend (AWS Lambda)

![endpoint](../Image/use_end.png)


**For AWS RDS**

Open Aurora and RDS console and choose **CREATE** in **Create with full configuration**

![endpoint](../Image/choose_create.png)

Choose **Engine type** (in this case is MySQL). Then choose **Easy create**.
![endpoint](../Image/clickmysql.png)


Scroll down at the end and click **Create database**.
![endpoint](../Image/fix_create.png)

Click on created database.

![endpoint](../Image/create_data.png)

Find **Connectivity & security**.

![endpoint](../Image/vpc.png)
Click **CIDR/IP-Inbound**.

![endpoint](../Image/click_ib.png)
Click **Security group ID** link.

![endpoint](../Image/group_ip.png)
Choose **Edit inbound rules**.

![endpoint](../Image/edit_ib.png)
Select **My IP**. Then **Save rules**.

![endpoint](../Image/my_ip.png)
Return to created Lamdba function and find **Configuration** -> **Environment variables** to add environment variables for AWS IOT Core and AWS RDS.

![endpoint](../Image/return.png)
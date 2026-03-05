# AWS S3 Static Website Deployment Demo

## Overview

This project demonstrates how to deploy a **static website using Amazon S3**. The purpose of this demo is to showcase how AWS S3 can be used as a **cost-effective, scalable, and serverless hosting solution** for static web applications.

In this demonstration, a simple responsive website is deployed on **Amazon S3 using the Static Website Hosting feature**.

This demo was conducted as part of an **AWS Cloud session at Nutan College of Engineering, Pune**.

---

## Technologies Used

- Amazon S3
- HTML5
- CSS3
- AWS Management Console

---

## Architecture

Static website hosting using Amazon S3 works by storing web assets (HTML, CSS, JS, images) inside an S3 bucket and making them publicly accessible.

```
User Browser
     │
     ▼
S3 Static Website Endpoint
     │
     ▼
Amazon S3 Bucket
(index.html, style.css, assets)
```

---

## Project Structure

```
aws-s3-static-website-demo
│
├── index.html
├── style.css
└── README.md
```

---

## Features

- Fully **serverless hosting**
- **Responsive UI design**
- **Highly scalable infrastructure**
- **Low cost static hosting**
- Deployable within minutes

---

## Prerequisites

Before deploying the website, ensure you have:

- An **AWS account**
- Access to the **AWS Management Console**
- Basic understanding of **Amazon S3**

---

# Deployment Steps

## Step 1: Login to AWS Console

Go to:

```
https://console.aws.amazon.com
```

Search for **S3** in the services menu.

---

## Step 2: Create an S3 Bucket

1. Click **Create Bucket**
2. Provide a globally unique bucket name

Example:

```
aws-static-demo-2026
```

3. Select Region

Recommended for this demo:

```
Asia Pacific (Mumbai) – ap-south-1
```

4. Disable **Block Public Access**

Uncheck:

```
Block all public access
```

Confirm the warning checkbox.

5. Click **Create Bucket**

---

## Step 3: Upload Website Files

Open the created bucket.

Click **Upload** and add the following files:

```
index.html
style.css
```

Click **Upload** to finish.

---

## Step 4: Enable Static Website Hosting

1. Open the bucket
2. Navigate to **Properties**
3. Scroll to **Static Website Hosting**
4. Click **Edit**

Enable:

```
Static Website Hosting
```

Configure:

```
Index Document: index.html
Error Document: index.html
```

Save the configuration.

AWS will generate a **Website Endpoint URL**.

Example:

```
http://aws-static-demo-2026.s3-website.ap-south-1.amazonaws.com
```

---

## Step 5: Configure Bucket Policy

To allow public access to the website files, add the following bucket policy.

Navigate to:

```
Permissions → Bucket Policy
```

Add:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadAccess",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::aws-static-demo-2026/*"
    }
  ]
}
```

Replace the bucket name accordingly.

Save the policy.

---

## Step 6: Access the Website

Go to:

```
Properties → Static Website Hosting
```

Open the **Website Endpoint URL**.

Your static website should now be live.

---

# Common Errors and Troubleshooting

## Access Denied

Cause: Public access is still blocked.

Fix: Disable **Block Public Access** in bucket permissions.

---

## 404 Not Found

Cause: `index.html` is missing or incorrectly named.

Fix: Ensure the file name is exactly:

```
index.html
```

Note: S3 is **case-sensitive**.

---

## Website Loads Without CSS

Cause: Incorrect CSS path.

Fix: Ensure the HTML file references CSS correctly:

```html
<link rel="stylesheet" href="style.css">
```

---

## Bucket Name Already Exists

Cause: S3 bucket names are globally unique.

Fix: Add suffix to the bucket name:

```
aws-static-demo-2026
aws-static-demo-mayuresh
```

---

# Advantages of Hosting Static Websites on S3

- Highly scalable
- 99.999999999% durability
- Serverless architecture
- Low operational cost
- Easy deployment

---

# Future Improvements

This demo can be extended by integrating additional AWS services:

- Amazon CloudFront for global CDN
- Route 53 for custom domain hosting
- AWS Certificate Manager for HTTPS support
- S3 Versioning for website rollback

---

# Demo Conducted By

**Mayuresh Muluk**  
AWS Cloud Captain
AWS Cloud Club PICT

---

# License

This project is for **educational and demonstration purposes**.

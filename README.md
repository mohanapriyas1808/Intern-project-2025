# **Static Website Hosting on AWS S3 with CloudFront**

This project demonstrates how to host a static website using **Amazon S3** and deliver it efficiently using **Amazon CloudFront (CDN)**.

---
# **Project Overview**

- **S3 Bucket**: Used to store the static website files (`index.html`, `style.css`, etc.)
- **Static Website Hosting**: Enabled on the S3 bucket
- **Public Access**: Configured the bucket policy to allow public `GET` access
- **CloudFront Distribution**: Configured to serve content from the S3 static website endpoint
- **No SSL/TLS**: HTTPS and certificates (SSL/TLS) were not used
- **No Route 53**: Custom domain or DNS configuration via Route 53 was not used

---

# **Files Hosted**

- `index.html`
- `style.css`
- `script.js`

---

# **Configuration Steps**

**### 1. Created S3 Bucket**
- Bucket name: `my-buc-10-07` (example)
- Enabled **Static Website Hosting** with `index.html` as root document
- Uploaded all static site files

**### 2. Made S3 Bucket Public**
- Unchecked “Block all public access” under permissions
- Added the following **bucket policy**:
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Sid": "PublicReadGetObject",
        "Effect": "Allow",
        "Principal": "*",
        "Action": "s3:GetObject",
        "Resource": "arn:aws:s3:::BUCKET_NAME/*"
      }
    ]
  }
  
**###3. Created CloudFront Distribution**
- Origin domain: Selected S3 static website endpoint
- Viewer protocol policy: HTTP only
- Default root object: index.html
- Used default CloudFront domain name for access



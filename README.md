# AWS Static Website Hosting with CloudFront & S3

A secure and scalable static website hosting solution using Amazon S3 and Amazon CloudFront for fast, reliable, and globally distributed content delivery.

##  Project Overview

This project demonstrates how to host a static website on AWS using Amazon S3 as the origin and Amazon CloudFront as the Content Delivery Network (CDN).

The S3 bucket is secured using **Origin Access Control (OAC)** so that website content is accessed through CloudFront instead of being directly exposed through the S3 bucket.

### Key Features

- Amazon S3 for static website file storage
- Amazon CloudFront for global content delivery
- Origin Access Control (OAC) for securing the S3 origin
- HTTPS-enabled content delivery through CloudFront
- CloudFront caching for improved performance
- Restricted direct access to the S3 bucket
- Responsive static website using HTML and CSS

##  Architecture

The architecture follows this flow:

**User → CloudFront → S3**

### How it works

1. The user requests the website through the CloudFront distribution.
2. CloudFront receives the request from the user.
3. CloudFront checks its cache for the requested content.
4. If the content is not available in the cache, CloudFront requests it from the S3 origin.
5. S3 returns the requested static files to CloudFront.
6. CloudFront delivers the content to the user from an AWS edge location.

This architecture improves website performance while keeping the S3 origin protected.

## ☁️ AWS Services Used

### Amazon S3

Amazon S3 is used to store the static website files such as:

- `index.html`
- `style.css`
- Other static assets

The S3 bucket acts as the origin for the CloudFront distribution.

### Amazon CloudFront

CloudFront is used as the CDN to distribute website content globally.

It provides:

- Global content delivery
- Edge caching
- Reduced latency
- HTTPS support
- Improved website performance

### Origin Access Control (OAC)

Origin Access Control is configured between CloudFront and S3.

OAC allows CloudFront to securely access objects stored in the S3 bucket while preventing direct public access to the S3 origin.

---

##  Security Configuration

The S3 bucket is configured to prevent unnecessary public access.

Instead of allowing users to directly access the S3 bucket, requests are routed through CloudFront.

The bucket policy allows the CloudFront distribution to access the required S3 objects using Origin Access Control.

### Security Flow

**User → HTTPS → CloudFront → OAC → S3**

This provides a more secure architecture compared with directly exposing the S3 bucket to the public internet.

##  Website Files

The static website consists of:

- `index.html` – Main webpage
- `style.css` – Website styling

These files are uploaded to the S3 bucket and served through CloudFront.

---

## ⚡ CloudFront Caching

CloudFront caches static website content at AWS edge locations.

When users request the same content, CloudFront can serve the cached version instead of requesting the object from S3 every time.

This helps:

- Reduce latency
- Improve page loading speed
- Reduce requests to the S3 origin
- Provide better performance for users in different geographic locations

---

## 🔒 HTTPS

CloudFront provides HTTPS-based access to the website.

This ensures that communication between users and CloudFront is encrypted.

The website can therefore be accessed securely through the CloudFront distribution URL.

---

## 📸 Project Screenshots

### Figure 1 – Website Output

Shows the final static website running successfully.

### Figure 2 – Website Files Uploaded to Amazon S3

Shows the HTML and CSS files uploaded to the S3 bucket.

### Figure 3 – Configuring Amazon S3 as CloudFront Origin

Shows the S3 bucket configured as the origin of the CloudFront distribution.

### Figure 4 – S3 Bucket Policy with OAC

Shows the S3 bucket policy that allows CloudFront to securely access the S3 objects through Origin Access Control.

### Figure 5 – CloudFront Distribution Details

Shows the configured CloudFront distribution and its deployment details.

---

## 🔄 Deployment Flow

The complete deployment process was:

1. Created a static website using HTML and CSS.
2. Created an Amazon S3 bucket.
3. Uploaded website files to the S3 bucket.
4. Configured CloudFront with the S3 bucket as the origin.
5. Created and configured Origin Access Control.
6. Updated the S3 bucket policy to allow CloudFront access.
7. Configured the default root object as `index.html`.
8. Enabled HTTPS delivery through CloudFront.
9. Tested the website using the CloudFront distribution URL.
10. Verified successful content delivery.

---

## 🛡️ Why CloudFront + S3?

Using CloudFront in front of S3 provides several advantages:

| Feature | Benefit |
|---|---|
| S3 | Durable static file storage |
| CloudFront | Global content delivery |
| OAC | Secure S3 origin access |
| HTTPS | Encrypted communication |
| Caching | Faster content delivery |
| Edge Locations | Lower latency |

---

## 🧰 Technologies Used

### Frontend

- HTML5
- CSS3

### AWS

- Amazon S3
- Amazon CloudFront
- Origin Access Control (OAC)
- IAM / S3 Bucket Policy

---

##  What I Learned

Through this project, I gained practical experience with:

- Static website hosting on AWS
- Amazon S3 bucket configuration
- Uploading and managing website objects
- CloudFront CDN configuration
- Origin Access Control
- S3 bucket policies
- HTTPS-based content delivery
- CloudFront caching
- Securing an S3 origin
- Understanding AWS edge-based content delivery

---

## 🚀 Project Outcome

The static website was successfully deployed using Amazon S3 and Amazon CloudFront.

The final architecture provides:

**Secure S3 Storage + CloudFront CDN + HTTPS + Global Content Delivery**

The project demonstrates a practical approach to deploying a fast, scalable, and secure static website on AWS.

---

## 📌 Architecture Summary

```text
                  Internet Users
                        │
                        │ HTTPS
                        ▼
               ┌─────────────────┐
               │  CloudFront CDN │
               └────────┬────────┘
                        │
                        │ OAC
                        ▼
               ┌─────────────────┐
               │    Amazon S3    │
               │ Static Website  │
               │ index.html      │
               │ style.css       │
               └─────────────────┘

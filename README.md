# AWS Static Website Hosting using Amazon S3 + CloudFront CDN

## Project Overview

This project demonstrates a Proof of Concept (POC) for hosting a static website on AWS using Amazon S3 as the origin storage and Amazon CloudFront as the Content Delivery Network (CDN) layer.

The implementation focuses on improving website performance, scalability, and global content delivery using AWS managed services.

---

## Architecture

```text
User Browser
      ↓
CloudFront CDN
(Global Edge Locations)
      ↓
Origin Access Control (OAC)
      ↓
Amazon S3 Bucket
(Static Website Files)
```

---

## AWS Services Used

### Amazon S3

Purpose:

- Store static website files
- Act as origin storage
- Centralized website hosting

Configuration:

- Bucket Type: Private Bucket
- Object Ownership: Bucket Owner Enforced
- Encryption: SSE-S3
- Website Files: HTML

---

### Amazon CloudFront

Purpose:

- Global CDN delivery
- Content caching
- Reduced latency
- Improved website performance
- Secure S3 integration

Configuration:

- Origin Type: Amazon S3
- Origin Access Control (OAC): Enabled
- Cache Policy: AWS Recommended
- Security Protection: Enabled

---

## Project Workflow

```text
User Request
      ↓
CloudFront Edge Location
      ↓
Cache Available?
     /       \
   YES       NO
    ↓         ↓
Serve       Fetch Data
Content     From S3 Origin
Directly        ↓
                Cache Content
                    ↓
             Return Response
```

---

## Implementation Steps

### Step 1 – Create S3 Bucket

Create an S3 bucket:

```

Bucket Name:
poc-static-website-piyush-patil-09022004

```

Upload website files:

```

index.html

```

---

### Step 2 – Configure Bucket Permissions

Configure:

- Private Bucket Access
- Bucket Policy for CloudFront OAC
- Bucket Owner Enforced

---

### Step 3 – Create CloudFront Distribution

Configuration:

| Parameter | Value |
|------------|--------|
| Origin Type | Amazon S3 |
| Cache Policy | Recommended |
| Origin Access | OAC |
| Security Protection | Enabled |

Deployment time:

```

5 – 15 Minutes

```

---

## CloudFront CDN Working

### Cache Hit

```text
User
 ↓
CloudFront Edge
 ↓
Content Found
 ↓
Website Delivered
```

### Cache Miss

```text
User
 ↓
CloudFront Edge
 ↓
Origin Request
 ↓
S3 Bucket
 ↓
Store Cache
 ↓
Deliver Content
```

---

## Security Implemented

- Private S3 Origin
- Origin Access Control (OAC)
- Encryption at Rest (SSE-S3)
- CloudFront Managed Security

---

## Issue Faced During Implementation

### Access Denied Error

Error:

```xml
<Error>
<Code>AccessDenied</Code>
<Message>Access Denied</Message>
</Error>
```

Root Cause:

Website file uploaded inside folder:

```

S3 Bucket/index.html

```

Solution:

Move:

```

index.html

```

to bucket root.

Correct Structure:

```text
Bucket
 └── index.html
```

---

## Validation Results

| Test Case | Status |
|------------|---------|
| Website Deployment | PASS |
| CloudFront CDN | PASS |
| Private S3 Access | PASS |
| Cache Delivery | PASS |
| Security Configuration | PASS |

---

## Current POC Scope

Implemented:

- Amazon S3
- CloudFront CDN
- Origin Access Control
- Global Content Delivery

Not Implemented:

- Route53
- ACM Certificate
- Custom Domain

Reason:

Current implementation uses CloudFront default HTTPS domain.

---

## Future Enhancements

- Route53 Integration
- ACM SSL Certificate
- Custom Domain Mapping
- CloudFront Monitoring
- AWS WAF Rules
- Logging and Metrics

---

## Final Output

Website URL:

```

https://d2cdjj1ym7qcf4.cloudfront.net

```

Project Status:

```

SUCCESSFULLY IMPLEMENTED

```

---

## Author

Piyush Patil

AWS Static Website Hosting POC

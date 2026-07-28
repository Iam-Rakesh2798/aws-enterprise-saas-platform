# Day 6 - Amazon CloudFront with Origin Access Control (OAC)

## Objective

Build a secure and globally distributed content delivery layer for the Employee Management SaaS Platform using Amazon CloudFront.

---

## Architecture Overview

Implemented Amazon CloudFront as a Content Delivery Network (CDN) to accelerate content delivery, reduce latency, and improve application performance.

Configured CloudFront with two origins:

- Application Load Balancer (ALB) for dynamic application requests.
- Amazon S3 Bucket for static content such as employee profile images.

Implemented Origin Access Control (OAC) to securely restrict direct access to the S3 bucket while allowing CloudFront to retrieve objects.

---

## AWS Services Used

- Amazon CloudFront
- Amazon S3
- Origin Access Control (OAC)
- Application Load Balancer (ALB)
- AWS IAM
- Auto Scaling Group
- Amazon EC2

---

## Resources Created

### CloudFront Distribution

- Distribution Type: Single Website/Application
- Origin 1: Amazon S3 Bucket
- Origin 2: Application Load Balancer
- HTTP Versions: HTTP/2 and HTTP/3
- Compression: Enabled
- Cache Policy: CachingOptimized

### Origin Access Control

- Origin Access Control (OAC) created
- Bucket Policy updated automatically
- Direct S3 access restricted

### Cache Behaviors

Default Behavior

- Path Pattern: *
- Origin: Application Load Balancer

Static Content Behavior

- Path Pattern: /images/*
- Origin: Amazon S3
- Cache Policy: CachingOptimized

---

## Security Implementation

- S3 Bucket kept private.
- Origin Access Control (OAC) used instead of public bucket access.
- Bucket policy automatically configured to allow access only from the CloudFront distribution.
- Dynamic application traffic routed through the Application Load Balancer.
- Static content served securely through CloudFront.

---

## Connectivity Validation

Verified CloudFront distribution deployment.

Successfully accessed static content using the CloudFront distribution domain.

Verified that direct access to the S3 object URL returned "Access Denied", confirming that only CloudFront could access the bucket.

---

## CloudFront Testing Performed

Verified CloudFront distribution deployment.

Tested static content delivery:

```
https://<cloudfront-domain>/images/profile.jpg
```

Verified direct S3 access:

```
https://employee-management-platform-rakesh2798.s3.ap-south-1.amazonaws.com/images/profile.jpg
```

Result:

```
Access Denied
```

Verified request routing using CloudFront Behaviors.

---

## Production Best Practices Followed

- Private S3 bucket.
- Origin Access Control (OAC) enabled.
- Separate origins for static and dynamic content.
- Cache Behaviors configured for URL-based routing.
- Managed Cache Policy used.
- Compression enabled.
- CloudFront used as the public entry point instead of exposing S3.

---

## Key Learnings

- Understanding Content Delivery Networks (CDNs).
- Difference between CloudFront, Edge Locations and Origins.
- CloudFront Distribution creation.
- Configuring multiple origins.
- Origin Access Control (OAC).
- Cache Behaviors and request routing.
- Cache Hit vs Cache Miss.
- Importance of keeping S3 private.
- Secure static content delivery using CloudFront.

---

## Outcome

Successfully deployed Amazon CloudFront in front of the application and S3 bucket, configured secure Origin Access Control, implemented multiple origins with cache behaviors, and validated secure delivery of static content while preventing direct access to the S3 bucket.
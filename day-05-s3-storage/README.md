# Day 5 - Amazon S3 Secure Object Storage

## Objective

Build a secure and production-style object storage layer for the Employee Management SaaS Platform using Amazon S3.

---

## Architecture Overview

Implemented Amazon S3 as the centralized object storage service for employee profile images, resumes, documents, and application logs.

Integrated the EC2 application servers with Amazon S3 using an IAM Role to securely upload and download objects without storing AWS access keys on the instances.

---

## AWS Services Used

- Amazon S3
- IAM Roles
- IAM Policies
- AWS Systems Manager (SSM)

---

## Resources Created

### S3 Bucket

- Bucket Type: General Purpose
- Region: Asia Pacific (Mumbai)
- Block Public Access: Enabled
- Versioning: Enabled
- Server-Side Encryption: SSE-S3

### Folder Structure

- employee-profile-images/
- employee-resumes/
- employee-documents/
- application-logs/

### IAM Configuration

- IAM Role: EC2-SSM-Role
- Custom IAM Policy: Employee-S3-Access-Policy

---

## Security Implementation

- Bucket configured as private.
- Block Public Access enabled.
- Server-side encryption enabled using SSE-S3.
- Versioning enabled to protect against accidental overwrites.
- Least-privilege IAM policy implemented for EC2 access.
- No AWS access keys stored on EC2 instances.

---

## Connectivity Validation

Verified secure access from the EC2 application server to Amazon S3 using AWS Systems Manager Session Manager.

Confirmed that the EC2 instance successfully assumed the IAM Role and accessed Amazon S3 using temporary AWS credentials.

---

## Operations Performed

Verified IAM Role.

```bash
aws sts get-caller-identity
```

Listed bucket contents.

```bash
aws s3 ls s3://employee-management-platform-rakesh2798
```

Uploaded a file.

```bash
echo "Employee Management Platform" > test.txt

aws s3 cp test.txt s3://employee-management-platform-rakesh2798/application-logs/
```

Downloaded the file.

```bash
aws s3 cp s3://employee-management-platform-rakesh2798/application-logs/test.txt .
```

Generated a Pre-Signed URL.

```bash
aws s3 presign s3://employee-management-platform-rakesh2798/application-logs/test.txt --expires-in 300
```

Verified Bucket Versioning by uploading multiple versions of the same object.

Configured a Lifecycle Rule to:

- Transition objects to Standard-IA after 30 days.
- Expire objects after 365 days.

---

## Production Best Practices Followed

- Private S3 bucket.
- Block Public Access enabled.
- Server-side encryption enabled.
- Bucket Versioning enabled.
- Least-privilege IAM policy implemented.
- IAM Role used instead of AWS access keys.
- Lifecycle Rule configured for storage cost optimization.
- Temporary access provided using Pre-Signed URLs.

---

## Key Learnings

- Why Amazon S3 is preferred over storing files on EC2.
- Using IAM Roles instead of long-term AWS credentials.
- Bucket Versioning for data protection.
- Server-side encryption for data at rest.
- Lifecycle Rules for storage cost optimization.
- Secure file sharing using Pre-Signed URLs.
- Difference between IAM Policies and Bucket Policies.

---

## Outcome

Successfully integrated Amazon S3 with the EC2 application servers using IAM Roles, implemented secure object storage with encryption and versioning, configured lifecycle management for cost optimization, and validated secure file upload, download, and temporary access using Pre-Signed URLs following AWS production best practices.

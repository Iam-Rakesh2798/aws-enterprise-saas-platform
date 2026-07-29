# Day 8 - AWS WAF and AWS Shield Standard

## Objective

Secure the Employee Management SaaS Platform by implementing AWS WAF and understanding AWS Shield Standard to protect the application against common web attacks and Distributed Denial of Service (DDoS) attacks.

---

## Architecture Overview

Implemented AWS WAF in front of the CloudFront distribution to inspect incoming HTTP/HTTPS requests before they reach the application infrastructure.

AWS Shield Standard automatically provides protection against common network and transport layer DDoS attacks, while AWS WAF protects against application-layer attacks such as SQL Injection and Cross-Site Scripting (XSS).

---

## AWS Services Used

- AWS WAF
- AWS Shield Standard
- Amazon CloudFront
- Application Load Balancer (ALB)
- Amazon S3
- Auto Scaling Group
- Amazon EC2
- Amazon RDS PostgreSQL

---

## Resources Configured

### AWS WAF

- Created Web ACL
- Associated Web ACL with CloudFront Distribution
- Enabled AWS Managed Rule Groups
- Configured Rate-Based Rule

### Managed Rule Groups

- AWS Managed Amazon IP Reputation List
- AWS Managed Common Rule Set
- AWS Managed Known Bad Inputs Rule Set

### Rate Limiting

- Rule Name: RateLimit-Per-IP
- Aggregate Key: IP Address
- Limit: 1000 Requests
- Evaluation Window: 5 Minutes
- Action: Count Mode

---

## Security Implementation

- Web ACL associated with CloudFront distribution.
- Managed rule groups enabled for common web attack protection.
- Rate-based rule configured to detect excessive requests from a single IP.
- Shield Standard automatically protects against Layer 3 and Layer 4 DDoS attacks.
- All managed rules configured in Count mode for monitoring before enforcing Block mode.

---

## Validation Performed

Verified Web ACL association with CloudFront.

Reviewed:

- Managed Rule Groups
- Rule Priorities
- Sampled Requests
- Allowed Request Metrics

Tested application access through CloudFront after enabling WAF protection.

Verified that all requests were allowed while rules were operating in Count mode.

---

## WAF Rules Configured

### AWS Managed Amazon IP Reputation List

Protects against requests originating from IP addresses with poor reputation based on AWS threat intelligence.

### AWS Managed Common Rule Set

Protects against common web exploits including malformed requests and known attack patterns.

### AWS Managed Known Bad Inputs Rule Set

Detects malicious payloads commonly used in SQL Injection, Cross-Site Scripting (XSS), and other application attacks.

### Rate-Based Rule

Monitors request rates from individual client IP addresses and can block excessive traffic to mitigate brute-force attacks and basic DDoS attempts.

---

## AWS Shield Standard

AWS Shield Standard is automatically enabled for supported AWS services and provides protection against common Layer 3 and Layer 4 DDoS attacks.

No manual configuration is required.

---

## Production Best Practices Followed

- Attached WAF to CloudFront instead of EC2 instances.
- Used AWS Managed Rule Groups.
- Started all rules in Count mode before switching to Block mode.
- Implemented Rate-Based Rule for abusive traffic detection.
- Kept CloudFront as the public entry point.
- Leveraged AWS Shield Standard for automatic DDoS protection.

---

## Key Learnings

- Difference between AWS WAF and AWS Shield Standard.
- Understanding Web ACLs and Managed Rule Groups.
- Difference between Count mode and Block mode.
- Configuring Rate-Based Rules.
- Protecting applications at the CloudFront layer.
- Difference between Layer 3/4 and Layer 7 attacks.
- Why Security Groups alone are not sufficient for web application security.

---

## Outcome

Successfully secured the Employee Management SaaS Platform by implementing AWS WAF with managed rule groups and rate limiting while understanding how AWS Shield Standard automatically protects the infrastructure against common DDoS attacks. The application is now protected using multiple security layers following AWS production best practices.
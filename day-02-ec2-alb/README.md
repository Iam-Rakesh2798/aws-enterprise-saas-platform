# Day 2 – Compute Layer and Load Balancing

## Overview

This phase introduces the application layer by deploying Amazon EC2 instances within private subnets and exposing the application through an Application Load Balancer (ALB).

Secure administration was implemented using AWS Systems Manager Session Manager, eliminating the need for SSH access. Amazon CloudWatch Agent was configured for infrastructure monitoring.

---

## Architecture

Refer to:

architecture/day-02-ec2-alb-architecture.png

---

## AWS Services Used

- Amazon EC2
- Application Load Balancer
- Target Group
- IAM Roles
- AWS Systems Manager
- Amazon CloudWatch
- CloudWatch Agent
- Security Groups

---

## Infrastructure Created

- IAM Role for EC2
- Instance Profile
- Launch Template
- Two EC2 Instances
- Target Group
- Application Load Balancer
- CloudWatch Agent Configuration
- Systems Manager Integration

---

## Application Deployment

The Employee Management Platform was deployed on two EC2 instances.

The application was served using Nginx.

Application availability was verified using:

```
curl localhost
```

---

## Validation

Verified:

- EC2 instances running successfully.
- Systems Manager Session Manager connectivity.
- IAM role attached correctly.
- CloudWatch Agent running.
- Target Group healthy.
- ALB DNS accessible.
- Load balancing functioning correctly.

---

## Monitoring

CloudWatch Agent was configured to collect:

- CPU Utilization
- Memory Usage
- Disk Usage
- Network Metrics

---

## Key Learnings

- Deploying applications on private EC2 instances.
- Configuring Application Load Balancer.
- Target Group health checks.
- Secure administration using Session Manager.
- CloudWatch monitoring.
- IAM Roles for EC2.

---

## Outcome

A highly available application layer was deployed behind an Application Load Balancer with centralized monitoring and secure administrative access.

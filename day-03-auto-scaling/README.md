# Day 3 – Auto Scaling and High Availability

## Overview

The third phase enhances application availability by introducing Amazon EC2 Auto Scaling.

A Launch Template was created to standardize EC2 configuration, and an Auto Scaling Group was configured to automatically maintain the desired number of application instances across multiple Availability Zones.

The Application Load Balancer distributes incoming traffic while the Auto Scaling Group replaces unhealthy instances automatically.

---

## Architecture

Refer to:

architecture/day-03-auto-scaling-architecture.png

---

## AWS Services Used

- EC2 Launch Template
- Auto Scaling Group
- Application Load Balancer
- Target Group
- Amazon CloudWatch
- CloudWatch Agent
- AWS Systems Manager

---

## Infrastructure Created

- Launch Template
- Auto Scaling Group
- Target Group Integration
- Health Checks
- Multi-AZ Deployment

---

## Auto Scaling Configuration

| Setting | Value |
|----------|-------|
| Desired Capacity | 2 |
| Minimum Capacity | 0 |
| Maximum Capacity | 4 |
| Health Check | EC2 + ALB |
| Availability Zones | 2 |

---

## Validation

Verified:

- Launch Template created successfully.
- Auto Scaling Group launched EC2 instances.
- Target Group reported healthy instances.
- ALB distributed traffic correctly.
- CloudWatch Agent operational.
- Session Manager connectivity verified.

---

## High Availability

The application was deployed across two Availability Zones to improve fault tolerance.

If an instance becomes unhealthy, the Auto Scaling Group automatically replaces it, ensuring continuous application availability.

---

## Key Learnings

- Launch Templates.
- Auto Scaling Groups.
- Health Checks.
- Self-Healing Infrastructure.
- Elastic Scaling.
- High Availability Design.

---

## Outcome

The application infrastructure now supports automatic instance replacement, multi-AZ deployment, and scalable compute capacity, providing a resilient and production-ready application environment.

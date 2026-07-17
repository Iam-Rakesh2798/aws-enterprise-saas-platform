# Day 1 – AWS Networking Foundation

## Overview

The first phase of the AWS Enterprise SaaS Platform focuses on designing a secure and highly available networking foundation. A custom Amazon VPC was created with public and private subnets distributed across two Availability Zones to support future application and database deployments.

This networking design follows AWS best practices by separating internet-facing resources from application and database resources.

---

## Architecture

Refer to:

architecture/day-01-vpc-architecture.png

---

## AWS Services Used

- Amazon VPC
- Public Subnets
- Private Application Subnets
- Private Database Subnets
- Internet Gateway
- NAT Gateway
- Elastic IP
- Route Tables
- Security Groups
- Network ACLs

---

## Infrastructure Created

- Custom VPC
- 2 Public Subnets
- 2 Private Application Subnets
- 2 Private Database Subnets
- Internet Gateway
- NAT Gateway
- Elastic IP
- Public Route Table
- Private Route Table
- Security Groups

---

## Network Design

| Resource | Configuration |
|----------|---------------|
| VPC CIDR | 10.0.0.0/16 |
| Public Subnets | 2 |
| Private Application Subnets | 2 |
| Private Database Subnets | 2 |
| Availability Zones | 2 |
| NAT Gateway | 1 |
| Internet Gateway | 1 |

---

## Validation

Verified:

- Public subnets have internet connectivity.
- Private subnets access the internet through the NAT Gateway.
- Route tables are associated with the correct subnets.
- Security groups allow only the required traffic.

---

## Key Learnings

- Designing production-ready VPC architectures.
- Public vs Private subnet design.
- Internet Gateway and NAT Gateway configuration.
- Route table associations.
- Security group implementation.
- High Availability networking design.

---

## Outcome

A secure and scalable networking foundation was successfully created for subsequent deployment of compute, load balancing, databases, and monitoring services.

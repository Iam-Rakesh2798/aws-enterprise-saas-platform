# Day 1 - VPC and Networking

**Date:** 15 July 2026

**Status:** ✅ Completed

## Objective

Build a production-ready AWS network for the Employee Management SaaS Platform.

---

## Resources Created

- Custom VPC (Employee-SaaS-VPC)
- 2 Public Subnets
- 2 Private Application Subnets
- 2 Private Database Subnets
- Internet Gateway
- Public Route Table
- Application Route Table
- Database Route Table
- NAT Gateway (created for testing)
- Elastic IP (associated with NAT Gateway)
- Security Group for testing
- Public EC2 Instance
- Private EC2 Instance

---

## Network Architecture

- Internet-facing resources are deployed in Public Subnets.
- Application servers are deployed in Private Application Subnets.
- Database resources are planned for Private Database Subnets.
- Internet access for private resources is provided through a NAT Gateway.

---

## Validation Performed

- Verified Public EC2 received a Public IP.
- Verified Private EC2 did not receive a Public IP.
- Confirmed route table configuration.
- Tested outbound internet access through the NAT Gateway.
- Stopped EC2 instances after validation.
- Deleted the NAT Gateway and released the Elastic IP to minimize AWS costs.

---

## Key Learnings

- Why a custom VPC is preferred over the default VPC.
- Difference between an Internet Gateway and a NAT Gateway.
- Purpose of route tables.
- Importance of subnet isolation.
- Benefits of Multi-AZ architecture.
- Why private instances should not have public IP addresses.

---

## Next Steps

- Deploy compute resources.
- Configure IAM Roles.
- Install Docker.
- Deploy the Employee Management application.
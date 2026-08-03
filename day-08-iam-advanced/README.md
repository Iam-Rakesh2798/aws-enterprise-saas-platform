# Day 8 – Advanced IAM (Enterprise Identity & Access Management)

## Overview

The ninth phase focuses on implementing a secure Identity and Access Management (IAM) architecture following the Principle of Least Privilege.

IAM Groups and IAM Users were created to organize access based on job roles. Customer Managed Policies were implemented to provide fine-grained permissions, while a Permission Boundary was applied to restrict the maximum permissions a user can obtain.

An IAM Role was configured with Amazon S3 Read-Only access and tested using AWS Security Token Service (STS) to generate temporary credentials. Multi-Factor Authentication (MFA) and IAM Access Analyzer were also configured to improve account security and identify unintended resource access.

---

## Architecture

Refer to:

```
architecture/day-09-iam-architecture.png
```

---

## AWS Services Used

- AWS Identity and Access Management (IAM)
- AWS Security Token Service (STS)
- IAM Access Analyzer
- Multi-Factor Authentication (MFA)

---

## Infrastructure Created

- IAM Groups
- IAM Users
- Customer Managed Policies
- Permission Boundary
- IAM Role
- Virtual MFA Device
- IAM Access Analyzer

---

## IAM Configuration

| Resource | Configuration |
|----------|---------------|
| IAM Groups | Developers, DevOps, DBA, Security |
| IAM Users | 4 Test Users |
| IAM Role | S3ReadOnlyRole |
| Permission Boundary | MaximumAllowedPermissions |
| MFA | Virtual MFA Device |
| Access Analyzer | Account Analyzer |

---

## Validation

Verified:

- IAM Groups created successfully.
- IAM Users assigned to appropriate groups.
- Customer Managed Policies attached successfully.
- Permission Boundary applied to developer-user.
- IAM Role assumed successfully using AWS STS.
- Temporary credentials generated successfully.
- MFA enabled and verified.
- IAM Access Analyzer created and active.

---

## Security Implementation

The IAM environment was designed using the Principle of Least Privilege by granting only the permissions required for each team.

Customer Managed Policies were assigned through IAM Groups, Permission Boundaries restricted maximum permissions, and IAM Roles with AWS STS provided temporary credentials instead of long-term access keys.

MFA was enabled to strengthen user authentication, while IAM Access Analyzer continuously evaluates resource policies for unintended public or cross-account access.

---

## Key Learnings

- IAM Users vs IAM Roles.
- IAM Groups.
- Customer Managed Policies.
- Permission Boundaries.
- Principle of Least Privilege.
- AWS STS.
- Temporary Credentials.
- Multi-Factor Authentication (MFA).
- IAM Access Analyzer.
- IAM Policy Evaluation Logic.

---

## Outcome

Successfully implemented an enterprise IAM architecture using IAM Groups, Customer Managed Policies, Permission Boundaries, IAM Roles, AWS STS, MFA, and IAM Access Analyzer to provide secure, scalable, and production-ready access management for AWS resources.
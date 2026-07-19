# Day 4 - Amazon RDS PostgreSQL

## Objective

Build a secure and production-style database layer for the Employee Management SaaS Platform using Amazon RDS PostgreSQL.

---

## Architecture Overview

Implemented a managed PostgreSQL database in private subnets to provide secure, scalable, and highly available data storage for the application layer.

The database is accessible only from the application servers running inside the private application subnets through dedicated security groups.

---

## AWS Services Used

- Amazon RDS PostgreSQL
- DB Subnet Group
- Security Groups
- AWS KMS
- AWS Systems Manager (SSM)

---

## Resources Created

### Database

- Engine: PostgreSQL
- Template: Free Tier
- Deployment: Single-AZ
- Instance Class: db.t4g.micro
- Storage: 20 GB (gp3)
- Encryption: Enabled
- Public Access: Disabled

### Networking

- Custom VPC
- Private DB Subnet Group
- Database Security Group
- Application Security Group

### Database Configuration

- Database Name: employee_management
- Master User: postgres

---

## Security Implementation

- Database deployed inside private subnets.
- Public accessibility disabled.
- PostgreSQL port (5432) allowed only from the application security group.
- Storage encryption enabled using AWS KMS.
- Automated backups configured.

---

## Connectivity Validation

Verified secure connectivity from the EC2 application server to Amazon RDS using AWS Systems Manager Session Manager.

Installed PostgreSQL client on Amazon Linux and successfully established an SSL-encrypted connection to the RDS instance.

---

## Database Operations Performed

Created Employees table.

```sql
CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    department VARCHAR(100),
    email VARCHAR(200),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

Inserted sample employee data.

```sql
INSERT INTO employees
(first_name,last_name,department,email)
VALUES
('Rakesh','K','Cloud','raki2798@gmail.com');
```

Verified records.

```sql
SELECT * FROM employees;
```

Checked table structure.

```sql
\d employees
```

Counted records.

```sql
SELECT COUNT(*) FROM employees;
```

---

## Production Best Practices Followed

- Database deployed in private subnets.
- Public access disabled.
- Dedicated security groups implemented.
- Encryption at rest enabled.
- Automated backups configured.
- SSL encrypted database connection.
- Principle of least privilege applied for network access.

---

## Key Learnings

- Difference between Amazon RDS and self-managed PostgreSQL.
- Importance of DB Subnet Groups.
- Secure database deployment using private subnets.
- Security Group-based database access.
- Connecting to RDS using Session Manager.
- Basic PostgreSQL administration and SQL operations.
- Importance of encryption and automated backups.

---

## Outcome

Successfully deployed a secure Amazon RDS PostgreSQL database, validated connectivity from private EC2 instances, and performed basic database administration tasks following AWS production best practices.

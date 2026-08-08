# Day 9 - Monitoring & Observability

## Objective

Implement a production-style monitoring, logging, and alerting solution for the
Employee Management SaaS Platform using Amazon CloudWatch.

The objective was to monitor EC2 infrastructure metrics, collect Nginx
application logs, centralize logs in CloudWatch, store the CloudWatch Agent
configuration in AWS Systems Manager Parameter Store, and configure CloudWatch
Alarms with Amazon SNS notifications.

---

## AWS Services Used

- Amazon CloudWatch
- CloudWatch Agent
- CloudWatch Metrics
- CloudWatch Logs
- CloudWatch Alarms
- Amazon SNS
- AWS Systems Manager
- SSM Parameter Store
- AWS IAM
- Amazon EC2
- Nginx

---

## CloudWatch Agent

Installed the Amazon CloudWatch Agent on the private EC2 application server.

The CloudWatch Agent is responsible for collecting metrics and logs that are
not provided directly by the default EC2 monitoring.

The agent was configured to run as:

```text
root
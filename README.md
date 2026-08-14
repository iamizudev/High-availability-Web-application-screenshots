# AWS High Availability Infrastructure

Hands-on AWS infrastructure project focused on designing and testing a highly available web application architecture across multiple Availability Zones.

## 📌 Project Overview

This project was built as a **learning and testing environment**, not a production deployment.

The infrastructure was later taken down to avoid unnecessary ongoing AWS costs. This repository preserves screenshots and documentation of the infrastructure that was created and tested.

## 🏗️ Infrastructure Components

* Amazon VPC
* Public & Private Subnets
* Internet Gateway
* NAT Gateway
* Route Tables
* Security Groups
* Amazon EFS
* EFS Access Point
* EC2
* Bastion Host
* Launch Template
* Auto Scaling Group
* Application Load Balancer
* Target Group
* Route 53
* AWS Certificate Manager
* Datadog
* Slack Notifications

## 🔐 Architecture

The application architecture used public subnets for internet-facing components and private subnets for application instances.

```text
Users
  │
  ▼
Route 53
  │
  ▼
Application Load Balancer
  │
  ▼
Target Group
  │
  ▼
Private EC2 Instances
  │
  ▼
Web Application
```

Monitoring was configured through:

```text
EC2 → Datadog → Slack
```

## 🧪 Troubleshooting

During testing, several real infrastructure issues were encountered.

### Unhealthy Targets

The Target Group initially showed multiple unhealthy instances.

### 403 Forbidden

Nginx returned a `403 Forbidden` response while testing the application.

### 503 Service Unavailable

A `503 Service Temporarily Unavailable` response was also encountered during ALB/application testing.

These issues required troubleshooting across the request path:

```text
DNS
 ↓
ALB
 ↓
Target Group
 ↓
Security Groups
 ↓
EC2
 ↓
Nginx
 ↓
Application
```

These troubleshooting scenarios were an important part of the project and helped reinforce practical AWS debugging skills.

## 📸 Screenshots

The `screenshots/` directory contains visual evidence of the infrastructure configuration, monitoring, testing, and troubleshooting performed during the project.

## 💡 Key Takeaways

* Multi-AZ architecture improves availability.
* Load Balancers depend on healthy targets.
* Security Groups must allow the required traffic between infrastructure layers.
* HTTP status codes can help identify where an application request is failing.
* Auto Scaling and Target Groups work together to provide resilient application delivery.
* Monitoring and alerting are important parts of cloud infrastructure.
* Cloud infrastructure should also be managed with cost awareness.

## ⚠️ Project Status

**Completed — Infrastructure Decommissioned**

The AWS resources were intentionally removed after testing to prevent unnecessary cloud costs.

The screenshots and documentation remain available in this repository as a record of the project.

## 👤 Author

**Ozoude Emmanuel**

Cloud Engineering | AWS Infrastructure

## 🙏🏽 Acknowledgements

Special thanks to **Digital Witch** and **MrSmart Agbawo** for the knowledge, guidance, and resources that contributed to my cloud engineering journey.

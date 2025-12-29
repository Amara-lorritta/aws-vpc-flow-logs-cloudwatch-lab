AWS VPC Flow Logs with CloudWatch

VPC • CloudWatch • Flow Logs | Networking & Security Monitoring

This lab demonstrates how I enabled VPC Flow Logs and delivered network traffic data to Amazon CloudWatch Logs. The setup provides visibility into accepted traffic within a VPC and supports security monitoring, troubleshooting, and network analysis.

📌 Overview

In this lab, I created a CloudWatch Log Group, provisioned a custom VPC, and enabled VPC Flow Logs to capture accepted traffic. The flow logs were configured to publish directly to CloudWatch Logs using an IAM role, allowing centralized monitoring of VPC network activity.

🔧 Tools Used

Amazon VPC — custom VPC creation and traffic monitoring

VPC Flow Logs — capture IP traffic metadata

Amazon CloudWatch Logs — centralized log storage and analysis

IAM Role — permissions for VPC to publish logs

AWS Management Console — configuration and validation

🏗️ Architecture Diagram

Architecture Summary

Custom VPC: whizvpc (10.1.0.0/16)

VPC Flow Logs enabled (Accepted traffic)

Logs delivered to CloudWatch Log Group whizvpclogs

IAM role allowing VPC to publish logs

⚙️ Implementation Steps
```bash
############################################################
# 1. SIGN IN TO AWS MANAGEMENT CONSOLE
############################################################
# - Click Open Console from lab portal
# - Use provided IAM Username + Password
# - Do NOT edit the 12-digit Account ID
# - Set region: us-east-1 (N. Virginia)

############################################################
# 2. CREATE CLOUDWATCH LOG GROUP
############################################################
# CloudWatch → Logs → Log Groups → Create log group
#   - Log Group Name: whizvpclogs
# Ignore CloudWatch metrics fetch errors (if any)

############################################################
# 3. CREATE A VPC
############################################################
# VPC → Your VPCs → Create VPC
#   - Resources: VPC only
#   - Name: whizvpc
#   - IPv4 CIDR: 10.1.0.0/16
#   - IPv6: None
#   - Tenancy: Default

############################################################
# 4. CREATE VPC FLOW LOGS
############################################################
# VPC → whizvpc → Flow Logs → Create flow log
# Flow log settings:
#   - Name: whizflow
#   - Filter: Accept
#   - Destination: CloudWatch Logs
#   - Log Group: whizvpclogs
#   - IAM Role: VPCFlowLog<RANDOM_NUMBER>
# Leave other options as default and create flow log

############################################################
# 5. VERIFY FLOW LOG CREATION
############################################################
# VPC → whizvpc → Flow Logs tab
# Confirm status shows ACTIVE
############################################################
```
ScreeShoots
CloudWatch Log Group Created
VPC Details Page
VPC Flow Logs Configuration
CloudWatch Log Stream Entries
Key Takeaways

VPC Flow Logs provide visibility into network traffic at the VPC level

Flow Logs can be delivered directly to CloudWatch Logs for monitoring and analysis

IAM roles are required for VPC Flow Logs to publish data securely

Filtering on Accepted traffic helps reduce noise and focus on allowed connections

Flow Logs support security analysis, troubleshooting, and performance insights

Author:

Amarachi Emeziem

Cloud Security Engineer / AWS re/Start Graduate.

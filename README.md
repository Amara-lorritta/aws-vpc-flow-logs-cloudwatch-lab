## **AWS VPC Flow Logs with CloudWatch**

VPC • CloudWatch • Flow Logs | Networking & Security Monitoring



## **Overview**

This lab demonstrates how I enabled VPC Flow Logs and delivered network traffic data to Amazon CloudWatch Logs. The setup provides visibility into accepted traffic within a VPC and supports security monitoring, troubleshooting, and network analysis.

In this lab, I created a CloudWatch Log Group, provisioned a custom VPC, and enabled VPC Flow Logs to capture accepted traffic. The flow logs were configured to publish directly to CloudWatch Logs using an IAM role, allowing centralized monitoring of VPC network activity.

## **Tools Used**

Amazon VPC — custom VPC creation and traffic monitoring

VPC Flow Logs — capture IP traffic metadata

Amazon CloudWatch Logs — centralized log storage and analysis

IAM Role — permissions for VPC to publish logs

AWS Management Console — configuration and validation

## **Architecture Diagram**

## Architecture Summary

Custom VPC: whizvpc (10.1.0.0/16)

VPC Flow Logs enabled (Accepted traffic)

Logs delivered to CloudWatch Log Group whizvpclogs

IAM role allowing VPC to publish logs

## **Implementation Steps**

```bash
############################################################
# 1. SIGN IN TO AWS MANAGEMENT CONSOLE
############################################################

############################################################
# 2. CREATE CLOUDWATCH LOG GROUP
############################################################
# CloudWatch → Logs → Log Groups → Create log group
#   - Log Group Name: Amavpclogs


############################################################
# 3. CREATE A VPC
############################################################
# VPC → Your VPCs → Create VPC
#   - Resources: VPC only
#   - Name: Myvpc
#   - IPv4 CIDR: 10.1.0.0/16
#   - IPv6: None
#   - Tenancy: Default

############################################################
# 4. CREATE VPC FLOW LOGS
############################################################
# VPC → whizvpc → Flow Logs → Create flow log
# Flow log settings:
#   - Name: Amaflow
#   - Filter: Accept
#   - Destination: CloudWatch Logs
#   - Log Group: Mvpclogs
#   - IAM Role: VPCFlowLog........


############################################################
# 5. VERIFY FLOW LOG CREATION
############################################################
# VPC → Myvpc → Flow Logs tab
# Confirm status shows ACTIVE
############################################################
```

## **ScreeShoots**

CloudWatch Log Group Created
<img width="1890" height="322" alt="image" src="https://github.com/user-attachments/assets/3f62b604-1c4e-43df-9c4c-5fb3c5d086b7" />

VPC Details Page
<img width="1644" height="566" alt="image" src="https://github.com/user-attachments/assets/9726d13c-5372-4361-9bc9-f09bc4b475ec" />

VPC Flow Logs Configuration
<img width="1578" height="291" alt="image" src="https://github.com/user-attachments/assets/ad3c5a67-e89c-4c4d-847e-edccd70b4dcc" />


## **Key Takeaways**

VPC Flow Logs provide visibility into network traffic at the VPC level

Flow Logs can be delivered directly to CloudWatch Logs for monitoring and analysis

IAM roles are required for VPC Flow Logs to publish data securely

Filtering on Accepted traffic helps reduce noise and focus on allowed connections

Flow Logs support security analysis, troubleshooting, and performance insights

## **Author**:

Amarachi Emeziem

Cloud Security Engineer / AWS re/Start Graduate.

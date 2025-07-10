---
title : "Prerequisite Steps"
date: "2025-06-17"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### AWS Account

First, you need to have a valid AWS account that you can log into the AWS Management Console. If you don't have one, you need to sign up and add an international payment card (Visa/Mastercard). This account allows you to use all AWS services, including SES, Lambda, and API Gateway.

You can sign up at https://aws.amazon.com/free/ to receive 12 months of some limited services for free.

#### Verified SES Email Identity

To use Amazon Simple Email Service (SES) to send emails, you must verify your email (or domain) in SES first. If you do not verify, you will not be able to send emails or will only be able to send them in the sandbox (only to yourself).

1. Steps:
   - Search for **AWS SES Console** then click in **Identities** in the left-side bar.
   ![SES](image.png)
   - Click on **Create Indentity** and tick on **Email Address** then click again **Create Identity**.
   ![SES](image-1.png)
   - Go to your email and click on the link to verify.

2. IAM Role with Permissions 
   You need an IAM Role for the Lambda function to execute. This role must have at least: 

   - AWSLambdaBasicExecutionRole (to log to CloudWatch).
   - AmazonSESFullAccess (to send emails via SES).
   - Steps:

      1. Go to **IAM Console**, select **Roles** on the left-side bar then click **Create Role**
      ![IAM Console](image-2.png)
      2. Choose **Lambda** as use case.
      3. Attach policies:
      - **AWSLambdaBasicExecutionRole**
      - **AmazonSESFullAccess**
      4. Give a clear name (example: **Lambda-SESSendEmail-Role**) and create the role.
   
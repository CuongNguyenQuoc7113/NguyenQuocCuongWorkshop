---
title : "Monitoring and Logs"
date: "2025-06-17"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

**Content:**
- [Definition](#definition)
- [Why do we need monitoring and logs?](#why-do-we-need-monitoring-logs)
- [Prerequisite](#prerequisite)
- [Steps](#steps)

## Definition

Monitoring and Logs is monitoring the system activities and viewing detailed logs for debugging, optimization, or ensuring stable application performance.

## Why do we need monitoring and logs?

To helps check if Lambda function runs successfully, and easily debug errors when API Gateway ➔ Lambda ➔ SES fails. Monitor invocations, duration, and errors to optimize cost.

## Prerequisite

Before starting, ensure:
- Lambda function is successfully deployed.
- You have access to AWS CloudWatch Logs.
- Basic understanding of CloudWatch Alarm to create alerts if needed.

## Steps

1. Go to **AWS Management Console**, Search for **CloudWatch** service.
   In the left menu, select Logs ➔ Log groups.

   Find your Lambda function **Log group** with format:

   ```/aws/lambda/YourFunctionName```
   ![AWS Cloudwatch](image.png)
   Click on the **Log group** ➔ Select the latest log stream
   ![AWS Cloudwatch](image-1.png)
   ➔ View detailed logs.
   For example:

   ```START RequestId: xxx Version: $LATEST
   Event received: {event data}
   SES send_email response: {response data}
   END RequestId: xxx
   REPORT RequestId: xxx Duration: xxx ms Billed Duration: xxx ms Memory Size: xxx MB Max Memory Used: xxx MB```

   (Meaning: Shows function ran, received input, returned output, execution time, and memory usage.)

   ![AWS Cloudwatch](image-2.png)


2. Create CloudWatch Alarm (Optional)

   CloudWatch Alarm is an alert triggered when a metric crosses a defined threshold, e.g. Lambda errors exceed allowed count.

   - Go to **CloudWatch Console**, on the left side-bar select **All Alarms**, then click **Create alarm**.
   ![AWS Cloudwatch](image-3.png)
   - Click on **Select metric** button, and choose **Lambda** ➔ **By Function Name** ➔ **Errors**
   ![AWS Cloudwatch](image-4.png)
   ![AWS Cloudwatch](image-5.png)
   ![AWS Cloudwatch](image-6.png)
   - In here, if you do not have any SNS topics created previously, the Select an SNS topic field is showing Required.
   ![AWS Cloudwatch](image-7.png)
   So here is a quick guide: Create an **SNS topic** to use for the Alarm.
   - Choose the **SNS(Simple Notification Service)** in AWS Console.
   - Choose and name the **Create topic** ➔ choose **Standard**.
   - Topic name: for example **AlarmNotificationTopic** ➔ click **Create Topic**.
   ![AWS SNS](image-8.png)
   ![AWS SNS](image-9.png)
   - In the topic you just created, select **Create subscription**.
   ![AWS SNS](image-10.png)
      - Protocol: choose Email.
      - Endpoint: Enter the email you want to receive notifications (example: yourmail@gmail.com).
      ![AWS SNS](image-11.png)
   - Go to your email ➔ Confirm **Subscription**.
   ![AWS SNS](image-12.png)
   After creating the **SNS topic** and **Subscription**, go back to **CloudWatch Alarm**, reload, and you will see the **SNS topic** appear in the list. Select it, then continue:
   - Name the alart. example: **LambdaSESErrorAlarmTopic**
   ![AWS Cloudwatch](image-13.png)
   - Preview and click **Create Alarm**
   ![AWS Cloudwatch](image-14.png)
   ![AWS Cloudwatch](image-15.png)
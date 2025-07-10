---
title : "Clean Up Resources"
date: "2025-06-17"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### The reason for cleaning resources

When completing a project or lab exercise on AWS, cleaning up unused resources is very important. This helps:
- Avoid unnecessary costs.
- Keep your AWS account organized.
- Improve security by reducing attack surface.

#### Steps

1. Delete **API Gateway**:
   - Step 1: Go to API Gateway service in console
   - Step 2: Select your created API
   - Step 3: Click Actions, then Delete API, and confirm

---

2. Delete **Lambda function**:
   - Step 1: Go to Lambda Console, select Functions.
   - Step 2: Search your function.
   - Step 3: Delete it to avoid charges.

---

3. Delete **SES verified email identity** if not needed.
   - Step 1: Go to SES Console ➔ Identities.
   - Step 2: Delete verified email if no longer needed

---

4. Delete **SNS topic** (if you have created one):
   - Step 1: Go to SNS Console ➔ Topics.
   - Step 2: Delete SNS topic if not needed anymore.

5. Delete **CloudWatch Alarm**:
   - Step 1: Go to CloudWatch Console ➔ Alarms.
   - Step 2: Delete alarm to stop monitoring and avoid charges.
---

Remember to keep your MFA devices secure and follow best practices to ensure the safety of your account.

---
title : "Create API Gateway Endpoint"
date: "2025-06-17"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

**Content:**
- [Definition](#definition)
- [Why do we need API Gateway?](#why-do-we-need-api-gateway)
- [Prerequisite](#prerequisite)
- [Steps](#steps)

#### Definition

Amazon API Gateway is a fully managed service that makes it easy to create, publish, maintain, monitor, and secure APIs at any scale.

#### Why do we need API Gateway?

1. Allow the frontend (web page) to easily send requests to the Lambda function through a URL endpoint.

2. We can manage security, authentication, limit requests, and monitor the API. 

3. It helps to separate the frontend and backend, while also making maintenance easier.

#### Prerequisite

To perform this section, ensure you have:
  - The Lambda function has been created and deployed.
  - The IAM role of the Lambda function has AmazonSESFullAccess permission.
  - Logged in to the AWS Management Console with permissions to create API Gateway and assign permissions to the Lambda function.

#### Steps

1. Go to **AWS Search Bar**, Search for **API Gateway** service then click in.
   In the [API Gateway], select **Create API** on the top right.

   ![API Gateway Console](image.png)

This is where you manage all your APIs in AWS.

2. Choose **Rest API** and select **Build** button next to it.

   ![API Gateway Console](image-1.png)

REST API is suitable for traditional apps, web backends, or microservices requiring multiple HTTP methods.

3. Enter **API details**:
   - Select **New API**.
   - API name: SendEmailAPI.
   - Description is Optional, so you can  enter information if you want.
   - Endpoint Type: Regional
   - Click **Create API** to create.

   ![API Gateway Console](image-2.png)

   ![API Gateway Console](image-3.png)

   Created successfully:

   ![API Gateway Console](image-4.png)

4. Create **resource /sendemail**

   - Click to your API name that you just created then select **Create Resource** button.

   ![API Gateway Console](image-5.png)

   - Resource Name: sendemail 
   You can click to CORS (Cross Origin Resource Sharing) if you want since it help create an OPTIONS method that allows all origins, all methods, and several common headers.

   ![API Gateway Console](image-6.png)


5. Create **POST method for /sendemail**

   Click on **resource /sendemail** and select the **Create Method** then Choose **Post** from the **Method Type**

   ![API Gateway Console](image-8.png)
   then click **Create Method** button
   ![API Gateway Console](image-9.png)
   after created successfully: 
   ![API Gateway Console](image-10.png)
   POST method is used to send data from client to server. Here, we send email content from frontend to Lambda to send via SES.

6. **Enable CORS** for /sendemail POST method

   Click on **resource /sendemail** and select the **Enable CORS** button 
   ![API Gateway Console](image-11.png)
   In the popup, make sure:
   - Access-Control-Allow-Origin: *
   - Access-Control-Allow-Methods: OPTIONS,POST
   then click Save.
   ![API Gateway Console](image-12.png)
   Successfully saved: 
   ![API Gateway Console](image-13.png)
{{% notice note %}}
Why CORS? 
Because when frontend runs on a different domain (e.g., localhost:5500) calling API Gateway (another domain), browser blocks requests without CORS headers.
{{% /notice %}}

7. Deploy API to stage
   - Click on the **Deplou API** button then select **New stage** from Stage options.
   - Stage name: dev then Click **Deploy**
   ![API Gateway Console](image-14.png)
   After deploying, you will see Invoke URL like:
   (https://your-api-id.execute-api.ap-southeast-2.amazonaws.com/dev)
   This is the endpoint URL used by frontend to call API.
   ![API Gateway Console](image-15.png)

   
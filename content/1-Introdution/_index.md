---
title : "Introdution"
date: "2025-06-17"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

**Content:**
- [Specific Objectives](#specific-objectives)
- [Find Canonical User ID](#find-canonical-user-id)
- [Why do you need to know this information?](#why-do-you-need-to-know-this-information?)

    ![AWS Diagram](<AWSDiagram.drawio (1).png>)

#### Specific Objectives
In this section, you will learn how to identify your AWS account identifiers, including:

- AWS Account ID:
Your AWS Account ID is required when configuring services, granting permissions, or integrating with third parties.

- Canonical User ID:
A unique ID string mainly used in Amazon S3 to set up Access Control Lists (ACLs) and manage permissions between AWS accounts.

1. For root user:

Go to the AWS Management Console, click your account name or number at the top right corner, then choose Security credentials.

Your AWS Account ID will be displayed in the Account details section.

2. For IAM user:

Requires the permission `aws-portal:ViewAccount`. Steps are the same as for root user.

**Tip:** If you do not see Security credentials, you might be signed in as a federated user with an IAM role. In this case, look for the Account entry to view the account ID.

#### Find Canonical User ID

1. For root user or IAM user:

To perform the following steps, you must have at least the following IAM permission:

(In Security credentials, under Account details, you will see Canonical user ID.)

-> This ID is used when configuring ACLs for S3 buckets.

2. For federated user with IAM role:

In the Amazon S3 console, choose a bucket, go to the Permissions tab, and under Access control list, the Bucket owner section shows your account’s canonical ID.

#### Why do you need to know this information?

- AWS Account ID is used to set up trust policies, manage billing, and configure multi-account architectures.

- Canonical User ID is important when setting up cross-account S3 bucket permissions.

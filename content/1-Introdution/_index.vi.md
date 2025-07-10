---
title : "Giới thiệu"
date: "2025-06-17"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

**Content:**
- [Mục tiêu cụ thể](#mục-tiêu-cụ-thể)
- [Tìm Canonical User ID](#tìm-canonical-user-id)
- [Tại sao cần biết những thông tin này?](#tại-sao-cần-biết-những-thông-tin-này?)

#### Mục tiêu cụ thể
Trong phần này, bạn sẽ học cách xác định thông tin nhận dạng (identifiers) của tài khoản AWS, bao gồm:

- AWS Account ID:
Số ID tài khoản AWS của bạn, cần thiết khi cấu hình dịch vụ, cấp quyền, hoặc tích hợp với bên thứ ba.

- Canonical User ID:
Một chuỗi ID đặc biệt được sử dụng chủ yếu trong Amazon S3 để thiết lập ACL (Access Control List) và phân quyền giữa các tài khoản AWS.

1. Đối với root user

Vào AWS Management Console, chọn tên hoặc số tài khoản ở góc trên bên phải, sau đó chọn Security credentials.

-> Số AWS account ID sẽ hiển thị trong phần Account details.

2. Đối với IAM user:

Cần quyền `aws-portal:ViewAccount`. Thao tác tương tự như root user.

**Tip:** Nếu không thấy Security credentials, bạn có thể đang đăng nhập qua federated user hoặc IAM role. Lúc này, hãy tìm mục Account để xem account ID.

#### Tìm Canonical User ID 

1. Đối với root user hoặc IAM user (For root user or IAM user):

Thực hiện trong Security credentials, dưới Account details sẽ có mục Canonical user ID.

-> ID này dùng khi cấu hình ACL cho bucket S3.

2. Đối với federated user với IAM role:

Vào Amazon S3 console, chọn bucket, tab Permissions, phần Access control list, mục Bucket owner sẽ hiển thị canonical ID của tài khoản

#### Tại sao cần biết những thông tin này? 

- AWS Account ID được sử dụng để thiết lập trust policies, quản lý billing, cấu hình multi-account architecture.

- Canonical User ID quan trọng khi thiết lập cross-account S3 bucket permissions.
 

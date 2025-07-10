---
title : "Dọn dẹp tài nguyên"
date: "2025-06-17" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Lý do cần dọn dẹp tài nguyên

Khi hoàn thành một dự án hoặc bài lab trên AWS, việc dọn dẹp các tài nguyên không sử dụng là rất quan trọng. Điều này giúp:
- Tránh phát sinh chi phí không cần thiết.
- Giữ tài khoản AWS gọn gàng, dễ quản lý.
- Nâng cao bảo mật bằng cách giảm bề mặt tấn công (attack surface).

#### Các bước

1. Xóa **API Gateway**:
   - Bước 1: Truy cập dịch vụ API Gateway trong console.
   - Bước 2: Chọn API bạn đã tạo.
   - Bước 3: Click Actions, chọn Delete API, và xác nhận.

---

2. Xóa **Lambda function**:
   - Bước 1: Vào Lambda Console, chọn Functions.
   - Bước 2: Tìm kiếm function của bạn.
   - Bước 3: Xóa function để tránh bị tính phí.

---

3. Xóa **SES verified email identity**  nếu không cần thiết.
   - Bước 1: Vào SES Console ➔ Identities.
   - Bước 2: Xóa email đã xác minh nếu không còn sử dụng.
---

4. Xóa **SNS topic** (nếu bạn đã tạo):
   - Bước 1: Vào SNS Console ➔ Topics.
   - Bước 2: Xóa SNS topic nếu không còn cần thiết.

5. Xóa **CloudWatch Alarm**:
   - Bước 1: Vào CloudWatch Console ➔ Alarms.
   - Bước 2: Xóa alarm để dừng giám sát và tránh phát sinh chi phí.

---

Hãy nhớ giữ thiết bị MFA (xác thực đa yếu tố) của bạn an toàn và luôn tuân theo các best practice (thực tiễn tốt nhất) để đảm bảo an toàn cho tài khoản của bạn.

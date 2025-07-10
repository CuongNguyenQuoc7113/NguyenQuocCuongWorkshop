---
title : "Frontend Integration Test"
date: "2025-06-17"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

**Content:**
- [Definition](#definition)
- [Why do we need integration testing?](#why-do-we-need-integration-testing)
- [Prerequisite](#prerequisite)
- [Steps](#steps)

#### Definition

Frontend Integration Test is the process of testing the connection between the user interface (frontend) and the API backend.

#### Why do we need integration testing?

To ensure frontend correctly calls the API, receives the response, and displays data properly. and detect early issues if API endpoint, method, CORS, or Lambda configuration is incorrect also to verify end-to-end flow: user inputs data ➔ API call ➔ Lambda processes ➔ SES sends email ➔ receive success response.

#### Prerequisite

Before starting, ensure:
- API Gateway endpoint is working and POST method returns 200 OK.
- Lambda function works correctly and has SES permission to send mail.
- SES identity (email or domain) is verified.
- Browser has internet access and can reach the API Gateway endpoint.

#### Steps

1. Create a web.html file.

   This is a simple HTML file to test sending email form via API Gateway ➔ Lambda ➔ SES.

```
<!DOCTYPE html>
<html>
<head>
    <title>Send Email via SES Lambda API</title>
</head>
<body>
    <h2>Send Email Form</h2>
    <form id="emailForm">
        To:<br>
        <input type="text" id="to" value="recipient@example.com"><br>
        Subject:<br>
        <input type="text" id="subject" value="Test email via SES Lambda"><br>
        Body:<br>
        <textarea id="body">hello,</textarea><br><br>
        <button type="submit">Send Email</button>
    </form>

    <script>
        document.getElementById('emailForm').addEventListener('submit', function(e) {
            e.preventDefault();
            fetch('YOUR_API_GATEWAY_URL/sendemail', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({
                    to: document.getElementById('to').value,
                    subject: document.getElementById('subject').value,
                    body: document.getElementById('body').value
                })
            })
            .then(res => res.json())
            .then(data => alert(data.message))
            .catch(err => console.error(err));
        });
    </script>
</body>
</html>
```

2. Next Step
Replace YOUR_API_GATEWAY_URL with the Invoke URL from your deployed API Gateway stage.
(Example:)
```
js
Copy
Edit
fetch('https://your-api-id.execute-api.ap-southeast-2.amazonaws.com/dev/sendemail'),
```
then run the website: 
![FE Integration Test](image.png)
Fill in the email details then Click Send Email, you'll see it shows "Email sent successfully!" if everything works.
![FE Integration Test](image-1.png)
Check recipient’s mailbox for the received email.
![FE Integration Test](image-2.png)

3. Troubleshooting

- CORS error: Check if CORS is enabled on API Gateway.
- Permission error: Check Lambda IAM Role has AmazonSESFullAccess.
- Email not received: SES sandbox allows sending only to verified emails.
- Fetch or 403 error: Check URL endpoint, method, and region.

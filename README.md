# API Documentation

## Send Public Email

This API endpoint allows users to send an email using their Gmail account. The user must provide their Gmail credentials, the recipient's email address, and the email content.

### Endpoint

- **URL**: `https://js-tech1.com/api/user/publicmail`
- **Method**: `POST`

### Request Headers

- `Content-Type: application/json`

### Request Body

The request body should be a JSON object containing the following fields:

- `gmail` (string): The sender's Gmail address.
- `password` (string): The sender's Gmail password. Note: It is recommended to use an [app password](https://support.google.com/accounts/answer/185833) for security purposes.
- `to` (string): The recipient's email address.
- `text` (string): A brief description of the email.
- `subject` (string): The subject of the email.
- `message` (string): The main content of the email.

#### Example Request

```json
{
  "gmail": "yourGmail@gmail.com",
  "password": "your app password",
  "to": "recipientGmail@gmail.com",
  "text": "contact from js-tech1",
  "subject": "hello there",
  "message": "this is the subject mail"
}
```

### Response

The response will be a JSON object containing the status of the email sending process.

#### Example Successful Response

```json
{
  "success": true
}
```

#### Example Error Response

```json
{
    "success": false,
    "error": {
        "code": "EAUTH",
        "response": "535-5.7.8 Username and Password not accepted. For more information, go to\n535 5.7.8  https://support.google.com/mail/?p=BadCredentials af79cd13be357-7a1d7444c91sm7217585a.115 - gsmtp",
        "responseCode": 535,
        "command": "AUTH PLAIN"
    }
}
```

### Error Handling

If the request fails, the API will return an error response with the appropriate status and error message.

### Code Examples

#### Axios (Node.js)

```javascript
const axios = require("axios");

let data = JSON.stringify({
  gmail: "yourGmail@gmail.com",
  password: "your app password",
  to: "recipientGmail@gmail.com",
  text: "contact from js-tech1",
  subject: "hello there",
  message: "this is the subject mail",
});

let config = {
  method: "post",
  maxBodyLength: Infinity,
  url: "https://js-tech1.com/api/user/publicmail",
  headers: {
    "Content-Type": "application/json",
  },
  data: data,
};

axios
  .request(config)
  .then((response) => {
    console.log(JSON.stringify(response.data));
  })
  .catch((error) => {
    console.log(error);
  });
```

#### Fetch (JavaScript)

```javascript
let data = JSON.stringify({
  gmail: "yourGmail@gmail.com",
  password: "your app password",
  to: "recipientGmail@gmail.com",
  text: "contact from js-tech1",
  subject: "hello there",
  message: "this is the subject mail",
});

let config = {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: data,
};

fetch("https://js-tech1.com/api/user/publicmail", config)
  .then((response) => response.json())
  .then((data) => {
    console.log(data);
  })
  .catch((error) => {
    console.error("Error:", error);
  });
```

#### cURL (Command Line)

```sh
curl -X POST https://js-tech1.com/api/user/publicmail \
-H 'Content-Type: application/json' \
-d '{
  "gmail": "yourGmail@gmail.com",
  "password": "your app password",
  "to": "recipientGmail@gmail.com",
  "text": "contact from js-tech1",
  "subject": "hello there",
  "message": "this is the subject mail"
}'
```
Watch the video below for a step-by-step guide on how to use the Send Public Email API:
<iframe width="560" height="315" src="https://www.youtube.com/embed/zENRKjBcHGk?si=9802bEQvSCGfRMCM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

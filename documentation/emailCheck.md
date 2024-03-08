# Function Name: checkIfEmailAlreadyUsed

### Description:

This Google Cloud Function checks if a given email is already used by any restaurant in our database. It returns a response indicating whether the email is already in use or not.

### Endpoint:

POST https://checkifemailalreadyused-cgtbvgpb5q-uc.a.run.app

### Request:

Method: POST
Headers:
Content-Type: application/json
Body: JSON object with the following structure:

{
  "email": "example@example.com"
}

### Response:

Status Codes:
200: Email is not already used.
401: Email is already used.
500: Internal server error occurred.
Body: JSON object with the following structure:

{
  "code": <status_code>
}

### Usage:

1. Request Format: Send a POST request to the provided endpoint with a JSON body containing the email to be checked.
2. Response Handling: Handle the response to determine if the email is already used or not.

Example:

#### Request:

POST https://checkifemailalreadyused-cgtbvgpb5q-uc.a.run.app

Content-Type: application/json

{
  "email": "example@example.com"
}

#### Response:

HTTP/1.1 200 OK
Content-Type: application/json

{
  "code": 200
}
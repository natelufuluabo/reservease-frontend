# Function Name: createSuperUser

### Description:

This Google Cloud Function is responsible for creating a new super user for a restaurant account. It performs several steps including checking if the account already has the maximum number of super users, creating an authentication ID for the new user, updating the list of super users associated with the account, and adding the new super user to the super users collection.

### Endpoint:

POST https://createsuperuser-module-cgtbvgpb5q-uc.a.run.app

### Request:

* Method: POST
* Headers:
    - Content-Type: application/json
* Body: JSON object containing the following keys:
    - name: String (Name of the new super user)
    - email: String (Email of the new super user)
    - password: String (Password of the new super user)
    - accountID: String (ID of the restaurant account)

### Response:

* Status Codes:
    - 204: Super user successfully created.
    - 404: Maximum number of super users reached for the account.
    - 500: Internal server error occurred.
    - 501: Email already in use by another user

* Body: JSON object with the following structure (for success):

{
  "code": 204,
  "data": {
    "name": "<name>",
    "email": "<email>",
    "securityLevel": "SuperUser",
    "authID": "<authID>"
  }
}

### Usage:

1. Request Format: Send a POST request to the provided endpoint with a JSON body containing the details of the new super user and the account ID.

2. Response Handling: Handle the response to determine if the super user was successfully created or if an error occurred.

Example:

#### Request:

POST https://createsuperuser-module-cgtbvgpb5q-uc.a.run.app
Content-Type: application/json

{
  "name": "John Doe",
  "email": "johndoe@example.com",
  "password": "password123",
  "accountID": "123456"
}

#### Response:

HTTP/1.1 204 No Content
Content-Type: application/json

{
  "code": 204,
  "data": {
    "name": "John Doe",
    "email": "johndoe@example.com",
    "securityLevel": "SuperUser",
    "authID": "ABC123"
  }
}
# Function Name: createRestaurantAccount

### Description:

This Google Cloud Function creates a new restaurant account in the database with the provided details. It returns the ID of the newly created account.

### Endpoint:

POST https://createrestaurantaccount-cgtbvgpb5q-uc.a.run.app

### Request:

* Method: POST
* Headers:
    - Content-Type: application/json
* Body: JSON object with the following keys:
    - Name: String (Restaurant name)
    - Address: String (Restaurant address)
    - Phone Number: String (Restaurant phone number)
    - HoursOfOperations: String (Restaurant hours of operations)
    - Email: String (Restaurant email)
    - Admins: Array of Strings (List of restaurants account admins)
    - SuperUsers: Array of Strings (List of restaurants account super users)

### Response:

* Status Code:
    - 200: Account successfully created.
    - 500: Internal server error occurred.

* Body: JSON object with the following structure:

{
  "accountID": "<docRef.id>"
}

Note: Very important to not pay attention how this data will be handled in the front-end because it will be necessary for the next step of the account set up for clients. This has to be implemented and extensively tested because it can become a point of failure for the software during account set up.

### Usage:

1. Request Format: Send a POST request to the provided endpoint with a JSON body containing the details of the restaurant account to be created.

2. Response Handling: Handle the response to obtain the ID of the newly created account.

Example:

#### Request:

POST https://createrestaurantaccount-cgtbvgpb5q-uc.a.run.app
Content-Type: application/json

{
  "Name": "Example Restaurant",
  "Address": "123 Example St, City, Country",
  "Phone Number": "123-456-7890",
  "HoursOfOperations": "Mon-Fri: 9am-5pm",
  "Email": "example@example.com",
  "Admins": [],
  "SuperUsers": []
}

Note: Very important to have the admins and superusers keys - even if the arrays are empty - when making the request because we will need those arrays to save admins and super users authentification IDs.

#### Response:

HTTP/1.1 200 OK
Content-Type: application/json

{
  "accountID": "ABC123"
}
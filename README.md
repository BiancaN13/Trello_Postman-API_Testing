# Trello-API Testing
This project contains a Postman collection for testing the Trello API. The collection includes several requests for interacting with the Trello API, such as retrieving information about all boards, creating a new board, creating lists and cards, and deleting a board.
## Introduction
The Trello API enables the creation of applications that can interact with Trello's project management service, such as managing boards, lists, and cards, or retrieving user data.

The Trello API provides a wide range of functionality for developers, including:

- Retrieve data from your boards, lists, or cards.
- Search for specific Trello boards or cards.
- Create and manage your boards, lists, and cards: create new boards, add lists, move cards, and more.
- Automate task management by moving cards between lists or archiving completed tasks.
- Get real-time updates on changes to your boards, lists, or cards.
- And much more! You can find a complete list of available endpoints in the API Reference.

## Getting Started with Trello API - Authorization
To interact with Trello's resources or manage user data, your application requires an API Key and an API Token for authentication.
## 1. Create a Trello Account

- **Sign up:** If you don’t already have a Trello account, create one.
- **Login:** Go to the Trello Developer Portal to access your account and manage your API credentials.
## 2. Obtain Your API Key and Token
1. **Get Your API Key:**

- Go to the Trello Developer API Key page.
- Generate or retrieve your existing API Key.
2. **Generate Your API Token:**

- After obtaining the API Key, navigate to the Token generation page.
- Authorize your application to access your Trello account and generate the API Token.
## 3. Set Up Your Trello API Environment in Postman
1. **Create Collection Variables:**

- In Postman, create a new collection named Trello API Collection.
- Add collection-level variables:
  - apiKey: Your Trello API Key
  - apiToken: Your Trello API Token
- Configure Requests with Collection Variables:

  - Use the collection variables {{apiKey}} and {{apiToken}} in your requests. For example:
   - URL Format: https://api.trello.com/1/boards/{{boardId}}?key={{apiKey}}&token={{apiToken}}
- This setup ensures that all requests within the collection automatically use the correct credentials.
## 4. Use the Trello API Collection
- Make Requests:
  - Use the Trello API collection in Postman to perform various operations like creating boards, lists, and cards, or retrieving data.
  - The API Key and Token will be included in each request using the collection variables.

## Project Setup
- Collection Variables:
  - baseURL: The base URL for the Trello API.
  - key: API key for authentication.
  - token: Authentication token.
  - boardId: ID of the created board.
  - todoListId: ID of the created TODO list.
  - doneListId: ID of the created DONE list.
  - cardId: ID of the created card.

## Tests perfromed
## 1. Get All Boards

**HTTP Method for Request:** `GET`

**Request Description:** This request returns all boards associated with the user account.

**Endpoint:** `{{baseURL}}/1/members/me/boards?key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
![getallboards](https://github.com/user-attachments/assets/19c2ddea-ce4f-4ea7-a4cb-3506b85ae666)
### JavaScript Tests
- Verifies if the response status is 200 OK.
![getallboardstest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/GetAllBoardsTests.PNG)
## 2. Create Board

**HTTP Method for Request:** `POST`

**Request Description:** Creates a new board in Trello.

**Endpoint:** `{{baseURL}}/1/boards/?name={Postman board2}{{boardNumber}}&key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
![createboard](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/CreateBoard.PNG)
### JavaScript Tests
- Verifies if the response status is 200 OK.
- Verifies if the board was created with the correct name.
- Verifies if the board is private.
- Verifies if the calendar view is disabled.
![createboardtest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/CreateBoardTest.PNG)
![createboardtest2](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/CreateBoardTest2.PNG)
## 3. Get Board

**HTTP Method for Request:** `GET`

**Request Description:** Returns details about a specific board.

**Endpoint:** `{{baseURL}}/1/boards/{{boardId}}?key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
![getboard](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/getboard.PNG)
### JavaScript Tests
- Verifies if the response status is 200 OK.
![getboardtest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/getboardtest.PNG)
## 4. Create TODO List

**HTTP Method for Request:** `POST`

**Request Description:** Creates a TODO list on a specific board.

**Endpoint:** `{{baseURL}}/1/lists?name=TODO&idBoard={{boardId}}&key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
![createtodolist](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/createtodolist.PNG)
### JavaScript Tests
- Verifies if the response status is 200 OK.
- Verifies if the TODO list was created and is active.
![createtodolisttest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/createtodolisttest.PNG)
## 5. Create DONE List

**HTTP Method for Request:** `POST`

**Request Description:** Creates a DONE list on a specific board.

**Endpoint:** `{{baseURL}}/1/lists?name=DONE&idBoard={{boardId}}&key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
![createdonelist](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/createdonelist.PNG)
### JavaScript Tests
- Verifies if the response status is 200 OK.
- Ensures that \ the newly created list is correctly named "DONE", is active (not closed), and is associated with the correct board.
![createdonelisttest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/createdonelisttest.PNG)
## 6. Create Card

**HTTP Method for Request:** `POST`

**Request Description:** Creates a card in the TODO list on the board.

**Endpoint:** `[{{baseURL}}/1/lists?name=DONE&idBoard={{boardId}}&key={{key}}&token={{token}}](https://api.trello.com/1/cards?idList={{todoListId}}&key={{key}}&token={{token}}&name=Sign-up for Trello)`

**Response Status Code:** `200 OK`
### API Request and Response
![createcard](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/createcard.PNG)
### JavaScript Tests
- Verifies if the response status is 200 OK.
- Verifies if the card was created correctly and is associated with the TODO list.
![createcardtest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/createcardtest.PNG)
## 7. Move Card To DONE List

**HTTP Method for Request:** `PUT`

**Request Description:** Moves a card from the TODO list to the DONE list.

**Endpoint:** `{{baseURL}}/1/cards/{{cardId}}?key={{key}}&token={{token}}&idList={{doneListId}}`

**Response Status Code:** `200 OK`
### API Request and Response
![movecard](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/movecard.PNG)
### JavaScript Tests
- Verifies if the response status is 200 OK and if the card was successfully moved.
![movecardtest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/movecardtest.PNG)
## 8. Delete Board

**HTTP Method for Request:** `DELETE`

**Request Description:** Deletes a specific board from Trello.

**Endpoint:** `{{baseURL}}/1/boards/{{boardId}}?key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
![deleteboard](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/deleteboard.PNG)
### JavaScript Tests
- Verifies if the response status is 200 OK.
![deleteboardtest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/deleteboardtest.PNG)
## 9. Get Deleted Board

**HTTP Method for Request:** `GET`

**Request Description:** Attempts to retrieve details about a deleted board.

**Endpoint:** `{{baseURL}}/1/boards/{{boardId}}?key={{key}}&token={{token}}`

**Response Status Code:** `404 Not Found`
### API Request and Response
![getdeletedboard](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/getdeletedboard.PNG)
### JavaScript Tests
- Verifies if the response status is 404 Not Found.
![getdeletedboardtest](https://github.com/BiancaN13/Trello_Postman-API_Testing/blob/main/getdeletedboardtest.PNG)

## Explanation of Tests
## 1. Status Code Validation
For each request, there is a test to verify that the status code of the response matches the expected value (e.g., 200 OK for successful requests, 404 Not Found for attempting to retrieve a deleted board).

## 2. Response Body Content Validation
Tests are included to verify that specific fields in the response match expected values. For example, after creating a board, the test ensures the board's name and other properties are correct.

## 3. Dynamic Variable Validation
Generated IDs, such as those for boards, lists, and cards, are stored as environment variables and used in subsequent requests to ensure data consistency.

## 4. Sequence Validation
- The requests are structured in a sequence to simulate real-world usage of the Trello API. For example:
  - First, a board is created.
  - Then, lists are added to the board.
  - Cards are created within those lists.
  - Cards are moved between lists to simulate task progress.
  - Finally, the board is deleted, and a test confirms that it has been successfully removed.

## 5. Error Handling and Negative Testing
Tests are included to check the API's error handling. For example, the GetDeletedBoard request checks that attempting to access a deleted board returns a 404 Not Found status.

## 6. Response Time Validation
To ensure the API's performance, response times are tested to ensure they fall within acceptable limits.

## 7. Cleanup and Environment Management
Environment variables are managed throughout the testing process to ensure they are correctly set and cleared as needed. This helps maintain a clean state for subsequent tests.

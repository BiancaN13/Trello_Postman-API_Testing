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
### JavaScript Tests
## 2. Create Board

**HTTP Method for Request:** `POST`

**Request Description:** Creates a new board in Trello.

**Endpoint:** `{{baseURL}}/1/boards/?name={Postman board2}{{boardNumber}}&key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
### JavaScript Tests
## 3. Get Board

**HTTP Method for Request:** `GET`

**Request Description:** Returns details about a specific board.

**Endpoint:** `{{baseURL}}/1/boards/{{boardId}}?key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
### JavaScript Tests
## 4. Create TODO List

**HTTP Method for Request:** `POST`

**Request Description:** Creates a TODO list on a specific board.

**Endpoint:** `{{baseURL}}/1/lists?name=TODO&idBoard={{boardId}}&key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
### JavaScript Tests
## 5. Create DONE List

**HTTP Method for Request:** `POST`

**Request Description:** Creates a DONE list on a specific board.

**Endpoint:** `{{baseURL}}/1/lists?name=DONE&idBoard={{boardId}}&key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
### JavaScript Tests
## 6. Create Card

**HTTP Method for Request:** `POST`

**Request Description:** Creates a card in the TODO list on the board.

**Endpoint:** `[{{baseURL}}/1/lists?name=DONE&idBoard={{boardId}}&key={{key}}&token={{token}}](https://api.trello.com/1/cards?idList={{todoListId}}&key={{key}}&token={{token}}&name=Sign-up for Trello)`

**Response Status Code:** `200 OK`
### API Request and Response
### JavaScript Tests
## 7. Create Card

**HTTP Method for Request:** `PUT`

**Request Description:** Moves a card from the TODO list to the DONE list.

**Endpoint:** `{{baseURL}}/1/cards/{{cardId}}?key={{key}}&token={{token}}&idList={{doneListId}}`

**Response Status Code:** `200 OK`
### API Request and Response
### JavaScript Tests
## 8. Delete Board

**HTTP Method for Request:** `DELETE`

**Request Description:** Deletes a specific board from Trello.

**Endpoint:** `{{baseURL}}/1/boards/{{boardId}}?key={{key}}&token={{token}}`

**Response Status Code:** `200 OK`
### API Request and Response
### JavaScript Tests
## 9. Get Deleted Board

**HTTP Method for Request:** `GET`

**Request Description:** Attempts to retrieve details about a deleted board.

**Endpoint:** `{{baseURL}}/1/boards/{{boardId}}?key={{key}}&token={{token}}`

**Response Status Code:** `404 Not Found`
### API Request and Response
### JavaScript Tests

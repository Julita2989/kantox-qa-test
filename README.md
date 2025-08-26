# Kantox QA Test Submission

This repository contains my submission for the Kantox QA technical test, including test cases for the Cashier System (Part 1) and API tests using Postman (Part 2).

Part 1: Test Case Creation for Cashier System

### Overview

The test cases for the Cashier System are documented in test_cases.xlsx. They cover:

- Adding products to the cart.
- Calculating totals with and without discounts.
- Applying discount rules (FreeRule, ReducedPriceRule, FractionPriceRule).
- Handling edge cases, negative cases, and configuration errors.
- Suppositions made due to the absence of products.yml and rules.yml.
- Two Gherkin examples.

### Files

test_cases.xlsx: Contains 12 test cases in a tabular format, suppositions, and Gherkin examples.

## Part 2: API Tests with Postman

### Prerequisites
- Node.js (v14 or higher)
- npm (v6 or higher)
- Postman (download from https://www.postman.com/downloads/)

### Setup Instructions
1. Clone or download this repository.
2. Navigate to the project directory: `cd path/to/repository`.
3. Install dependencies: `npm install`.
4. Start the JSON server: `npm start`.
   - The API will be available at `http://localhost:3000`.
   - If port 3000 is in use, change it (e.g., `json-server --watch db.json --port 3001`) and update the `baseUrl` variable in Postman.
5. Import the Postman collection:
   - Open Postman.
   - Click "Import" > "Choose Files" and select `collection.json` from this repository.
   - Set up an environment variable `baseUrl` with value `http://localhost:3000` (see below).

### Resetting the Database
- The json-server modifies `db.json` for `POST` and `DELETE` requests, and these changes persist across server restarts.
- To reset `db.json` to its original state:
  1. Keep a backup of the original `db.json` (e.g., copy to `db.json.bak`).
  2. After running tests, stop the server (`Ctrl+C`).
  3. Restore the original file: `cp db.json.bak db.json` (macOS/Linux) or `copy db.json.bak db.json` (Windows).
  4. Restart the server: `npm start`.
- This ensures consistent test results, especially for `GET` requests expecting specific data.

### Running the Tests in Postman
1. Ensure the JSON server is running (see Setup Instructions).
2. In Postman, open the imported "Kantox API Test" collection.
3. Set the environment:
   - Create a new environment (Environments tab > Add).
   - Add variable `baseUrl` with value `http://localhost:3000`.
   - Select this environment.
4. Run individual requests or use the Collection Runner:
   - Click "Runner" at the top.
   - Select the collection, choose your environment, and click "Run Kantox API Test".
   - All tests should pass if the server is set up correctly and `db.json` is in its original state.

### Collection Details
- The `collection.json` file contains tests for all required endpoints:
  - `GET /posts`, `GET /posts/{id}`, `POST /posts`, `PUT /posts/{id}`, `DELETE /posts/{id}`
  - `GET /comments`, `GET /comments/{id}`, `POST /comments`, `PUT /comments/{id}`, `DELETE /comments/{id}`
  - `GET /profile`
- Additional negative tests:
  - `GET /posts/999`: Verifies 404 for invalid ID.
  - `POST /posts` with empty body: Verifies the response lacks `title` and `author` fields.
  - `POST /posts` with malformed JSON: Verifies 500 Internal Server Error (observed behavior) and checks for an error message. Note: Expected 400 Bad Request, but json-server (v1.0.0-beta.1) returns 500, which may indicate a server-side issue or configuration.
    - `GET /comments/999`: Verifies 404 for invalid ID.
- Each request includes automated tests for:
  - Correct status codes (e.g., 200, 201, 404, 500).
  - Response structure and content (e.g., expected titles, IDs, absence of fields, or error messages).
- Requests are organized into folders: `Posts`, `Comments`, `Profile`, `Negative Tests`.

### Notes
- The server uses `db.json` as the data source, which is modified by `POST` and `DELETE` requests. Reset it as described above for consistent test runs.
- The `POST /posts` malformed JSON test returns 500 instead of the expected 400, which has been documented in the test description and adjusted in the assertions.
- If tests fail, ensure the server is running, `baseUrl` is correct, and `db.json` is reset to its original state.


















































# Kantox QA Test Submission

## Part 2: API Tests with Postman

### Prerequisites
- Node.js (v14 or higher)
- npm (v6 or higher)
- Postman (download from https://www.postman.com/downloads/)

### Setup Instructions
1. Clone or download this repository.
2. Navigate to the project directory: `cd path/to/repository`.
3. Install dependencies: `npm install`.
4. Start the JSON server: `npm start`.
   - The API will be available at `http://localhost:3000`.
5. Import the Postman collection:
   - Open Postman.
   - Click "Import" > "Choose Files" and select `collection.json` from this repository.
   - Set up an environment variable `baseUrl` with value `http://localhost:3000` (see below for details).


### Running the Tests in Postman
1. Ensure the JSON server is running (see Setup Instructions).
2. In Postman, open the imported "Kantox API Test" collection.
3. Set the environment: If not auto-set, create a new environment (Environments tab > Add), add `baseUrl` variable as `http://localhost:3000`, and select it.
4. Run individual requests or use the Collection Runner:
   - Click "Runner" at the top.
   - Select the collection, choose your environment, and click "Run Kantox API Test".
   - All tests should pass if the server is set up correctly.

























>>>>>>> 03eb0b2 (Initial submission with test cases and Postman collection)

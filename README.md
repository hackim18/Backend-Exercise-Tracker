# Exercise Tracker

This project is an Exercise Tracker built with Node.js, Express, and MongoDB. The application allows you to create users, log exercises for each user, and retrieve the exercise logs.

## Live Demo

You can see a live demo of the application here: [Exercise Tracker](https://exercise-tracker.hackimtech.com)

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [License](#license)

## Installation

1. **Clone the repository**:

   ```sh
   git clone https://github.com/hackim18/Backend-Exercise-Tracker
   cd Backend-Exercise-Tracker
   ```

2. **Install dependencies**:

   ```sh
   npm install
   ```

3. **Create a .env file** in the root of the project and add the following lines:

   ```sh
   PORT=3000
   DB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/<dbname>?retryWrites=true&w=majority
   ```

4. **Start the server**:
   ```sh
   npm start
   ```

The application will be running on http://localhost:3000.

## Usage

To use the Exercise Tracker, you can make requests to the following endpoints:

### API Endpoints

1. **Root Endpoint**

   - URL: /
   - Method: GET
   - Description: Serves the homepage of the application.
   - Example: http://localhost:3000/

2. **Create a New User**

   - URL: /api/users
   - Method: POST
   - Description: Creates a new user.
   - Request Body:
     ```json
     {
       "username": "fcc_test"
     }
     ```
   - Example: http://localhost:3000/api/users
   - Response:
     ```json
     {
       "username": "fcc_test",
       "_id": "5fb5853f734231456ccb3b05"
     }
     ```

3. **Get All Users**

   - URL: /api/users
   - Method: GET
   - Description: Retrieves a list of all users.
   - Example: http://localhost:3000/api/users
   - Response:
     ```json
     [
       {
         "username": "fcc_test",
         "_id": "5fb5853f734231456ccb3b05"
       }
     ]
     ```

4. **Add Exercise to a User**

   - URL: /api/users/:id/exercises
   - Method: POST
   - Description: Adds an exercise to a user.
   - Request Body:
     ```json
     {
       "description": "test",
       "duration": 60,
       "date": "1990-01-01"
     }
     ```
   - Example: http://localhost:3000/api/users/5fb5853f734231456ccb3b05/exercises
   - Response:
     ```json
     {
       "username": "fcc_test",
       "description": "test",
       "duration": 60,
       "date": "Mon Jan 01 1990",
       "_id": "5fb5853f734231456ccb3b05"
     }
     ```

5. **Get User's Exercise Log**
   - URL: /api/users/:id/logs
   - Method: GET
   - Description: Retrieves a user's exercise log.
   - Query Parameters:
     - from (optional): Start date for the log.
     - to (optional): End date for the log.
     - limit (optional): Limit the number of log entries.
   - Example: http://localhost:3000/api/users/5fb5853f734231456ccb3b05/logs?from=1990-01-01&to=2020-12-31&limit=10
   - Response:
     ```json
     {
       "username": "fcc_test",
       "count": 1,
       "_id": "5fb5853f734231456ccb3b05",
       "log": [
         {
           "description": "test",
           "duration": 60,
           "date": "Mon Jan 01 1990"
         }
       ]
     }
     ```

## License

This project is licensed under the MIT License. See the LICENSE file for details.

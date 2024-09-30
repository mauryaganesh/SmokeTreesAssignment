# SmokeTreesAssignment - User Registration App

## Project Overview

This project is a simple **User Registration App** built using **React** for the frontend and **Node.js** with **SQLite** for the backend. The app allows users to enter their **name** and **address** using a form. Once the form is submitted, the data is saved in the backend and is displayed in a table below the form. The table shows all the registered users and their addresses.

## Project Structure

The project has two main directories:

- `backend`: Contains the backend logic, database setup, and server-side code.
- `frontend`: Contains the React code for the user interface.

Here is the structure of the directories:

```
SmokeTreesAssignment/
│
├── backend/
│   ├── database.js
│   └── server.js
│
└── frontend/
    ├── public/
    ├── src/
    │   ├── components/
    │   │   └── UserForm.js
    │   ├── App.js
    │   ├── index.js
    │   └── index.css
```

---

## Getting Started

### Prerequisites

You need to have the following tools installed on your system:

- **Node.js** (for the backend and frontend development)
- **npm** (for managing dependencies)
- **SQLite3** (for the database)

---

## Backend Setup

1. **Navigate to the `backend/` directory**:

   ```bash
   cd SmokeTreesAssignment/backend
   ```

2. **Install dependencies**:

   ```bash
   npm install
   ```

3. **Create the `database.js` file**:

   This file initializes an SQLite database, creates two tables: `User` and `Address`, and exports a function to get the database connection.

   ```javascript
   // database.js
   const sqlite3 = require("sqlite3").verbose();

   // Initialize SQLite database in memory
   const db = new sqlite3.Database("./database.db");

   // Create User and Address tables
   db.serialize(() => {
     db.run(
       "CREATE TABLE IF NOT EXISTS User (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT)"
     );
     db.run(
       "CREATE TABLE IF NOT EXISTS Address (id INTEGER PRIMARY KEY AUTOINCREMENT, userId INTEGER, address TEXT, FOREIGN KEY(userId) REFERENCES User(id))"
     );
   });

   module.exports = db;
   ```

4. **Create the `server.js` file**:

   This file handles the backend logic, sets up API routes for submitting and retrieving user data, and connects to the SQLite database.

5. **Run the backend server**:
   ```bash
   node server.js
   ```

---

## Frontend Setup

1. **Navigate to the `frontend/` directory**:

   ```bash
   cd ../frontend
   ```

2. **Install frontend dependencies**:

   ```bash
   npm install
   ```

3. **Create the `UserForm.js` component** in `src/components` directory:

   This component handles the form input, submission, and displaying the registered users.

4. **Start the frontend server**:
   ```bash
   npm start
   ```

---

## How to Use

1. **Start the Backend Server**:

   - Go to the `backend` directory and run `node server.js`.
   - The backend will run on `http://localhost:5000`.

2. **Start the Frontend Server**:

   - Go to the `frontend` directory and run `npm start`.
   - The frontend will run on `http://localhost:3000`.

3. **Open the application** in your browser at `http://localhost:3000

`. You will see a form to enter the **name** and **address** of the user.

4. **Submit the form**, and the details will be stored in the backend. The list of all registered users will be displayed below the form.

---

## Additional Notes

- **Data validation**: The form checks for required fields (name and address) before submission.
- **API used**: The `fetch` API is used to interact with the backend.
- **Table of registered users**: Displays the list of users stored in the database.

---

## Conclusion

This project is a basic full-stack application that demonstrates user registration using a form. It stores data in a backend SQLite3 database and displays it on the frontend using React.

---

Let me know if you need any help or further explanations!

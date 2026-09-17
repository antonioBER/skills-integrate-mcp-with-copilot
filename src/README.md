# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign in with a student or administrator account
- Sign up for activities as an authenticated student
- Unregister your own activities as a student

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   uvicorn app:app --reload
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/login`                                                            | Create an authenticated session                                     |
| POST   | `/logout`                                                           | End the current session                                             |
| GET    | `/me`                                                               | Get the current user and role                                       |
| POST   | `/activities/{activity_name}/signup`                               | Sign up the authenticated student                                   |
| DELETE | `/activities/{activity_name}/unregister`                           | Unregister the authenticated student                                |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

Activities, sessions, and registration changes are stored in memory, which means they will be reset when the server restarts. User passwords are stored as salted PBKDF2 hashes in `users.json`, never as plaintext.

Development accounts:

- `admin@mergington.edu` / `admin-demo-password`
- `student@mergington.edu` / `student-demo-password`

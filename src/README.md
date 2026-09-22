# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Teachers can sign students up for activities and unregister them

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

Use `teacher` / `mergington-teacher` to sign in locally. The password is stored only as a PBKDF2 hash in `teachers.json`.

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/auth/login`                                                     | Start a teacher session                                              |
| POST   | `/auth/logout`                                                    | End the current teacher session                                      |
| GET    | `/auth/me`                                                        | Return the signed-in teacher                                         |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Sign up a student; teacher login required                            |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student; teacher login required                     |

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

All data is stored in memory, which means data will be reset when the server restarts.

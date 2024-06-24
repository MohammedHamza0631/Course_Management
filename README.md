# Course Management App

This project is a Course Management Application that allows users to browse and enroll through various courses. The application provides a smooth and interactive user experience, leveraging modern technologies such as React and Next UI for the frontend, and Node.js and PostgreSQL for the backend and database.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Database Schema](#database-schema)
- [License](#license)

## Live Link
- To access the live project, Go [here](https://ine-frontend.vercel.app)

## Features

- **User Authentication**: Users can register and log in to the application.
- **Course Browsing**: Users can browse available courses without logging in.
- **Search Functionality**: Users can search from a list of courses and the results get updated in real time.
- **Course Enrollment**: Users need to enroll in a course to access its video content and lessons.

## Tech Stack

- **Frontend**: React, Next UI
- **Backend**: Node.js, Express
- **Database**: PostgreSQL
- **Image and Video CDN**: Cloudinary

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/course-management-app.git
    cd course-management-app
    ```

2. Install backend dependencies:
    ```bash
    cd backend
    npm install
    ```

3. Install frontend dependencies:
    ```bash
    cd ../frontend
    npm install
    ```

4. Set up the PostgreSQL database:
    - Create a database named `course_management`.
    - Run the SQL scripts located in the `backend/db` folder to set up the tables.

5. Configure environment variables:
    - Create a `.env` file in the `backend` directory and add the following:
    ```bash
    PORT=5000
    DATABASE_URL=your_database_url
    JWT_SECRET=your_jwt_secret
    ```

6. Start the backend server:
    ```bash
    cd backend
    npm start
    ```

7. Start the frontend development server:
    ```bash
    cd ../frontend
    npm start
    ```

## Usage

1. **Register/Login**: Users can register a new account or log in using existing credentials.
2. **Browse Courses**: Users can browse available courses without needing to log in or enroll.
3. **Search Courses**: Users can search from the list of courses to get a specific course.
4. **Enroll in Courses**: Users can enroll in courses to access the detailed lessons and video content.

## API Endpoints

- **Authentication**
  - `POST /api/auth/register`: Register a new user
  - `POST /api/auth/login`: Login with user credentials

- **Courses**
  - `GET /api/courses`: Get all courses
  - `GET /api/courses/:id`: Get course details by ID
  - `GET /api/courses/search?term=keyword`: Search courses by keyword

- **Enrollments**
  - `GET /api/enrollments/status/:userId/:courseId`: Check enrollment status
  - `POST /api/enrollments`: Enroll in a course

## Database Schema

### Users Table
| Column      | Type    | Description         |
|-------------|---------|---------------------|
| id          | SERIAL  | Primary Key         |
| username    | VARCHAR | Unique Username     |
| password    | VARCHAR | Hashed Password     |
| email       | VARCHAR | User Email Address  |

### Courses Table
| Column   | Type    | Description           |
|----------|---------|-----------------------|
| id       | SERIAL  | Primary Key           |
| title    | VARCHAR | Course Title          |
| summary  | TEXT    | Course Summary        |
| cover    | TEXT    | Cover Image URL       |
| tags     | TEXT[]  | Course Tags           |

### Lessons Table
| Column       | Type    | Description               |
|--------------|---------|---------------------------|
| id           | SERIAL  | Primary Key               |
| course_id    | INT     | Foreign Key (Courses)     |
| title        | VARCHAR | Lesson Title              |
| video_id     | VARCHAR | Video ID                  |
| text_content | TEXT    | Lesson Content            |

### Enrollments Table
| Column    | Type    | Description               |
|-----------|---------|---------------------------|
| id        | SERIAL  | Primary Key               |
| user_id   | INT     | Foreign Key (Users)       |
| course_id | INT     | Foreign Key (Courses)     |

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

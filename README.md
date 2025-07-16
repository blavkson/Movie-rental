# Movie Rental System

A simple movie rental system built with Node.js, Express, and MySQL.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Database Setup](#database-setup)
- [API Endpoints](#api-endpoints)
- [Frontend](#frontend)
- [Contributing](#contributing)
- [License](#license)

## Features

- User authentication (signup, login, logout)
- Browse and search for movies
- View movie details
- Rent movies
- View rental history

## Technologies Used

- **Backend:** Node.js, Express.js
- **Database:** MySQL
- **Frontend:** HTML, CSS, JavaScript

## Prerequisites

- Node.js and npm installed
- MySQL installed

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/movie-rental-system.git
   ```
2. Navigate to the project directory:
   ```bash
   cd movie-rental-system
   ```
3. Install the dependencies:
    ```bash
    npm install
    ```

## Database Setup

1. Create a MySQL database named `movie_rental_db`.
2. Create a `.env` file in the root directory and add the following environment variables:
   ```
   DB_HOST=localhost
   DB_USER=your_mysql_username
   DB_PASSWORD=your_mysql_password
   DB_NAME=movie_rental_db
   ```
3. Run the database migrations to create the necessary tables:
    ```bash
    npm run migrate
    ```

### Database Schema

The database consists of three tables: `users`, `movies`, and `rentals`.

#### `users` table

| Column | Type | Description |
|---|---|---|
| id | INT | Primary Key, Auto Increment |
| username | VARCHAR(255) | User's username |
| email | VARCHAR(255) | User's email |
| password | VARCHAR(255) | Hashed password |
| created_at | TIMESTAMP | Timestamp of creation |

#### `movies` table

| Column | Type | Description |
|---|---|---|
| id | INT | Primary Key, Auto Increment |
| title | VARCHAR(255) | Movie title |
| genre | VARCHAR(255) | Movie genre |
| release_year | INT | Movie release year |
| available_copies | INT | Number of available copies |
| created_at | TIMESTAMP | Timestamp of creation |

#### `rentals` table

| Column | Type | Description |
|---|---|---|
| id | INT | Primary Key, Auto Increment |
| user_id | INT | Foreign Key to `users` table |
| movie_id | INT | Foreign Key to `movies` table |
| rental_date | TIMESTAMP | Timestamp of rental |
| return_date | TIMESTAMP | Timestamp of return (nullable) |

## API Endpoints

### Users

- `POST /api/users/signup` - Register a new user.
- `POST /api/users/login` - Login a user.
- `GET /api/users/logout` - Logout a user.

### Movies

- `GET /api/movies` - Get a list of all movies.
- `GET /api/movies/:id` - Get details of a specific movie.
- `POST /api/movies` - Add a new movie (admin only).
- `PUT /api/movies/:id` - Update a movie (admin only).
- `DELETE /api/movies/:id` - Delete a movie (admin only).

### Rentals

- `POST /api/rentals` - Rent a movie.
- `GET /api/rentals` - Get rental history for the logged-in user.

## Frontend

The frontend is built with basic HTML, CSS, and JavaScript. The files are located in the `public` directory.

### Pages

- `index.html` - Home page with a list of movies.
- `login.html` - Login page.
- `signup.html` - Signup page.
- `movie.html` - Movie details page.
- `profile.html` - User profile page with rental history.

### Main JavaScript files

- `public/js/main.js` - Main script for handling movie display and search.
- `public/js/auth.js` - Script for handling user authentication.
- `public/js/movie.js` - Script for handling movie details and renting.
- `public/js/profile.js` - Script for displaying user profile and rental history.

## Contributing

Contributions are welcome! Please feel free to submit a pull request.

## License

This project is licensed under the MIT License.

# Secure Notes API – Learning Notes

## Project Overview

The Secure Notes API is a RESTful backend application built using Flask and SQLAlchemy. It allows users to create, read, update, and delete notes while storing data in a SQLite database.

The goal of this project was to learn how a backend application is structured, how APIs communicate with clients, how databases store information, and how Docker can package an application to run consistently on any machine.

---

# Skills Practiced

- Python
- Flask
- REST API Development
- SQLAlchemy ORM
- SQLite Database
- CRUD Operations
- JSON Request & Response
- Environment Variables (.env)
- Docker
- Postman API Testing
- Git & GitHub

---

# Project Flow

Idea

↓

Create Flask Project

↓

Configure Application

↓

Connect Database

↓

Create Database Model

↓

Build CRUD APIs

↓

Test with Postman

↓

Containerize using Docker

↓

Document Project

---

# Concepts Learned

## 1. What is an API?

API stands for Application Programming Interface.

It allows two applications to communicate using HTTP requests.

Example

Client

↓

POST /notes

↓

Server

↓

Database

↓

JSON Response

Without APIs, applications cannot exchange data.

---

## 2. Why Flask?

Flask is a lightweight Python web framework.

Why we used it

- Easy for beginners
- Good for REST APIs
- Flexible
- Simple project structure

---

## 3. What is REST?

REST is a standard way of designing APIs.

Each URL represents a resource.

Example

GET /notes

means

"Give me all notes."

REST makes APIs predictable and easy to understand.

---

## 4. HTTP Methods

GET

Retrieve data.

POST

Create new data.

PUT

Update existing data.

DELETE

Remove data.

These four methods are the foundation of CRUD operations.

---

## 5. What is CRUD?

CRUD represents the four basic database operations.

Create

Insert data

Read

Retrieve data

Update

Modify existing data

Delete

Remove data

Almost every backend application performs CRUD operations.

---

## 6. Why JSON?

JSON is the standard format used to exchange data between clients and servers.

Example

```json
{
  "title": "Docker",
  "description": "Learn Docker basics"
}
```

It is lightweight, readable, and supported by almost every programming language.

---

## 7. Why SQLite?

SQLite stores the database inside a single file.

Why we used it

- No installation required
- Lightweight
- Perfect for learning
- Easy to integrate with Flask

---

## 8. What is SQLAlchemy?

SQLAlchemy is an ORM (Object Relational Mapper).

Instead of writing SQL queries manually, Python classes represent database tables.

Example

Python Class

↓

Database Table

↓

Rows

This makes database operations easier and cleaner.

---

## 9. Why Validation?

Validation checks whether the incoming request contains valid data.

Example

Missing title

↓

Return

400 Bad Request

Validation prevents incorrect or incomplete data from entering the database.

---

## 10. Why Environment Variables?

Sensitive information should never be written directly into source code.

Instead we use

.env

to store

- Secret keys
- Database URLs
- Configuration

This improves security and makes the project easier to configure.

---

## 11. Why Git?

Git tracks every change made during development.

Benefits

- Version history
- Rollback changes
- Team collaboration
- Safe experimentation

---

## 12. Why GitHub?

GitHub stores Git repositories online.

Benefits

- Portfolio
- Collaboration
- Backup
- Code sharing

---

## 13. Why Postman?

Postman allows testing APIs without building a frontend.

It helped verify

- Requests
- Responses
- Status codes
- Error handling

---

## 14. Why Docker?

Docker packages the application together with all dependencies.

Without Docker

Application may work on one machine but fail on another.

With Docker

Application behaves consistently everywhere.

One image

↓

Many computers

↓

Same result

---

# API Status Codes Learned

200

Request successful.

201

Resource created successfully.

400

Invalid request from client.

404

Requested resource not found.

500

Internal server error.

---

# Folder Purpose

app.py

Application entry point.

config.py

Application configuration.

database.py

Initializes SQLAlchemy.

models.py

Defines database tables.

routes.py

Contains API endpoints.

Dockerfile

Instructions to build the Docker image.

requirements.txt

Python dependencies.

README.md

Project documentation.

---

# Challenges Faced

## Git Push Rejected

Problem

GitHub had commits that were not available locally.

Reason

Local and remote repositories were out of sync.

Solution

Used

git pull --rebase origin main

before pushing.

---

## Docker Database Error

Problem

SQLALCHEMY_DATABASE_URI was missing.

Reason

The container did not load the .env file.

Solution

Started the container using

docker run --env-file .env

---

## Docker Connection Issue

Problem

Application could not be accessed.

Reason

Flask was listening only on localhost inside the container.

Solution

Changed

```python
app.run(host="0.0.0.0", port=5000)
```

so Docker could expose the application outside the container.

---

## Port Already In Use

Problem

Port 5000 was occupied.

Solution

Mapped another port.

5001:5000

---

# Key Learnings

- Understand how backend applications are structured.
- Design REST APIs using Flask.
- Connect APIs with databases.
- Validate incoming requests.
- Handle HTTP status codes.
- Test APIs using Postman.
- Use Git for version control.
- Push projects to GitHub.
- Containerise applications using Docker.
- Debug common Docker and Git issues.

---

# Final Outcome

Successfully built a complete RESTful Notes API.

Implemented CRUD functionality, integrated a SQLite database, tested all endpoints using Postman, containerized the application with Docker, documented the project, and published it on GitHub.

This project provided practical experience with backend development workflows and strengthened understanding of API design, databases, version control, and containerization.

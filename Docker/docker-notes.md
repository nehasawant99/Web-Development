## Docker Fundamentals Notes

Docker is a tool that **packages an application with everything it needs to run**—its code, libraries, dependencies, and runtime—into a **container**.
This lets the application run the same way on your laptop, a test server, or a production server.

## Why Docker is used

### 1. Consistent environment

Without Docker:

```text
Works on my laptop ❌
Fails on the server ❌
```

With Docker:

```text
Works on my laptop ✅
Works on the server ✅
```

---

### 2. Easy deployment

Instead of installing:

* Python
* Node.js
* Java
* Nginx
* Libraries

on every server, you just run the Docker container.

```bash
docker run myapp
```

---

### 3. Isolated applications

Each application has its own environment.

Example:

```text
Container 1
Python 3.12

Container 2
Python 3.10

Container 3
Node.js 22
```

They don't interfere with each other.

---

### 4. Quick setup

Without Docker:

* Install software
* Configure dependencies
* Resolve version conflicts

With Docker:

```bash
docker compose up
```

Everything starts automatically.

---

### 5. Easier teamwork

If your teammate clones your project:

Without Docker:

> "Install Python 3.11, PostgreSQL 16, Redis..."

With Docker:

```bash
git clone ...
docker compose up
```

Everyone gets the same setup.

---

## Example

Suppose you built a Flask website.

Without Docker:

```text
Mac
├── Python
├── Flask
├── SQLite
```

On the server, you must install everything again.

With Docker:

```text
Docker Container
├── Python
├── Flask
├── SQLite
├── Your App
```

Move the container to another machine, and it runs the same way.

---

## Docker in a real company

A web application might look like this:

```text
Users
   │
   ▼
Nginx
   │
   ▼
Docker Container
   │
   ├── Flask API
   ├── React App
   └── Redis
   │
   ▼
PostgreSQL
```

Each service can run in its own container, making updates and scaling easier.

---

## Basic Docker commands

```bash
docker pull nginx          # Download an image
docker images              # List images
docker ps                  # Running containers
docker run nginx           # Start a container
docker stop <container-id> # Stop a container
docker rm <container-id>   # Remove a container
docker build -t myapp .    # Build your own image
docker compose up          # Start multiple services
```

---

## Docker vs Virtual Machine

| Docker                           | Virtual Machine                 |
| -------------------------------- | ------------------------------- |
| Lightweight                      | Heavier                         |
| Starts in seconds                | Takes longer to boot            |
| Shares the host OS kernel        | Runs a full guest OS            |
| Uses fewer resources             | Uses more CPU/RAM/storage       |
| Great for apps and microservices | Good for full operating systems |

---

# These notes are for educational purposes and study material. To understand better and faster


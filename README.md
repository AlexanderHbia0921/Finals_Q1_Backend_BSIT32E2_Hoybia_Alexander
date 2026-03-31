# 🖥️ Todo API – Finals_Q1 (Backend)

This project serves as the backend API for a Todo application built with **ASP.NET Core Web API**.
It supports CRUD operations, blockchain-like validation, and proof-of-work security.

---

# 🚀 Project Overview

The backend is responsible for:

* Managing Todo items using in-memory storage
* Providing CRUD API endpoints
* Generating hash chains for data integrity
* Performing proof-of-work validation
* Verifying the integrity of the chain

---

# 🧩 Architecture Summary

The application follows a **layered architecture**:

* **Controller Layer** → Handles HTTP requests
* **Model Layer** → Defines the Todo data structure
* **Helper Layer** → Contains SHA-256 hashing logic
* **In-Memory Storage** → Uses `List<Todo>` for data storage

### Design Principles

* RESTful API design
* Separation of concerns
* Deterministic hash chaining for integrity validation

---

# ⚙️ Setup Instructions

```bash
cd TodoApi
dotnet restore
dotnet run
```

The API will run at:

```
http://localhost:5023
```

Swagger UI:

```
http://localhost:5023/swagger
```

---

# 🔗 API Endpoints

| Method | Endpoint          | Description       |
| ------ | ----------------- | ----------------- |
| GET    | /api/todos        | Get all todos     |
| POST   | /api/todos        | Create a todo     |
| PUT    | /api/todos/{id}   | Update a todo     |
| DELETE | /api/todos/{id}   | Delete a todo     |
| GET    | /api/todos/verify | Verify hash chain |

---

# 🔐 Advanced Features

## Blockchain-Style Hashing

Each todo item contains:

* `Hash`
* `PreviousHash`

Every record is linked to the previous one.
Any modification will break the chain and invalidate the data.

---

## Chain Verification

```
GET /api/todos/verify
```

Returns:

* `200 OK` → Chain is valid
* `409 Conflict` → Chain has been tampered

---

## ⛏️ Proof-of-Work

Before accepting POST or PUT requests:

```
SHA256(title | nonce) must start with "00"
```

* Valid → Request accepted
* Invalid → Request rejected (`400 Bad Request`)

---

# 📌 Summary

This backend demonstrates:

* RESTful API development
* Hash-based data integrity
* Proof-of-work validation
* Clean layered architecture

---

# 👨‍💻 Author

**Alexander C. Hoybia**

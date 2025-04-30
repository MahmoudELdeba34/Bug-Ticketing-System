# 📡 Bug Ticketing System - API Documentation

This document provides a full explanation of the available API endpoints used in the Bug Ticketing System project. It can be used for understanding how to interact with the backend API via HTTP requests.

---

## 🔐 Account Management

### `POST /api/Account/Register`
- **Description**: Register a new user.
- **Request Body (JSON)**:
```json
{
  "userName": "Mahmoud_Ahmed",
  "password": "YourPassword123!",
  "email": "mahmoud@example.com"
}
```
- **Response**: `200 OK` on success.

---

### `POST /api/Account/Login`
- **Description**: Log in to the system to receive a JWT token.
- **Request Body (JSON)**:
```json
{
  "userName": "Mahmoud_Ahmed",
  "password": "YourPassword123!"
}
```
- **Response**: `200 OK` with a JWT token for authorization.

---

### `POST /api/Account/assign-role`
- **Description**: Assign a specific role (e.g., Admin, Developer, Student) to a user.
- **Query Parameters**:
  - `userName`: the username (e.g., Mahmoud_Ahmed)
  - `role`: role name (e.g., Student)
- **Example**:
```
POST /api/Account/assign-role?userName=Mahmoud_Ahmed&role=Student
```
- **Response**: `"Role 'Student' added to user 'Mahmoud_Ahmed'"`

---

## 📎 Attachment

### `POST /api/Attachment`
- **Description**: Upload a file and attach it to a bug report.
- **Request Type**: `multipart/form-data`
- **Form Fields**:
  - `bugId`: Bug’s unique ID (GUID)
  - `File`: File to be uploaded
- **Authorization**: Requires Bearer Token
- **Response**: `200 OK` if uploaded successfully.

---

### `GET /api/Attachment?bugId={id}`
- **Description**: Retrieve all attachments related to a specific bug.
- **Query Parameter**:
  - `bugId`: The GUID of the bug
- **Response**: `200 OK` with attachment metadata.

---

### `DELETE /api/Attachment/{attachmentId}`
- **Description**: Delete a specific attachment.
- **Parameter**: `attachmentId` (GUID)
- **Response**: `200 OK` on successful deletion.

---

## 🐞 Bug Management

### `GET /api/Bug`
- **Description**: Retrieve all bugs in the system.
- **Response**: List of bugs.

---

### `GET /api/Bug/{id}`
- **Description**: Get the details of a specific bug by its ID.
- **Response**: Bug object with details.

---

## 📁 Project Management

### `GET /api/Project`
- **Description**: Get all projects.
- **Response**: List of project objects.

---

### `POST /api/Project`
- **Description**: Create a new project.
- **Request Body (JSON)**:
```json
{
  "name": "New Project",
  "description": "Details about the project"
}
```
- **Response**: `200 OK` if successfully created.

---

### `GET /api/Project/{id}`
- **Description**: Get a specific project by its ID.
- **Response**: Project details.

---

## 🧾 Schemas (DTOs)

### RegisterDto
```json
{
  "userName": "string",
  "password": "string",
  "email": "string"
}
```

### LoginDto
```json
{
  "userName": "string",
  "password": "string"
}
```

### ProjectAddDto
```json
{
  "name": "string",
  "description": "string"
}
```

---




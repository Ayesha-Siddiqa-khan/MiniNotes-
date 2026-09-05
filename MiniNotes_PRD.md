# MiniNotes — Product Requirements Document (PRD)

## 1. Product Overview

**Product Name:** MiniNotes

**Purpose:**  
MiniNotes is a very small notes application created primarily as a hands-on practice project for deploying and running an application on AWS.

The application should remain intentionally simple so the main focus can be on deployment, networking, and AWS infrastructure rather than complex application features.

## 2. Goals

- Build a small, working web application.
- Practice deploying an application on AWS.
- Practice exposing the application through an AWS networking component such as an Application Load Balancer / API Gateway, depending on the deployment architecture.
- Practice application health checks, logs, and basic troubleshooting.
- Keep the application small enough to understand and manage easily.

## 3. Target User

A single developer/student using MiniNotes for learning and AWS deployment practice.

## 4. Core Features

### 4.1 Create a Note
The user can:
- Enter a note title.
- Enter note content.
- Save the note.

### 4.2 View Notes
The user can:
- See a list of saved notes.
- View the title and content of each note.

### 4.3 Delete a Note
The user can:
- Delete an existing note.

## 5. MVP Scope

The first version should contain only:

- Simple frontend UI.
- Simple backend API.
- Notes storage.
- Create note.
- List notes.
- Delete note.
- Health-check endpoint such as `/health`.
- Production-ready configuration through environment variables.
- Docker support.
- AWS deployment.

## 6. Suggested API

### `GET /health`
Returns the application's health status.

Example response:
```json
{
  "status": "healthy"
}
```

### `GET /notes`
Returns all notes.

### `POST /notes`
Creates a new note.

Example request:
```json
{
  "title": "My Note",
  "content": "Learning AWS deployment."
}
```

### `DELETE /notes/{id}`
Deletes a note by ID.

## 7. Data Model

A note should contain:

| Field | Type | Required |
|---|---|---|
| id | Integer/String | Yes |
| title | String | Yes |
| content | Text | Yes |
| created_at | DateTime | Yes |

## 8. Technical Direction

The implementation should follow a simple architecture.

**Frontend → Backend API → Database**

The application should be containerized with Docker.

The exact programming language/framework can follow the developer's existing skills and preferences. The implementation should avoid unnecessary frameworks or services.

## 9. AWS Deployment Practice

The project should be deployed to AWS with a simple architecture.

The deployment should provide:

- A running application on AWS.
- Public access to the application.
- Health checks.
- Application logs.
- Environment-variable based configuration.
- A clear way to start, stop, redeploy, and troubleshoot the application.

An AWS networking layer such as an **Application Load Balancer (ALB)** or **API Gateway** can be used as part of the deployment practice, depending on the selected architecture.

## 10. Non-Functional Requirements

- Keep the application lightweight.
- Keep the code easy to understand.
- Use secure configuration practices.
- Do not hard-code secrets.
- Provide a Dockerfile.
- Provide clear setup and deployment instructions.
- The application should return a successful response from `/health` when running correctly.

## 11. Out of Scope

The MVP should NOT include:

- User authentication.
- Social login.
- Sharing notes.
- Rich-text editing.
- File uploads.
- Notifications.
- Mobile applications.
- Complex permissions.
- AI features.
- Advanced search.
- Payments.

These can be considered later, but they are not required for the practice project.

## 12. Success Criteria

The project is successful when:

1. MiniNotes runs locally.
2. Notes can be created, viewed, and deleted.
3. The application can be built into a Docker image.
4. The Docker container runs successfully.
5. The application is deployed on AWS.
6. The deployed application is publicly reachable.
7. The health endpoint works through the deployed networking layer.
8. Logs can be inspected when something goes wrong.
9. The application can be redeployed without changing the application code unnecessarily.

## 13. Development Principle

Keep MiniNotes intentionally small. The primary learning objective is **AWS deployment and infrastructure practice**, not building a feature-rich notes platform.

Before implementing major changes, inspect the existing project structure and architecture, use the simplest suitable approach, avoid breaking working functionality, and test the application locally and after deployment.

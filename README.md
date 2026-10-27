# 🚀 TechPro AI — AI-Powered Customer Support Platform

An intelligent customer support platform that combines **AI-powered conversations, Retrieval-Augmented Generation (RAG), ticket management, and real-time support workflows** in one application.

TechPro AI helps customers find answers from a local knowledge base, create support tickets, and connect with support agents when additional assistance is needed. Administrators can manage knowledge-base documents and monitor support activity through an analytics dashboard.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#️-system-architecture)
- [Technology Stack](#️-technology-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Getting Started](#-getting-started)
- [Demo Accounts](#-demo-accounts)
- [Application API](#-application-api)
- [AI Service API](#-ai-service-api)
- [Testing and Build](#-testing-and-build)
- [Configuration](#️-configuration)
- [Security Considerations](#-security-considerations)
- [Future Enhancements](#-future-enhancements)
- [License](#-license)

---

## 🎯 Overview

TechPro AI is a full-stack customer support application designed to make customer service faster, more accessible, and easier to manage.

The application consists of three primary services:

- **React Frontend:** Provides the user interface for customers, support agents, and administrators.
- **Express Backend:** Handles authentication, API requests, ticket management, application data, and real-time communication.
- **Python AI Service:** Retrieves relevant information from local support documents and generates knowledge-grounded responses using the project's retrieval and agent modules.

The platform also supports conversation history, message feedback, specialist routing, and knowledge-base re-indexing.

### 💡 What Makes TechPro AI Useful?

Instead of requiring customers to search through multiple support documents, TechPro AI provides a conversational interface that helps them find relevant information and access support when needed.

---

## ✨ Key Features

### 🤖 1. AI-Powered Customer Support
- Chat with an AI-powered support assistant.
- Retrieve relevant information from local knowledge-base documents.
- Display source references to help users identify supporting documents.
- Provide suggested questions for easier interaction.
- Route queries to appropriate support specialists.
- Maintain conversation history.
- Collect feedback on AI-generated responses.

### 🔐 2. Authentication and Role-Based Access
- Support separate customer, agent, and administrator roles.
- Authenticate users using JSON Web Tokens (JWT).
- Protect authenticated API endpoints.
- Restrict administrative operations according to user roles.

### 🎫 3. Support Ticket Management
- Allow customers to create support tickets.
- Enable users to view their tickets.
- Allow agents and administrators to update ticket status and priority.
- Support agent assignment.
- Organize customer issues for easier tracking.

### ⚡ 4. Real-Time Support Workflows
- Use Socket.IO for real-time communication.
- Support real-time events for customer support workflows.
- Provide the foundation for live agent handoffs.

### 📊 5. Admin Dashboard and Analytics
- Provide an administrative analytics dashboard.
- Display support-related statistics.
- Allow administrators to review knowledge-base documents.
- Support saving documents and requesting re-indexing.

### 📚 6. Knowledge-Base Management
- Store support documents in the local knowledge-base directory.
- Retrieve relevant document content for AI conversations.
- Allow administrators to update knowledge-base documents.
- Request re-indexing after document updates.

### 🎙️ 7. Voice Input
- Support voice input through browser speech recognition where available.
- Allow users to enter messages using their voice instead of typing.

---

## 🏗️ System Architecture

TechPro AI follows a modular architecture in which the frontend, backend, and AI service operate independently.

```text
                   ┌──────────────────────────┐
                   │       Users              │
                   │ Customer / Agent / Admin │
                   └────────────┬─────────────┘
                                │
                                ▼
                   ┌──────────────────────────┐
                   │      React Frontend      │
                   │        Vite Client       │
                   └────────────┬─────────────┘
                                │
                     REST API / Socket.IO
                                │
                                ▼
                   ┌──────────────────────────┐
                   │      Express Server      │
                   │                          │
                   │ Authentication           │
                   │ Ticket Management        │
                   │ Application APIs         │
                   │ Real-Time Communication  │
                   └───────┬─────────┬────────┘
                           │         │
                           │         ▼
                           │  ┌────────────────────┐
                           │  │   JSON Data Store  │
                           │  │ support_store.json │
                           │  └────────────────────┘
                           │
                           ▼
                   ┌──────────────────────────┐
                   │     Python AI Service   │
                   │                          │
                   │ RAG Retrieval            │
                   │ AI Chat Endpoint         │
                   │ Agent Listing            │
                   │ Knowledge-Base Ingestion │
                   └────────────┬─────────────┘
                                │
                                ▼
                   ┌──────────────────────────┐
                   │     Knowledge Base      │
                   │      Text Documents      │
                   └──────────────────────────┘
```

### 🔄 AI Chat Workflow

1. A customer submits a question through the React frontend.
2. The frontend sends the request to the Express backend.
3. The backend forwards the request to the Python AI service.
4. The AI service retrieves relevant information from the knowledge base.
5. The service generates a response using the project's retrieval and agent modules.
6. The response and available source references are returned to the frontend.
7. The customer can continue the conversation or create a support ticket if further assistance is required.

*Note: The exact response-generation method depends on the implementation of the project's AI and retrieval modules.*

---

## 🛠️ Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React 18, Vite |
| Backend | Node.js, Express.js |
| AI Service | Python 3 |
| AI Approach | Retrieval-Augmented Generation (RAG) |
| Authentication | JSON Web Tokens (JWT) |
| Real-Time Communication | Socket.IO |
| Data Persistence | JSON file storage |
| Knowledge Base | Local text documents |
| Python HTTP Client | Requests |
| Package Management | npm, pip |
| Testing | Project-configured server and client test scripts |

---

## 📂 Project Structure

```text
TechPro-AI/
│
├── client/
│   ├── src/
│   │   ├── config.js
│   │   └── ...
│   ├── package.json
│   └── ...
│
├── server/
│   ├── support_store.json
│   └── ...
│
├── ai-service/
│   ├── requirements.txt
│   └── ...
│
├── knowledge-base/
│   └── ...
│
├── package.json
├── README.md
└── ...
```

### Directory Description

| Directory or File | Purpose |
|---|---|
| `client/` | React single-page application served by Vite. |
| `server/` | Express REST API and Socket.IO server. |
| `server/support_store.json` | JSON file used for application data persistence. |
| `ai-service/` | Python HTTP server for AI chat, retrieval, and document ingestion. |
| `ai-service/requirements.txt` | Python dependency list. |
| `knowledge-base/` | Local text documents used by the AI service. |
| `package.json` | Root-level scripts for installation, development, testing, and building. |

*The structure above highlights the main components. Individual source files may vary depending on the implementation.*

---

## 📋 Prerequisites

Install the following before running the application:

- **Node.js and npm** — for the frontend and backend.
- **Python 3** — for the AI service.
- **Git** — for cloning and managing the repository.

Verify your installations:

```bash
node --version
npm --version
python --version
git --version
```

If your system uses the `python3` command instead of `python`, replace `python` with `python3` in the relevant commands.

---

## 🚀 Getting Started

Follow these steps to run TechPro AI locally.

### Step 1: Clone the Repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_REPOSITORY_DIRECTORY>
```

Replace the placeholders with your actual GitHub repository URL and directory name.

### Step 2: Install JavaScript Dependencies

Run this command from the repository root:

```bash
npm run install:all
```

This uses the installation script configured in the root `package.json`.

### Step 3: Install Python Dependencies

```bash
python -m pip install -r ai-service/requirements.txt
```

This installs the Python packages required by the AI service.

### Step 4: Start the AI Service

Open a terminal in the repository root and run:

```bash
npm run start:ai
```

The AI service uses port `8000` by default.

### Step 5: Start the Backend Server

Open a second terminal in the repository root and run:

```bash
npm run start:server
```

The Express backend uses port `5005` by default.

### Step 6: Start the Frontend

Open a third terminal in the repository root and run:

```bash
npm run start:client
```

The frontend uses Vite and runs on port `3000` by default.

### Step 7: Open the Application

Open the local frontend address in your browser:

**http://localhost:3000**

Make sure all three services are running before testing the complete application.

### Default Service Ports

| Service | Default Port | Local Address |
|---|---:|---|
| React Frontend | 3000 | `http://localhost:3000` |
| Express Backend | 5005 | `http://localhost:5005` |
| Python AI Service | 8000 | `http://localhost:8000` |

---

## 👤 Demo Accounts

When the backend's JSON store contains no users, it creates the following local development accounts.

| Role | Email | Password |
|---|---|---|
| Customer | `user@example.com` | `password123` |
| Support Agent | `agent@example.com` | `password123` |
| Administrator | `admin@example.com` | `password123` |

### Important Notes

- Demo accounts are created only when the stored user list is empty.
- If users already exist in `server/support_store.json`, the demo accounts may not be created.
- These credentials are intended only for local development.
- Never use these credentials or the default JWT signing secret in a production environment.

---

## 🔌 Application API

The Express backend provides REST API endpoints for authentication, conversations, tickets, knowledge-base management, and analytics.

Protected endpoints require an authentication token obtained through the login endpoint.

Include the token in the request header:

```http
Authorization: Bearer <YOUR_JWT_TOKEN>
```

### 1. Authentication

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/api/health` | Public | Check backend health. |
| POST | `/api/auth/register` | Public | Register a new account. |
| POST | `/api/auth/login` | Public | Authenticate and receive a JWT. |
| GET | `/api/auth/me` | Authenticated | Retrieve the current account. |

### 2. AI Chat and Conversations

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/api/chat/agents` | Authenticated | List available AI support agents. |
| GET | `/api/chat/conversations` | Authenticated | List the current user's conversations. |
| GET | `/api/chat/conversations/:conversation_id` | Authenticated | Retrieve a conversation or create one using `new` where supported. |
| POST | `/api/chat/message` | Authenticated | Submit a message to the AI service. |
| POST | `/api/chat/feedback` | Authenticated | Submit feedback on a message. |

### 3. Ticket Management

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/api/tickets` | Authenticated | List accessible tickets. |
| GET | `/api/tickets/:id` | Authenticated | Retrieve a ticket. |
| POST | `/api/tickets` | Authenticated | Create a support ticket. |
| PATCH | `/api/tickets/:id` | Agent or Admin | Update ticket status, priority, or assignment. |

### 4. Knowledge-Base Management

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/api/kb` | Authenticated | List knowledge-base documents. |
| POST | `/api/kb` | Admin | Save a document and request re-indexing. |

### 5. Analytics

| Method | Endpoint | Access | Description |
|---|---|---|---|
| GET | `/api/analytics` | Admin | Retrieve dashboard analytics. |

*Access permissions and request formats are determined by the backend implementation.*

---

## 🧠 AI Service API

The Python AI service exposes endpoints for health checks, AI agent information, service statistics, chat, and knowledge-base ingestion.

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Check AI service health. |
| GET | `/ai/agents` | Retrieve AI support agent information. |
| GET | `/ai/stats` | Retrieve AI service statistics. |
| POST | `/ai/chat` | Process an AI chat request. |
| POST | `/ai/ingest` | Ingest or re-index knowledge-base content. |

**Base URL:** `http://localhost:8000`

The AI service uses Python's standard-library HTTP server, the `requests` package, and the project's retrieval and agent modules.

According to the project configuration, a separate model API key is not required. The exact retrieval and response-generation capabilities depend on the implementation of the local AI modules.

---

## 🧪 Testing and Build

Run these commands from the repository root.

### Run Backend Tests

```bash
npm run test:server
```

### Run Frontend Tests

```bash
npm run test:client
```

### Build the Frontend

```bash
npm run build:client
```

These commands use scripts configured in the root `package.json`. Confirm that the corresponding scripts and test dependencies are present before running them.

---

## ⚙️ Configuration

TechPro AI supports configuration options for the backend, AI service, and frontend.

### Backend Configuration

| Variable | Default | Purpose |
|---|---|---|
| `PORT` | `5005` | Port used by the Express server. |
| `AI_SERVICE_URL` | `http://localhost:8000` | Base URL of the Python AI service. |
| `JWT_SECRET` | Project-configured default, if any | Secret used for JWT signing and verification. |

Configure production secrets using environment variables rather than hardcoding them.

Example backend `.env` configuration:

```env
PORT=5005
AI_SERVICE_URL=http://localhost:8000
JWT_SECRET=replace_with_a_long_random_secret
```

Use a unique, securely generated JWT secret in any shared or production environment.

### AI Service Configuration

The AI service uses port `8000` by default and also reads the `PORT` environment variable.

### Frontend Configuration

The frontend currently uses localhost URLs in:

```text
client/src/config.js
```

When deploying the application, update the frontend configuration to use the appropriate hosted backend API and Socket.IO addresses.

---

## 🔒 Security Considerations

Before exposing TechPro AI publicly, address the following security requirements:

- Replace all demo credentials and default secrets.
- Configure a strong, unique `JWT_SECRET`.
- Ensure passwords are securely hashed and verified by the backend.
- Enforce role-based authorization on every protected operation.
- Configure production CORS rules.
- Use HTTPS for public-facing services.
- Validate and sanitize user input.
- Protect knowledge-base ingestion and document-management endpoints.
- Avoid exposing internal AI service endpoints unnecessarily.
- Replace JSON file persistence with a suitable database for production workloads.
- Back up application data and avoid committing real customer information.
- Add appropriate rate limiting, logging, and error handling.

**Note:** These are deployment recommendations, not a claim that every security control is already implemented.

---

## 🔮 Future Enhancements

Potential improvements for future versions include:

- Integration with a production-grade database.
- Improved semantic search and vector-based retrieval.
- Enhanced document parsing for PDF and DOCX files.
- More advanced AI response evaluation.
- Expanded ticket assignment and escalation workflows.
- Email notifications for ticket updates.
- More detailed analytics and reporting.
- Improved accessibility and multilingual support.
- Automated deployment and continuous integration.
- Production-ready monitoring and audit logging.

These are possible future improvements and may not be implemented in the current version.

---


## 👩‍💻 Author

**TechPro AI — AI-Powered Customer Support Platform**

Built to explore the integration of full-stack web development, retrieval-augmented generation, and real-time customer support workflows.

---

⭐ **If you find this project useful, consider giving the repository a star!**

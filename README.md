# Task Manager App

A full-stack task manager application built with:

* 🧠 Backend: Go (with Gorilla Mux)
* 💻 Frontend: Vue.js + TypeScript
* 🐳 DevOps: Docker (upcoming)
* ☁️ Architecture: Cloud-native REST API

## 📦 Project Structure

```
task-manager-app/
├── backend/             # Go backend with REST API
│   ├── main.go
│   ├── model.go
│   └── Dockerfile
│
├── frontend/            # Vue 3 + TS frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── TaskForm.vue
│   │   │   └── TaskList.vue
│   │   ├── App.vue
│   │   ├── main.ts
│   │   └── types.ts
│   └── Dockerfile
│
├── docker-compose.yml  # Service orchestration
└── README.md            # Project documentation
```

---

## ✅ Phase 2: Go Backend API (Completed)

* Implemented `Task` model
* Created CRUD routes: `GET`, `POST`, `PUT`, `DELETE`
* JSON response formats fixed (returns `[]` instead of `null`)
* Uses `gorilla/mux` for routing
* Backend listens on port `8088` (Jenkins uses 8080)

### 🔁 Endpoints

| Method | URL           | Description    |
| ------ | ------------- | -------------- |
| GET    | `/tasks`      | List all tasks |
| POST   | `/tasks`      | Add new task   |
| PUT    | `/tasks/{id}` | Update a task  |
| DELETE | `/tasks/{id}` | Delete a task  |

---

## 🔖 Phase 3: Vue.js Frontend Integration (Completed)

* Set up Vue 3 + TypeScript project
* Created reusable `TaskList.vue` and `TaskForm.vue` components
* Integrated Axios to communicate with Go backend
* Displayed tasks fetched from API (`GET /tasks`)
* Added new tasks via form (`POST /tasks`)
* TypeScript types defined in `src/types.ts`

### 📁 Component Overview

* `TaskList.vue`: Lists all current tasks from backend
* `TaskForm.vue`: Form to add new tasks with `title`, `description`, `status`

### 📲 API Base URL

```
http://localhost:8088
```

Frontend served via Vite at:

```
http://localhost:5173
```

---

## ✅ Phase 4: Edit & Delete in UI (Completed)

* Added "Edit" button with inline editable fields (title, description, status)
* Added "Delete" button to remove tasks
* Connected buttons to API endpoints (`PUT` and `DELETE`)
* Refreshed task list on each update to keep data in sync

### 🔹 UX Features

* Inline editing with Save / Cancel buttons
* Instant UI updates after changes
* Reuse of existing Task model and backend API

---


## ⚙️ Setup Instructions

### 1. Clone the repo

```bash
git clone https://github.com/Bhimesh1/taskmanager.git
cd taskmanager
```

### 2. Run with Docker Compose

```bash
docker compose up --build
```

* Backend will run on: [http://localhost:8088/tasks](http://localhost:8088/tasks)
* Frontend will run on: [http://localhost:5173](http://localhost:5173)

---

## 📌 Features

* Create, read, and list tasks
* Task model with ID, title, description, and status
* RESTful APIs (GET, POST)
* Responsive frontend using Vue.js 3 + TS
* Clean architecture and code separation

---

## 📮 Contact

**Bhimesh Patil** 

[GitHub](https://github.com/Bhimesh1) ・ [Email](mailto:bhimeshpatil1@gmail.com)

---

> Project created for learning and demonstration purposes. Contributions welcome!


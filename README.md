# 📋 ToDo App — Full-Stack JWT Authorization with Role-Based Access

A full-stack ToDo application built using **Node.js**, **Express**, **Sequelize**, and **React (Vite)**. Features secure **JWT-based authentication** (cookies only), **role-based access control**, and a clean, scalable project structure.

---

## ✨ Features

- ✅ JWT Authentication (HTTP-only cookies)
- ✅ Role-based access control (User, Admin)
- ✅ CRUD operations for Tasks
- ✅ Status transitions: `pending`, `in progress`, `completed`
- ✅ Admin can view all users’ tasks
- ✅ Users can manage only their own tasks
- ✅ Protected routes (React + React Router)
- ✅ AuthContext to handle session on frontend
- ✅ Backend architecture with layers:
  - Controllers
  - Services
  - Repositories
  - DTOs, middlewares
- ✅ Input validation with Joi
- ✅ Auto-create initial admin on start
- ✅ Production-ready environment switching
- ✅ Clean UI using minimal custom styling

---

## 🧱 Tech Stack

**Frontend:**
- React (Vite)
- Axios
- React Router DOM

**Backend:**
- Node.js
- Express
- Sequelize (MySQL)
- JWT (cookie only)
- dotenv
- cookie-parser
- Joi
- CORS
- Winston (Logger)

---

## 🚀 Getting Started

### 🔧 Development Mode

#### Backend

```bash
cd backend
npm install
npm run dev
```

#### Frontend

```bash
cd frontend
npm install
npm run dev
```

#### 🧪 Environment Variables

Create `.env` in `/backend`:

```env
//Example
SERVER_PORT=3000
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=12345
DB_NAME=mydb

JWT_SECRET=holiday
JWT_EXPIRES_IN=1d
INIT_ADMIN_PASSWORD=Admin12345

FRONTEND_URL=http://localhost:5173
NODE_ENV=development
```

---

### 📦 Production Mode

1. Build frontend:

```bash
cd frontend
npm run build
```

2. Start backend in production:

```bash
cd backend
npm install
npm start
```

✅ Make sure `NODE_ENV=production` in `.env`  
✅ Vite will generate static files into `backend/public`

---

## 🔐 API Endpoints

> All endpoints are prefixed with `/api`

### 🛡️ Auth

| Method | Endpoint         | Description                                  | Access        | Role          |
|--------|------------------|----------------------------------------------|---------------|---------------|
| POST   | `/auth/register` | Register a new user                          | Public        | —             |
| POST   | `/auth/login`    | Authenticate user and issue JWT cookie       | Public        | —             |
| POST   | `/auth/logout`   | Logout current user (clears auth cookie)     | Authenticated | User/Admin    |
| GET    | `/auth/me`       | Fetch authenticated user's information       | Authenticated | User/Admin    |


### 📋 Tasks

| Method | Endpoint         | Description                                                | Access        | Role          |
|--------|------------------|------------------------------------------------------------|---------------|---------------|
| GET    | `/tasks`         | Fetch tasks belonging to the authenticated user           | Authenticated | User/Admin    |
| GET    | `/tasks/:id`     | Fetch specific task (only owner or admin has access)      | Authenticated | User/Admin    |
| POST   | `/tasks`         | Create a new task under the authenticated user's account  | Authenticated | **User only** |
| PUT    | `/tasks/:id`     | Update task (title, description, status) if user is owner | Authenticated | **User only** |
| DELETE | `/tasks/:id`     | Delete a task (only owner or admin can delete)            | Authenticated | User/Admin    |
| GET    | `/tasks/all`     | Fetch all tasks in the system                             | Authenticated | **Admin only** |

---

## 🗂 Folder Structure

```bash
backend/
├── src/
│   ├── controllers/
│   ├── middlewares/
│   ├── database/
│   ├── dtos/
│   ├── constants/
│   ├── models/
│   ├── repositories/
│   ├── routes/
│   ├── services/
│   ├── logs/
│   └── utils/

frontend/
├── src/
│   ├── components/
│   ├── context/
│   └── pages/
```

---

## 📌 Future Enhancements

- [ ] Pagination for task list
- [ ] Filtering by status/date
- [ ] Task deadlines and reminders
- [ ] Profile management (change password, username)
- [ ] Admin dashboard (user overview, task stats)
- [ ] Unit & Integration tests
- [ ] CI/CD with GitHub Actions
- [ ] Dockerization

---

## 📄 License

MIT — free to use for any purpose.

---

> Designed and developed with ❤️ to simulate a real-world production-ready workflow.

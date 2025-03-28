# ToDo App — Full-Stack JWT Authorization with Role-Based Access

A full-stack ToDo application built using **Node.js**, **Express**, **Sequelize**, and **React (Vite)**. Features secure **JWT-based authentication** (cookies only), **role-based access control**, and a clean, scalable project structure.

## Features

- **JWT Authentication** via HTTP-only cookies
- **Role-based access control** (User, Admin)
- **CRUD operations** for Tasks
- Admin can view all tasks
- Users can only access their own tasks
- Status updates for tasks: `pending`, `in progress`, `completed`
- Responsive and minimalist UI (React)
- **Protected routes** and AuthContext on the client side
- Modular backend with layered architecture:
  - Controllers
  - Services
  - Repositories
- DTOs, middlewares, validation (Joi)
- Auto-create initial admin user on launch

## Tech Stack

**Frontend:**
- React (Vite)
- Axios
- React Router

**Backend:**
- Node.js
- Express
- Sequelize (MySQL)
- JWT
- dotenv
- cookie-parser
- CORS
- Joi

---

## API Endpoints

All endpoints are prefixed with `/api`.

### Auth

| Method | Endpoint         | Description                 | Access       |
|--------|------------------|-----------------------------|--------------|
| POST   | `/auth/register` | Register new user           | Public       |
| POST   | `/auth/login`    | Login user                  | Public       |
| POST   | `/auth/logout`   | Logout user (clears cookie) | Authenticated |
| GET    | `/auth/me`       | Get current user from token | Authenticated |

### Tasks

| Method | Endpoint              | Description                             | Access       |
|--------|-----------------------|-----------------------------------------|--------------|
| GET    | `/tasks`              | Get user's tasks                         | Authenticated |
| GET    | `/tasks/:id`          | Get task by ID (user or admin only)     | Role-based   |
| POST   | `/tasks`              | Create new task                          | Authenticated |
| PUT    | `/tasks/:id`          | Update task (title, description, status)| Owner/Admin  |
| DELETE | `/tasks/:id`          | Delete task                              | Owner/Admin  |
| GET    | `/tasks/all`          | Get all tasks (admin only)              | Admin        |

---

## Folder Structure

```
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

## Getting Started

### Development Mode

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

#### Environment Variables


Backend `.env`:

```
SERVER_PORT=Server port //3000
DB_HOST=DB host //localhost
DB_PORT=DB port //3306
DB_USER=DB user //root
DB_PASSWORD=DB password //DataBase12345
DB_NAME=DB name //mydb
JWT_SECRET=JWT secret key //holiday
JWT_EXPIRES_IN=JWT before date //1d
INIT_ADMIN_PASSWORD=Admin password //Admin12345
FRONTEND_URL=Frontend URL for Cors in develop mod //http://localhost:5173
NODE_ENV=development/production //Select one
```


```

### Production Mode

1. Build frontend:
```bash
cd frontend
npm run build
```

2. Serve with backend:
```bash
cd backend
npm install
npm start
```

Ensure `NODE_ENV=production` in your backend `.env` file.

---

## Future Improvements

- [ ] Pagination for tasks
- [ ] Filters by status/date
- [ ] Task deadlines & reminders
- [ ] Profile editing (username, password)
- [ ] Admin dashboard
- [ ] Unit & integration testing
- [ ] CI/CD pipeline (GitHub Actions)
- [ ] Docker integration

---

## License

MIT — Free to use for any purpose.

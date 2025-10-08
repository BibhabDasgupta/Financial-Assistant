# Personal Finance Assistant

A **full-stack, production-ready Personal Finance Assistant** that helps users manage their income, expenses, budgets, recurring transactions, and receipts — complete with analytics, exports, and notifications.

**Demo Video Link:** [https://shorturl.at/RuPgR](https://shorturl.at/RuPgR)

It includes:

* A **Node.js + Express backend** with OAuth, JWT, OCR, background jobs, and analytics.
* A **React + TypeScript frontend** built with Vite and Tailwind CSS for a modern, responsive user experience.

---

## 📘 Design Models and Documentation

| Model / Document | Link |
| ---------------- | ---- |
| System Architecture Diagram | [View Architecture Diagram](https://shorturl.at/hrW6j) |
| Use Case Diagram | [View Use Case Diagram](https://shorturl.at/WnVB5) |
| Entity Relationship Diagram (ERD) | [View ERD](https://shorturl.at/e7Fsf) |
| Sequence Diagram for OAuth | [View Sequence Diagram for OAuth](https://drive.google.com/file/d/1CpNpMwJ_RNSnvj1bJKLPeevAFXt2FgsQ/view?usp=sharing) |
| Sequence Diagram for OCR Processing | [View Sequence Diagram for OCR Processing](https://drive.google.com/file/d/1XiqVd1LffUdhVYs6Qo1UDa6DW2On1aEk/view?usp=sharing) |
| Sequence Diagram for Budget Check | [View Sequence Diagram for Budget Check](https://drive.google.com/file/d/1gjEYp-ejcM693oYz2sDrvkEFiOTYc9qb/view?usp=sharing) |

---

## 📦 Repositories

| Component                | Repository                                                                                     | Tech Stack                                                         |
| ------------------------ | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Backend (API Server)** | [Financial-Assistant-Backend](https://github.com/BibhabDasgupta/Financial-Assistant-Backend)   | Node.js, Express, Sequelize (PostgreSQL), Redis, Passport.js, Bull |
| **Frontend (Web App)**   | [Financial-Assistant-Frontend](https://github.com/BibhabDasgupta/Financial-Assistant-Frontend) | React 18, TypeScript, Vite, Tailwind CSS, React Query              |

---

## 🧱 Repository Layout

Now your structure looks like this:

```
Financial-Assistant/
├── frontend/   → linked to Financial-Assistant-Frontend repo
├── backend/    → linked to Financial-Assistant-Backend repo
└── README.md   → overview (the one you’re reading)
```

When someone clones your main repo, they should run:

```bash
git clone --recurse-submodules https://github.com/BibhabDasgupta/Financial-Assistant.git
```

This ensures the frontend and backend submodules are cloned automatically.

---

## 🧠 Overview

The **Finance Assistant** allows authenticated users to:

* Track income and expenses
* Manage budgets and categories
* Upload receipts (with OCR extraction)
* Automate recurring transactions
* View detailed analytics dashboards
* Import/export financial data (PDF, CSV, Excel)
* Receive personalized alerts and notifications

---

## 🏗️ System Architecture

```
Frontend (React + Vite)
        │
        ▼
Backend API (Express.js)
        │
 ┌────────────┬────────────┬────────────┐
 │ PostgreSQL │   Redis    │  Bull Jobs │
 │ (Supabase) │ (Caching)  │ (Workers)  │
 └────────────┴────────────┴────────────┘
```

* **PostgreSQL / Supabase:** Data persistence
* **Redis:** Caching, rate-limiting, session & token management
* **Bull / node-cron:** Background job queue for OCR, reports, and notifications
* **Multer + Tesseract.js + pdf-parse:** File upload and text extraction
* **JWT + OAuth:** Secure authentication (Google, GitHub)

---

## 🚀 Features

✅ OAuth login (Google / GitHub)
✅ JWT auth with refresh tokens & blacklist
✅ CRUD for transactions, budgets, and categories
✅ OCR-based receipt parsing
✅ Recurring transaction management
✅ Analytics dashboards and summaries
✅ Import (PDF) and Export (CSV/Excel/PDF)
✅ Notifications and alerts
✅ Rate limiting, caching, and background workers
✅ Docker support for production deployment

---

## 🧩 Tech Stack Summary

### **Backend**

| Category        | Technology                      |
| --------------- | ------------------------------- |
| Language        | Node.js (v18+)                  |
| Framework       | Express.js                      |
| ORM             | Sequelize                       |
| Database        | PostgreSQL / Supabase           |
| Caching         | Redis                           |
| Authentication  | Passport.js (OAuth) + JWT       |
| Validation      | Joi                             |
| Background Jobs | Bull + node-cron                |
| File Handling   | Multer, Tesseract.js, pdf-parse |
| Logging         | Winston                         |
| Testing         | Jest, Supertest                 |
| Deployment      | Docker, Docker Compose          |

### **Frontend**

| Category           | Technology                   |
| ------------------ | ---------------------------- |
| Framework          | React 18 + Vite              |
| Language           | TypeScript                   |
| Styling            | Tailwind CSS                 |
| UI Components      | Radix UI + shadcn-ui         |
| Data Fetching      | React Query + Axios          |
| Routing            | React Router v6              |
| Forms & Validation | React Hook Form + Zod        |
| Charts             | Recharts                     |
| Notifications      | Sonner (toast)               |
| State Management   | Context API (Auth, Theme)    |
| Testing            | Jest + React Testing Library |

---

## ⚙️ Getting Started

### 🧰 Prerequisites

* Node.js ≥ 18
* PostgreSQL (or Supabase)
* Redis
* npm / yarn
* (optional) Docker & Docker Compose

---

## 🖥️ Backend Setup

Clone the backend repository:

```bash
git clone https://github.com/BibhabDasgupta/Financial-Assistant-Backend.git
cd Financial-Assistant-Backend
```

### Environment Setup

Copy `.env.example` → `.env` and configure:

```env
NODE_ENV=development
PORT=5000
API_VERSION=v1

DATABASE_URL=postgresql://user:password@localhost:5432/finance
REDIS_HOST=localhost
REDIS_PORT=6379

JWT_SECRET=supersecretkey
JWT_EXPIRE=1h
JWT_REFRESH_EXPIRE=7d

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_secret
GOOGLE_CALLBACK_URL=http://localhost:5000/api/v1/auth/google/callback

GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_secret
GITHUB_CALLBACK_URL=http://localhost:5000/api/v1/auth/github/callback

FRONTEND_URL=http://localhost:5173
```

### Run Locally

```bash
npm install
npm run dev
```

### Production

```bash
npm start
```

### Migrations

```bash
npm run migrate
npm run seed
```

---

## 🧮 Frontend Setup

Clone the frontend repository:

```bash
git clone https://github.com/BibhabDasgupta/Financial-Assistant-Frontend.git
cd Financial-Assistant-Frontend
```

### Environment Setup

Create `.env` file:

```env
VITE_API_BASE_URL=http://localhost:5000
VITE_API_VERSION=v1
VITE_API_URL=http://localhost:5000/api/v1
```

### Run Locally

```bash
npm install
npm run dev
```

### Build for Production

```bash
npm run build
npm run preview
```

---

## 🧭 API Overview

### Authentication

| Endpoint               | Method | Description        |
| ---------------------- | ------ | ------------------ |
| `/api/v1/auth/google`  | GET    | Start Google OAuth |
| `/api/v1/auth/github`  | GET    | Start GitHub OAuth |
| `/api/v1/auth/refresh` | POST   | Refresh JWT        |
| `/api/v1/auth/logout`  | POST   | Revoke JWT         |
| `/api/v1/auth/me`      | GET    | Get current user   |

### Transactions

| Endpoint                   | Method | Description           |
| -------------------------- | ------ | --------------------- |
| `/api/v1/transactions`     | POST   | Create transaction    |
| `/api/v1/transactions`     | GET    | List all transactions |
| `/api/v1/transactions/:id` | PUT    | Update transaction    |
| `/api/v1/transactions/:id` | DELETE | Delete transaction    |

…and more for **budgets**, **categories**, **receipts**, **analytics**, **recurring transactions**, and **notifications**.

For detailed validation schemas → see `src/utils/validation.js`.

---

## 🧾 Frontend Key Pages

| Page            | Route                       | Description |
| --------------- | --------------------------- | ----------- |
| `/`             | Landing page                |             |
| `/login`        | OAuth login page            |             |
| `/dashboard`    | Overview with KPIs          |             |
| `/transactions` | Transaction table + filters |             |
| `/analytics`    | Visual reports & graphs     |             |
| `/budgets`      | Category-wise budgets       |             |
| `/receipts`     | Uploaded receipts + OCR     |             |
| `/recurring`    | Recurring transactions      |             |
| `/settings`     | User profile, theme, logout |             |

---

## 🧠 Folder Structures

### **Backend**

```
src/
 ├── config/           # Database, Redis, Passport
 ├── controllers/      # API handlers
 ├── routes/           # Express routes
 ├── models/           # Sequelize models
 ├── services/         # Business logic
 ├── dao/              # Data access layer
 ├── middleware/       # Auth, validation, rate limit
 ├── jobs/ & workers/  # Bull queue jobs
 ├── utils/            # Helpers, logger, validation
 ├── uploads/          # Uploaded receipts
 └── app.js / server.js
```

### **Frontend**

```
src/
 ├── components/       # Reusable UI (shadcn-style)
 ├── pages/            # Page views
 ├── context/          # Auth & Theme providers
 ├── hooks/            # Custom React hooks
 ├── services/         # API clients (Axios)
 ├── lib/              # Utilities
 ├── assets/           # Static icons/images
 └── App.tsx / main.tsx
```

---

## 🧰 Development Notes

* Use **Postman** or **Thunder Client** to test backend endpoints
* Use **React Query Devtools** for frontend debugging
* Keep backend running at `http://localhost:5000` when developing frontend
* JWT tokens are stored in `localStorage` (future improvement: cookies)

---

## 🧪 Testing

### Backend

```bash
npm test
```

### Frontend

```bash
npm run test
```

---

## 🐳 Docker Deployment

The project includes `Dockerfile` and `docker-compose.yml` for containerized deployment.

```bash
docker-compose up --build
```

This sets up:

* Node.js API container
* PostgreSQL database
* Redis cache

---

## 🔐 Security Recommendations

* Rotate JWT secrets regularly
* Use HTTPS in production
* Configure CORS carefully
* Store tokens in `httpOnly` cookies for enhanced security
* Move uploaded files to S3 or secure cloud storage

---

## 📈 Future Enhancements

* Add Swagger / OpenAPI documentation
* Integrate email alerts (Nodemailer)
* Machine learning expense categorization
* GraphQL or gRPC microservice support
* Enhanced CI/CD with GitHub Actions

---

## 🧑‍💻 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📬 Contact

**Developer:** [Bibhab Dasgupta](https://github.com/BibhabDasgupta)
🌐 Backend Repo: [Financial-Assistant-Backend](https://github.com/BibhabDasgupta/Financial-Assistant-Backend)
🌐 Frontend Repo: [Financial-Assistant-Frontend](https://github.com/BibhabDasgupta/Financial-Assistant-Frontend)

---

✅ **Summary**:
This `README.md` is now perfect for **main repository** — it contains:

* links to both sub-repos
* submodule cloning instruction
* structure overview
* all project details (features, setup, API, architecture, etc.)

---

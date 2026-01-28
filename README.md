Markdown
# Mini CRM Backend

A production-ready REST API for managing Users, Customers, and Tasks. Built with **NestJS**, **Prisma**, and **PostgreSQL**. This project demonstrates a scalable backend architecture with strict Role-Based Access Control (RBAC), JWT Authentication, and clean code practices.

## 🚀 Tech Stack

* **Framework:** [NestJS](https://nestjs.com/) (TypeScript)
* **Database:** PostgreSQL
* **ORM:** Prisma
* **Authentication:** Passport-JWT & Bcrypt
* **Documentation:** Swagger / OpenAPI
* **Containerization:** Docker Compose (for Database)

---

## 📋 Features

### 1. Authentication & Security
* **JWT-based Auth:** Secure login and registration.
* **Role-Based Access Control (RBAC):** Distinct `ADMIN` and `EMPLOYEE` roles.
* **Password Hashing:** Bcrypt implementation for security.
* **Guards:** Global protection for private routes.

### 2. User Management
* **Admin Only:** Admins can view and manage user roles.

### 3. Customer Management (CRM)
* **CRUD Operations:** Full lifecycle management for customer data.
* **Pagination:** Efficient data fetching with page/limit queries.
* **Uniqueness:** Enforced constraints on Email and Phone.

### 4. Task Management
* **Relational Logic:** Tasks linked to both Employees and Customers.
* **Ownership Security:**
    * **Admins:** Can view and manage *all* tasks.
    * **Employees:** Can only view and update tasks *assigned to them*.
* **Status Workflow:** `PENDING` -> `IN_PROGRESS` -> `DONE`.

---

## 🛠️ Installation & Setup

### Prerequisites
* Node.js (v18 or higher)
* Docker Desktop (for PostgreSQL)

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd mini-crm-backend
2. Install Dependencies
Bash
npm install
3. Environment Configuration
Create a .env file in the root directory:

Bash
cp .env.example .env
(Update DATABASE_URL in .env if necessary. Default is configured for Docker).

🗄️ Database Setup
1. Start PostgreSQL (via Docker)
Ensure Docker Desktop is running, then start the database container:

Bash
docker-compose up -d
2. Run Migrations
Push the Prisma schema to the database:

Bash
npx prisma migrate dev --name init_schema
3. Generate Prisma Client
Bash
npx prisma generate
⚡ Running the Application
Development Mode
Bash
npm run start:dev
Server will start at: http://localhost:3000

📖 API Documentation (Swagger)
The API is fully documented using Swagger. Once the server is running, visit:

👉 http://localhost:3000/api

You can test endpoints directly from the interface:

Register a new user (Role: ADMIN).

Login to get the accessToken.

Click Authorize at the top right and paste the token: Bearer <your_token>.

Test protected routes (Users, Customers, Tasks).

🧪 Testing
Health Check
HTTP
GET /health
Example: Admin User Setup
POST /auth/register

JSON
{
  "name": "Admin User",
  "email": "admin@example.com",
  "password": "password123",
  "role": "ADMIN"
}
📂 Project Structure
Bash
src/
├── auth/           # Auth logic, Strategies, Guards
├── common/         # Global Decorators (@Roles) and Guards
├── customers/      # Customer CRUD & Pagination
├── tasks/          # Task Management & RBAC Logic
├── users/          # User Management
├── prisma/         # Database Service
└── main.ts         # App Entry & Swagger Config
🤝 Submission Details
Assignment: Backend Intern Assignment

Submitted by: Kunal Prajapati

Submission Date: 28-Jan-2026
# JobHive — Full Stack Job Board App (MERN)

A complete job board built with MongoDB, Express.js, React.js, and Node.js.

## Features

**Job Seekers**
- Browse and search jobs with filters (type, category, experience, remote)
- Save jobs to apply later
- Apply with resume upload and cover letter
- Track application status (pending → reviewed → shortlisted → hired)
- Manage profile and upload resume

**Employers**
- Post jobs with full details (salary, requirements, skills)
- View all applicants per job
- Update application status with email notifications

**General**
- JWT-based authentication (register/login)
- Role-based access (jobseeker / employer)
- Email notifications on apply and status change
- Resume upload via Cloudinary
- Pagination, full-text search, and filters

---

## Project Structure

```
job-board/
├── client/                  ← React frontend
│   └── src/
│       ├── pages/           Home, Jobs, JobDetail, Login, Register, Dashboard, PostJob, Profile
│       ├── components/      Navbar, JobCard, SearchBar
│       ├── context/         AuthContext (JWT auth state)
│       └── utils/           api.js (axios), helpers.js
└── server/                  ← Node.js + Express backend
    ├── models/              User.js, Job.js, Application.js
    ├── routes/              auth.js, jobs.js, applications.js, users.js
    ├── middleware/          auth.js (JWT protect), errorHandler.js
    └── config/              db.js (MongoDB), cloudinary.js (file uploads)
```

---

## Quick Start

### 1. Clone and install dependencies

```bash
git clone https://github.com/jayashree200/websites.git
cd job-board
npm run install-all
```

### 2. Set up environment variables

```bash
cd server
cp .env.example .env
# Edit .env with your MongoDB URI, JWT secret, Cloudinary keys, and Gmail credentials
```

### 3. Set up MongoDB Atlas (free)

1. Go to https://www.mongodb.com/atlas
2. Create a free cluster
3. Get your connection string and paste it into `MONGO_URI` in `.env`

### 4. Set up Cloudinary (free, for resume uploads)

1. Go to https://cloudinary.com
2. Copy your Cloud Name, API Key, API Secret into `.env`

### 5. Set up Gmail for email notifications

1. Enable 2FA on your Gmail account
2. Generate an App Password (Google Account → Security → App Passwords)
3. Use your Gmail and the app password in `.env`

### 6. Run the app

```bash
# From root directory — runs both server and client
npm run dev
```

- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

---

## API Endpoints

### Auth
| Method | Route | Access | Description |
|--------|-------|--------|-------------|
| POST | /api/auth/register | Public | Register as jobseeker or employer |
| POST | /api/auth/login | Public | Login |
| GET | /api/auth/me | Private | Get current user |
| PUT | /api/auth/profile | Private | Update profile |
| PUT | /api/auth/change-password | Private | Change password |

### Jobs
| Method | Route | Access | Description |
|--------|-------|--------|-------------|
| GET | /api/jobs | Public | List jobs (search + filters + pagination) |
| GET | /api/jobs/:id | Public | Get single job |
| POST | /api/jobs | Employer | Post a new job |
| PUT | /api/jobs/:id | Employer | Update a job |
| DELETE | /api/jobs/:id | Employer | Delete a job |
| GET | /api/jobs/employer/my-jobs | Employer | Get all jobs posted by employer |

### Applications
| Method | Route | Access | Description |
|--------|-------|--------|-------------|
| POST | /api/applications/:jobId | Jobseeker | Apply to a job (with resume upload) |
| GET | /api/applications/my | Jobseeker | Get my applications |
| GET | /api/applications/job/:jobId | Employer | Get all applicants for a job |
| PUT | /api/applications/:id/status | Employer | Update application status |

### Users
| Method | Route | Access | Description |
|--------|-------|--------|-------------|
| POST | /api/users/upload-resume | Private | Upload resume to Cloudinary |
| POST | /api/users/save-job/:jobId | Private | Save/unsave a job |
| GET | /api/users/saved-jobs | Private | Get saved jobs |

---

## Deploy

**Frontend → Vercel (free)**
```bash
cd client && npm run build
# Connect to Vercel and deploy the /client folder
# Set REACT_APP_API_URL to your Render backend URL
```

**Backend → Render (free)**
```bash
# Connect your GitHub repo to Render
# Root directory: server
# Build command: npm install
# Start command: npm start
# Add all .env variables in Render dashboard
```

**Database → MongoDB Atlas (free tier)**

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18, React Router v6, Axios |
| Backend | Node.js, Express.js |
| Database | MongoDB + Mongoose |
| Auth | JWT (jsonwebtoken + bcryptjs) |
| File Upload | Multer + Cloudinary |
| Email | Nodemailer (Gmail SMTP) |
| Validation | express-validator |
| Deploy | Vercel (frontend) + Render (backend) + MongoDB Atlas |

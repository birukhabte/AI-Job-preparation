#  AI-Powered Job Preparation Platform

A production-ready full-stack GenAI web application that helps users prepare for job interviews by analyzing their resume against job descriptions, detecting skill gaps, generating personalized interview questions, and creating ATS-optimized resumes.

>  **Work in Progress** — BUG in gemini API integration.

---

##  Features

-  **Secure Authentication** — JWT with token blacklisting, OTP email verification, httpOnly cookies
-  **Resume Upload & Parsing** — Upload resume and job description for AI analysis
-  **Skill Gap Detection** — Gemini AI detects missing skills based on JD vs resume
-  **Interview Question Generation** — Role-specific technical and behavioural questions
-  **Personalized Prep Plan** — Structured preparation plan based on detected gaps
-  **ATS Resume Generation** — Puppeteer-based dynamic PDF resume tailored to the job

---

##  Tech Stack

### Frontend
| Tech | Purpose |
|---|---|
| React.js + Vite | UI framework |
| React Router | Client-side routing |
| Axios | HTTP requests |
| Context API | Global state management |
| SCSS | Styling |

### Backend
| Tech | Purpose |
|---|---|
| Node.js + Express.js | Server & API |
| MongoDB + Mongoose | Database |
| JWT | Authentication |
| bcrypt | Password hashing |
| cookie-parser | Cookie management |
| Gemini AI | AI features |
| Puppeteer | PDF generation |

---

##  Project Structure

```
GenAI/
├── Backend/
│   ├── src/
│   │   ├── controllers/                 # auth.controller.js , interview.controller.js
│   │   ├── models/                      # user.model.js, blacklist.model.js, report.model.js
│   │   ├── routes/                      # auth.route.js, interview.route.js
│   │   ├── middlewares/                 # auth.middleware.js, file.middleware.js 
│   │   ├── config/                      # database.js
│   │   ├── services/                    # ai.service.js
│   │   └── app.js
│   ├── .env                             # Never committed
│   ├── .gitignore
│   ├── package.json
│   └── server.js
├── Frontend/
│   ├── src/
│   │   ├── features/
│   │   │   ├── auth/
│   │   │   │   ├── components           # Protected.jsx
│   │   │   │   ├── hooks/               # useAuth.jsx
│   │   │   │   ├── pages/               # Login.jsx, Register.jsx
│   │   │   │   ├── styles/              # auth.form.scss
│   │   │   │   ├── services/            # auth.api.jsx
│   │   │   │   └── auth.context.jsx
│   │   │   └── interview/
│   │   │       ├── components           
│   │   │       ├── hooks/               # useInterview.jsx
│   │   │       ├── pages/               # Home.jsx, Interview.jsx
│   │   │       ├── styles/              # home.scss, interview.scss
│   │   │       ├── services/            # interview.api.jsx
│   │   │       └── interview.context.jsx
│   │   ├── styles/                      # button.scss
│   │   ├── App.jsx
│   │   ├── style.scss
│   │   └── main.jsx
│   ├── index.html
│   └── package.json
└── README.md
```

---

##  Getting Started

### Prerequisites
- Node.js v18+
- MongoDB (local or Atlas)
- Google Gemini API Key

### 1. Clone the repository
```bash
git clone https://github.com/Ri1tik/GenAI.git
cd GenAI
```

### 2. Setup Backend
```bash
cd Backend
npm install
```

Create `.env` file in `Backend/`:
```env
PORT=3000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_min_32_chars
GOOGLE_API_KEY=your_gemini_api_key
NODE_ENV=development
```

Start the backend:
```bash
node server.js
# or with auto-restart
nodemon server.js
```

### 3. Setup Frontend
```bash
cd Frontend
npm install
```

Create `.env` file in `Frontend/`:
```env
VITE_API_URL=http://localhost:3000
```

Start the frontend:
```bash
npm run dev
```

### 4. Open in browser
```
http://localhost:5173
```

---

##  API Endpoints

### Auth Routes — `/api/auth`

| Method | Endpoint | Access | Description |
|---|---|---|---|
| POST | `/register` | Public | Register a new user |
| POST | `/login` | Public | Login a user |
| GET | `/logout` | Public | Clear auth token from cookies and blacklist it |
| GET | `/getMe` | Private | Get details of the currently authenticated user |

### Interview Routes — `/api/interview`

| Method | Endpoint | Access | Description |
|---|---|---|---|
| POST | `/` | Private | Generate interview report based on candidate's resume, self description, and job description |
| GET | `/:interviewId` | Private | Get interview report by ID |
| GET | `/` | Private | Get all interview reports of the logged-in user |
| GET | `/resume/pdf/:interviewReportId` | Private | Download AI-generated resume PDF for the interview report |

---

##  Security Features

-  JWT stored in **httpOnly cookies** (not localStorage)
-  Token **blacklisting on logout** prevents session reuse
-  Passwords hashed with **bcrypt** (salt rounds: 10)
-  Protected routes via **Express middleware**
-  CORS configured with **credentials: true**
-  Environment variables validated on startup

---

##  Author

**Ritik Roshan Yadav**
-  B.Tech CSE — NIT Rourkela (CGPA: 9.03)
-  GitHub: [@Ri1tik](https://github.com/Ri1tik)
-  ritik.r.yadav0001@gmail.com

---

##  License

This project is for educational and portfolio purposes.




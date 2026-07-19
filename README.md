# 📋 AUREON 360 — AI-Powered HR Management System



AUREON 360 is an AI-powered HR Management System that combines natural language processing, document intelligence, automated workflows, and secure authentication to enable smart HR operations. Designed for both HR and employees, this system supports employee self-service, automated decision support, and structured HR actions.

---

## ✨ What’s Inside

### 🤖 AI HR Assistant
- Ask HR queries in plain English
- Employees see only their data ✅
- HR sees all data ✅
- Natural-language SQL execution for employee data queries
- Policy Q&A using **RAG (Retrieval-Augmented Generation)**

### 📝 Policy Q&A (PDF Upload)
- Upload HR policy PDFs
- Automatically index using FAISS
- Ask clean bullet-point questions like:
  - *“What is the maternity leave policy?”*

### 🌴 Leave Workflow (Fully Automated)

**Employee does:**
- Submit leave online
- Track approval status

**HR does:**
- Approve / Reject leave inside dashboard
- View pending approvals list

**Email & Notifications:**
- ✅ Email alert to HR when leave is requested
- ✅ Email notification to employee when updated
- ✅ Notification bell on UI
- ✅ Full audit logging

### 💳 Payslip Automation
- Generate professional PDF payslips
- Email employees directly from the system
- Stored PDFs in backend folder for history

### 🔐 OTP Login Security
- Email OTP authentication before login
- Valid 10 mins, single-use
- Logged for audit

---

## 🧱 Tech Stack

| Component | Technology |
|----------|------------|
| Frontend | React + Vite + Tailwind CSS |
| Backend | FastAPI, LangChain, FAISS, SQLite |
| LLM | Google Gemini |
| Embeddings | sentence-transformers/all-MiniLM-L6-v2 |
| Email | SMTP (Gmail App Password recommended) |

---

## 📦 Project Structure

hrms/
├─ backend/
│ ├─ main.py
│ ├─ config.py
│ ├─ agents/
│ │ ├─ main_agent.py
│ │ └─ policy/policy_agent.py
│ ├─ database/db_setup.py
│ ├─ utils/
│ │ ├─ email_utils.py
│ │ └─ payslip_generator.py
│ └─ uploads/ # CSV / PDF uploads
├─ frontend/
│ ├─ src/
│ │ ├─ App.jsx
│ │ ├─ components/
│ │ │ ├─ Login.jsx
│ │ │ ├─ Chat.jsx
│ │ │ ├─ LeaveRequestForm.jsx
│ │ │ ├─ HRPendingApprovals.jsx
│ │ │ └─ NotificationsBell.jsx
│ │ └─ services/api.js
│ └─ index.css
└─ README.md

---

## 🔐 Environment Variables

Create a file: `backend/.env`

~~~
# LLM / RAG
GEMINI_API_KEY=your_gemini_key
LLAMA_CLOUD_API_KEY=your_llama_parse_key

# Email SMTP
SMTP_SERVER=smtp.gmail.com
SMTP_PORT=587
EMAIL_USER=your_hr_mailbox@gmail.com
EMAIL_PASSWORD=your_app_password
EMAIL_DISABLE_SEND=false   # true = simulate, false = actually send

# Database & uploads
DATABASE_URL=sqlite:///./hr_employees.db
UPLOAD_DIR=./uploads
DB_PATH=hr_employees.db
EMBED_MODEL_NAME=sentence-transformers/all-MiniLM-L6-v2
FAISS_INDEX_PATH=./policy_faiss_index
~~~

---

## ▶️ Getting Started

### ✅ Backend Setup

~~~
cd backend
python -m venv .venv
# Windows:
.\.venv\Scripts\activate
# macOS/Linux:
# source .venv/bin/activate

pip install --upgrade pip
pip install -r requirements.txt

python -m uvicorn main:app --reload --host 0.0.0.0 --port 8000
~~~

> ⚠️ If reloader issues occur on Windows, run with:
~~~
uvicorn main:app --reload --host 0.0.0.0 --port 8000 --reload-exclude ".venv/*"
~~~

### ✅ Frontend Setup

~~~
cd frontend
npm install
npm run dev
~~~

**Launch URL:** http://localhost:5173

---

## 🔑 Login Flow (OTP Authentication)

1. Employee/HR enters ID or Email → Requests OTP  
2. System emails OTP (valid for 10 minutes)  
3. User verifies OTP → Login success  
4. Role-based portal access granted  

**Security guarantees:**
- ✔️ Secure authentication  
- ✔️ Single-use OTP  
- ✔️ Logged for auditing  
- ✔️ Separate HR & Employee experiences

---







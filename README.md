# Leave Management System

Leave Management System, branded as LeaveXact, is a full-stack HR application for employee leave requests, admin approvals, leave balances, calendars, audit logs, public holidays, and analytics.

## Tech Stack

| Layer | Tools |
| --- | --- |
| Frontend | Next.js 15, React 19, TypeScript |
| Backend | FastAPI, Python, SQLAlchemy, Pydantic |
| Database | SQLite by default, PostgreSQL supported |
| Auth | JWT bearer tokens, passlib password hashing |
| UI | Tailwind CSS, shadcn/ui, Radix UI, Lucide React |
| Forms/Validation | react-hook-form, Zod |
| Charts | Recharts |
| Timezone | Asia/Kolkata / IST-aware backend logic |

## Project Structure

```text
Leave Management System/
+-- lms-fe/
|   +-- app/admin/          # Admin portal pages
|   +-- app/employee/       # Employee portal pages
|   +-- app/api/            # Next.js proxy routes
|   +-- components/
|   +-- lib/
+-- lms-be/
    +-- app/
        +-- routes/         # auth, employee, leave, admin, analytics, logs
        +-- auth.py
        +-- crud.py
        +-- models.py
        +-- schemas.py
        +-- holidays.py
        +-- main.py
    +-- scripts/            # data helpers and reset scripts
```

## Backend Setup

```bash
cd "Leave Management System/lms-be"
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python run.py
```

API base URL: `http://localhost:8000`

### Backend Environment

Create `lms-be/.env`.

```env
DATABASE_URL=sqlite:///./data/leavexact.db
SECRET_KEY=change-me
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440
ALLOWED_ORIGINS=["http://localhost:3000"]
TIMEZONE=Asia/Kolkata
```

## Frontend Setup

```bash
cd "Leave Management System/lms-fe"
npm install
npm run dev
```

Create `lms-fe/.env`.

```env
NEXT_PUBLIC_BACKEND_URL=http://localhost:8000
```

## Main APIs

| Prefix | Purpose |
| --- | --- |
| `/api/auth` | Login, registration, profile, password, email changes |
| `/api/employees` | Employee CRUD |
| `/api/leave` | Leave requests and calendars |
| `/api/admin` | Approval, rejection, admin calendar |
| `/api/analytics` | Summary, employee, and department analytics |
| `/api/logs` | Audit log search and pagination |
| `/api/holidays` | Holiday data |

## Scripts

Backend helper scripts live in `lms-be/scripts` and cover sample leave population, balance resets, database viewing, and clearing leave records.


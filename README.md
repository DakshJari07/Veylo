# Veylo — AI-Powered Meeting Intelligence

**From conversations to clarity.**

Veylo is a full-stack AI-powered meeting intelligence platform designed to transform meeting conversations into structured, actionable information.

Instead of simply summarizing meetings, Veylo focuses on extracting decisions, tracking commitments, identifying unresolved questions, and highlighting potential project risks.

The goal is to help teams maintain accountability, improve collaboration, and ensure important discussions translate into meaningful progress.

## Key Features

### Project Management
- Create and manage projects.
- Organize meetings under individual projects.
- Maintain structured meeting records in PostgreSQL.

### Meeting Intelligence
- Store meeting transcripts and meeting details.
- Extract actionable information using an LLM-powered analysis pipeline.
- Generate structured meeting summaries.

### Action & Decision Tracking
- Track commitments, owners, deadlines, and statuses.
- Record decisions made during meetings.
- Maintain unresolved questions.
- Identify and categorize project risks.

### AI-Powered Extraction
- Analyze meeting transcripts using the OpenAI API.
- Extract structured information using validated JSON responses.
- Apply validation and safeguards to reduce unsupported AI-generated information.
- Handle API failures and invalid responses.

## Technology Stack

| Layer | Technologies |
|-------|-------------|
| Frontend | Next.js, React, TypeScript, Tailwind CSS |
| Backend | Python, FastAPI |
| Database | PostgreSQL |
| Database Hosting | Supabase |
| ORM | SQLAlchemy |
| AI Integration | OpenAI API |
| Validation | Pydantic |
| Testing | Pytest |
| Version Control | Git, GitHub |

## System Architecture

```text
                 Next.js Frontend
                        |
                        v
                   FastAPI Backend
                        |
              +---------+---------+
              |                   |
              v                   v
       PostgreSQL Database    OpenAI API
          (Supabase)              |
              |                   v
              |           Structured Extraction
              |                   |
              +---------+---------+
                        |
                        v
               Meeting Intelligence
```

## How It Works

1. A project is created through the backend API.
2. Meetings and their transcripts are associated with the project.
3. The meeting analysis service processes transcript content using an LLM.
4. The analysis produces structured summaries, commitments, decisions, questions, and risks.
5. The extracted information can be reviewed before being saved through the application's database endpoints.

**Current status:** The project and meeting APIs, relational database models, structured extraction service, and automated tests have been implemented. The frontend review workflow and full production deployment are still under development.

## Database Design

Veylo uses PostgreSQL with six primary tables:

- `projects`
- `meetings`
- `commitments`
- `decisions`
- `open_questions`
- `risks`

The relational structure allows meeting information to remain associated with projects while supporting longer-term tracking of decisions and commitments.

## Getting Started

### Prerequisites

- Python
- Node.js
- PostgreSQL database (Supabase recommended)
- OpenAI API key for live AI extraction

### 1. Clone the Repository

```bash
git clone https://github.com/DakshJari07/veylo.git
cd veylo
```

### 2. Backend Setup

Navigate to the backend directory:

```bash
cd backend
```

Create a Python virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.\.venv\Scripts\Activate.ps1
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Create a `.env` file inside the backend directory:

```env
DATABASE_URL=your_postgresql_connection_string
OPENAI_API_KEY=your_openai_api_key
```

Start FastAPI:

```bash
uvicorn app.main:app --reload
```

Backend API documentation:

http://127.0.0.1:8000/docs

### 3. Frontend Setup

Open another terminal and navigate to the frontend directory:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

The frontend will typically run at:

http://localhost:3000

## API Endpoints

### Projects
- `POST /projects`
- `GET /projects`
- `GET /projects/{project_id}`

### Meetings
- `POST /projects/{project_id}/meetings`
- `GET /projects/{project_id}/meetings`
- `GET /meetings/{meeting_id}`

### Meeting Intelligence
- `POST /analyze-meeting`

### Commitments
- `POST /projects/{project_id}/commitments`
- `GET /projects/{project_id}/commitments`

### Decisions
- `POST /projects/{project_id}/decisions`
- `GET /projects/{project_id}/decisions`

### Questions
- `POST /projects/{project_id}/questions`
- `GET /projects/{project_id}/questions`

### Risks
- `POST /projects/{project_id}/risks`
- `GET /projects/{project_id}/risks`

## Testing

The backend includes automated tests covering meeting analysis, request validation, and error handling.

Run:

```bash
cd backend
python -m pytest
```

The meeting-analysis tests use mocked LLM responses, allowing validation without making paid API requests.

## Development Roadmap

- [x] FastAPI backend setup
- [x] Supabase PostgreSQL integration
- [x] Project and meeting management APIs
- [x] Commitments, decisions, questions, and risks APIs
- [x] LLM-based structured extraction integration
- [x] Automated meeting-analysis tests
- [ ] Frontend dashboard and project workspace
- [ ] AI extraction review and approval interface
- [ ] User authentication
- [ ] Commitment status management
- [ ] Production deployment
- [ ] Real-user testing and feedback

## Project Vision

Veylo aims to go beyond traditional meeting summarization.

Its long-term objective is to provide teams with a centralized workspace where meeting outcomes become trackable actions, decisions remain accessible, and unresolved issues are visible across a project's lifecycle.

---

**Veylo — From conversations to clarity.**

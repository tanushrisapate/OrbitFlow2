# Orbit Flow

**Plan. Track. Collaborate.** Orbit Flow is a web app for managing workspaces, projects, tasks and team progress in one place.

> **Status: early development.** The frontend project is set up and the landing page is started. The backend, database and the app screens are planned but not built yet. Features are listed as available only once they are coded and tested.

---

## Table of contents

- [Features](#features)
- [Current status](#current-status)
- [Tech stack](#tech-stack)
- [Project structure](#project-structure)
- [Getting started](#getting-started)
- [Available scripts](#available-scripts)
- [Planned architecture](#planned-architecture)
- [Data model](#data-model)
- [Roadmap](#roadmap)
- [Author](#author)

---

## Features

Planned:

- **Workspaces:** organise your teams.
- **Projects:** plan and track work inside a workspace.
- **Tasks:** assign to team members, set priority and deadline, update status.
- **Comments and activity:** discuss tasks and keep a record of changes.
- **Analytics:** completed, pending and overdue tasks, plus a weekly completion trend.

## Current status

| Area | State |
| --- | --- |
| Frontend project (React and Vite) | Set up |
| Landing page (navbar, hero, feature section) | In progress |
| Dashboard, workspace, project and task screens | Not started |
| Backend API (FastAPI) | Not started |
| Database (PostgreSQL) | Not started |
| Authentication | Not started |

## Tech stack

**In the repository now**

| Layer | Technology |
| --- | --- |
| UI library | React 19 |
| Build tool and dev server | Vite |
| Linting | Oxlint |
| Landing page | HTML and CSS |

**Planned**

| Layer | Technology |
| --- | --- |
| Backend | Python, FastAPI, Pydantic |
| Database access | SQLAlchemy, Alembic migrations |
| Database | PostgreSQL |
| Testing | Pytest, Postman |

## Project structure

```
OrbitFlow2/
└── frontend/
    ├── index1.html            # early plain-HTML draft of the home page
    ├── package.json           # dependencies and scripts
    ├── vite.config.js
    └── src/
        ├── main.jsx           # React entry point
        ├── App.jsx            # root component (still the Vite starter)
        ├── index.css
        ├── App.css
        ├── css/
        │   └── style.css      # styles for the landing page
        └── pages/
            └── index.html     # landing page: navbar, hero, feature section
```

A `backend/` folder will be added when the API work starts.

## Getting started

### Prerequisites

- [Node.js](https://nodejs.org/) (current LTS) and npm
- Git

### Run the frontend

```bash
git clone https://github.com/tanushrisapate/OrbitFlow2.git
cd OrbitFlow2/frontend
npm install
npm run dev
```

Vite prints a local address (usually `http://localhost:5173`). Open it in your browser.

## Available scripts

Run these from the `frontend/` folder.

| Command | What it does |
| --- | --- |
| `npm run dev` | Starts the development server with hot reload |
| `npm run build` | Creates a production build |
| `npm run preview` | Serves the production build locally |
| `npm run lint` | Checks the code with Oxlint |

## Planned architecture

```
Browser (React)  ──HTTP / JSON──▶  FastAPI  ──SQLAlchemy──▶  PostgreSQL
```

The frontend sends JSON requests to the API. FastAPI validates them with Pydantic, saves data through SQLAlchemy, and returns JSON. Schema changes are tracked with Alembic migrations.

## Data model

| Entity | Purpose | Relationship |
| --- | --- | --- |
| Workspace | Top-level container for a team's work | Has many projects |
| Project | A body of work inside a workspace | Belongs to one workspace; has many tasks |
| Task | A unit of work with priority, deadline and status | Belongs to one project; assigned to one member; has many comments |
| Member | A person in a workspace | Many-to-many with workspaces; can have many tasks |
| Comment | A discussion note on a task | Belongs to one task and one member |
| Activity | A record of a change or event | Linked to a project or task |

## Roadmap

- [x] Create the frontend project with React and Vite
- [ ] Finish the landing page
- [ ] Backend setup, models and migrations
- [ ] CRUD API for workspaces, projects and tasks
- [ ] Workspace, project and task screens
- [ ] Comments and activity
- [ ] Analytics endpoints and dashboard
- [ ] Authentication

## Author

Tanushri Sapate

## License

To be decided.

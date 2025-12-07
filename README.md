📊 Sales Pulse — Actionable Tableau + Salesforce + Slack Analytics Platform

Sales Pulse is a full-stack web application that transforms Tableau dashboards into an actionable workflow engine.
It embeds Tableau visualizations into a modern React web app, allows users to trigger Salesforce actions, sends automated Slack notifications, and maintains a full audit trail of all actions.

Built for hackathons and enterprise analytics use cases, Sales Pulse showcases the future of AI-powered, agentic analytics.

🚀 Features
🔹 1. Embedded Tableau Dashboards

Interactive Tableau dashboards rendered inside a React web app

Account list, account details, trends, and risk scores

Clickable marks update contextual insights and actions

🔹 2. Actionable Insights

A custom sidebar + Tableau Extension shows:

Selected Account details

AI / rule-based recommendation

Explainability for every recommendation

🔹 3. Salesforce Integration

Backend triggers:

Task creation

Case updates

Agentforce automations (if enabled)

Supports OAuth 2.0 with Salesforce.

🔹 4. Slack Integration

Automatically posts summaries to Slack channel

Includes actionable buttons & deep links

🔹 5. Complete Audit Logging

Logs all actions with:

Account ID

User ID

Action type

Reason

Notes

Payload sent

Result returned

Timestamp

🔹 6. Mock Mode for Demo

No Salesforce or Slack? No problem.
Enable DEMO_MODE=true and app simulates all actions for easy offline demos.

🔹 7. Modern Full-Stack Architecture

Frontend: React + Vite

Backend: Node.js + Express

Extensions: Tableau Extensions API

DB: SQLite (local), Postgres (production)

📁 Project Folder Structure
sales-pulse/
├── README.md
├── tableau/
│   └── workbooks/              # Published dashboards or .twbx files
├── frontend/
│   ├── index.html
│   ├── package.json
│   └── src/
│       ├── App.jsx
│       ├── main.jsx
│       ├── components/
│       │   ├── TableauEmbed.jsx
│       │   ├── Sidebar.jsx
│       │   ├── ActionModal.jsx
│       │   └── Toast.jsx
│       └── pages/
│           ├── DashboardPage.jsx
│           └── AuditPage.jsx
├── extension/
│   ├── index.html
│   ├── manifest.json
│   └── src/
│       └── ExtensionUI.jsx
├── backend/
│   ├── package.json
│   └── src/
│       ├── index.js
│       ├── db.js
│       ├── routes/
│       │   ├── action.js
│       │   ├── audit.js
│       │   └── auth.js
│       └── services/
│           ├── salesforce.js
│           ├── slack.js
│           └── agentforce.js
├── docs/
│   ├── API_LIST.md
│   ├── SETUP.md
│   └── ARCHITECTURE.png
└── .github/
    └── workflows/
        └── deploy.yml

🔧 Installation & Setup
✅ 1. Clone the repository
git clone https://github.com/<your-username>/sales-pulse.git
cd sales-pulse

🔐 Environment Variables (Frontend + Backend)

Create a .env file in frontend:

VITE_TABLEAU_URL=<your_tableau_dashboard_embed_url>
VITE_BACKEND_URL=http://localhost:4000


Create a .env file in backend:

PORT=4000
DEMO_MODE=true

# Salesforce OAuth
SF_CLIENT_ID=
SF_CLIENT_SECRET=
SF_REDIRECT_URI=http://localhost:4000/auth/salesforce/callback
SF_LOGIN_URL=https://login.salesforce.com

# Slack
SLACK_BOT_TOKEN=
SLACK_CHANNEL_ID=

# Database
DATABASE_URL=sqlite:./salespulse.db

# JWT
JWT_SECRET=supersecretkey

▶️ Running the project locally
1. Start Backend
cd backend
npm install
npm start


Backend runs on:
👉 http://localhost:4000

2. Start Frontend
cd frontend
npm install
npm run dev


Frontend runs on:
👉 http://localhost:5173

3. Running the Tableau Extension

Serve the /extension folder statically:

cd extension
npx http-server .


Then load this extension in Tableau Desktop or Tableau Cloud.

🌍 Deployment Instructions
🚀 Frontend → Deploy on Vercel

Go to https://vercel.com

Import GitHub repository

Set build command:

npm run build


Set output directory:

dist


Add frontend env variables in Vercel dashboard

🚀 Backend → Deploy on Render.com / Railway.app

Create new Web Service

Link GitHub repo

Set environment: Node.js

Start command:

npm start


Add backend environment variables

🚀 Tableau Workbooks

You may:

Upload to Tableau Cloud, OR

Store .twbx in tableau/workbooks/

🖼️ Screenshots (Add placeholders)
Dashboard Embed

![Dashboard Screenshot](docs/dashboard.png)

Sidebar with Recommendations

![Sidebar Screenshot](docs/sidebar.png)

Audit Logs

![Audit Screenshot](docs/audit.png)

📘 API Documentation
POST /api/action

Trigger an action (task creation, escalation, etc.)

Request:
{
  "user_id": "123",
  "account_id": "ACC-001",
  "action": "create_task",
  "notes": "Follow up",
  "recommendation_reason": "High churn probability"
}

Response:
{
  "status": "ok",
  "action_id": "uuid",
  "result": "Task created"
}

GET /api/audit

Returns all actions with filters.

Response:
[
  {
    "action_id": "uuid",
    "account_id": "ACC-001",
    "user_id": "123",
    "action": "create_task",
    "timestamp": "2025-01-01",
    "result": "success"
  }
]

GET /api/audit/:id

Detailed audit record.

OAuth Routes
GET /auth/salesforce

Redirects user to Salesforce login page.

GET /auth/salesforce/callback

Handles OAuth and stores tokens.

🧩 Tech Stack
Frontend

React + Vite

Axios

Tableau JS SDK

Backend

Node.js + Express

Salesforce REST API

Slack Web API

JWT Auth

Database

SQLite (dev)

Postgres (prod)

🛡️ Security

OAuth tokens are stored encrypted

Environment variables not committed to repo

All API endpoints validate JWT

Sanitized inputs & schema validation

Audit trail for every action invoked

🧪 Tests

Jest unit tests for backend routes

Integration test for POST /api/action

Smoke test for frontend build

🌟 Future Improvements

Add ML-based churn prediction model

Multi-agent workflow automation via Agentforce

Role-based UI with permissions

Slack two-way approval flows

🏁 Conclusion

Sales Pulse demonstrates a complete analytics-to-action pipeline integrating:

Tableau

Salesforce

Slack

Full-stack web technologies

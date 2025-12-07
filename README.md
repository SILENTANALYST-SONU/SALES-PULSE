🌟 # Sales Pulse — Actionable Tableau + Salesforce + Slack Platform

Sales Pulse is a full-stack analytics-to-action web application that embeds Tableau dashboards inside a modern React app and adds action buttons, Salesforce automation, Slack alerts, and complete audit logging.

It demonstrates the future of agentic, actionable analytics for enterprise teams.

⭐ ## Features
🔹 Embedded Tableau Dashboards

Completely interactive

Displays Accounts, KPIs, Risk scores, Trends

Updates context automatically when selecting a row

🔹 Actionable Insights Panel

Shows selected Account

Displays AI/rule-based recommendation

Provides explainability reasons

🔹 Salesforce Integration

Create Tasks

Update Cases

Trigger Agentforce automation

🔹 Slack Notifications

Auto-post action summaries

Deep link back to dashboard

🔹 Audit Trail

Logs every action

View audit history in Audit Page

Stores payloads, metadata, timestamps

🔹 Mock Mode

Works without Salesforce or Slack

Ideal for hackathons/demos

🗂️ ## Project Folder Structure (Vertical Tree View)
sales-pulse/
│
├── README.md
│
├── tableau/
│   └── workbooks/
│       └── <tableau-dashboard.twbx>
│
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
│
├── extension/
│   ├── index.html
│   ├── manifest.json
│   └── src/
│       └── ExtensionUI.jsx
│
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
│
├── docs/
│   ├── API_LIST.md
│   ├── SETUP.md
│   └── ARCHITECTURE.png
│
└── .github/
    └── workflows/
        └── deploy.yml

🔧 ## Installation & Setup
1️⃣ Clone the Repository
git clone https://github.com/<your-username>/sales-pulse.git
cd sales-pulse

🔐 ## Environment Variables
📌 Frontend .env
VITE_TABLEAU_URL=<your_tableau_embed_url>
VITE_BACKEND_URL=http://localhost:4000

📌 Backend .env
PORT=4000
DEMO_MODE=true

# Salesforce OAuth
SF_CLIENT_ID=
SF_CLIENT_SECRET=
SF_REDIRECT_URI=http://localhost:4000/auth/salesforce/callback

# Slack
SLACK_BOT_TOKEN=
SLACK_CHANNEL_ID=

# Database
DATABASE_URL=sqlite:./salespulse.db

# JWT Secret
JWT_SECRET=supersecret

▶️ ## Run the Application Locally
2️⃣ Start Backend
cd backend
npm install
npm start


Backend → http://localhost:4000

3️⃣ Start Frontend
cd frontend
npm install
npm run dev


Frontend → http://localhost:5173

4️⃣ Start Tableau Extension (optional)
cd extension
npx http-server .


Use URL in Tableau Desktop or Tableau Cloud Extension Manager.

🌍 ## Deployment Guide
🚀 Frontend → Vercel

Import GitHub repo

Set build command:

npm run build


Output directory:

dist


Add environment variables

Deploy 🎉

🚀 Backend → Render / Railway / Replit

Create new Web Service

Connect GitHub repo

Environment: Node.js

Start command:

npm start


Add environment variables

Deploy 🎉

🖼️ ## Screenshot Placeholders

Add your screenshots here:

Dashboard Embed
![Dashboard](docs/dashboard.png)

Action Modal
![ActionModal](docs/actionmodal.png)

Audit Logs
![Audit](docs/audit.png)

📘 ## API Documentation
🔹 POST /api/action

Trigger Salesforce/Agentforce/Slack action.

Request

{
  "user_id": "001",
  "account_id": "ACC-01",
  "action": "create_task",
  "notes": "Follow up",
  "recommendation_reason": "High churn risk"
}


Response

{
  "status": "ok",
  "action_id": "uuid",
  "result": "Task created"
}

🔹 GET /api/audit

Fetch list of all audit actions.

🔹 GET /api/audit/:id

Fetch full details for one audit entry.

🔹 OAuth Routes

/auth/salesforce

/auth/salesforce/callback

🛡️ ## Security

Secure OAuth token storage

JWT-based route protection

Validation for all inputs

No secrets committed to repo

Mock mode protects sensitive API keys

🧪 ## Test Coverage

Backend unit tests using Jest

Integration test: POST /api/action

CI test workflow via GitHub Actions

🌟 ## Future Improvements

Add ML churn prediction

Add Slack approval flows

Add RLS-aware Tableau views

Add multi-agent Agentforce orchestration

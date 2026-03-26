# Fuzebox — AI Agent Performance Dashboard

A comprehensive, real-time performance dashboard for monitoring and evaluating AI agents. Fuzebox provides full observability into agent task execution, cost economics, quality scoring, and distributed traces — all through an interactive Streamlit interface backed by OpenTelemetry instrumentation and a local SQLite database.

[Live Demo](https://fuzebox-isdv5qtatyegzefxi68o9q.streamlit.app/) · [GitHub Repository](https://github.com/rashidinvozone/Fuzebox)

---

## Getting Started

### Local Setup

```bash
git clone https://github.com/rashidinvozone/Fuzebox.git
cd Fuzebox
pip install -r requirements.txt
streamlit run dashboard_app.py
```

The dashboard will open at [http://localhost:8501](http://localhost:8501). Click **Load Demo Data** in the sidebar to populate the database with sample agents, tasks, and traces.

### Docker

```bash
docker compose up
```

This builds the image and starts the dashboard on [http://localhost:8501](http://localhost:8501). Persistent data is stored in the `./data` volume.

### Deploy to Render

1. Push this repository to your GitHub account.
2. Go to [Render](https://render.com) and create a **New Web Service**.
3. Connect your GitHub repo and select the `main` branch.
4. Render will auto-detect the `render.yaml` blueprint and configure the build and start commands.
5. Once deployed, your dashboard will be live at the URL Render assigns.

---

## Dashboard Pages

### 1. Overview

High-level KPIs at a glance — total tasks, success rate, total cost, and active agent count. Includes a cost trend chart over time, a throughput chart showing tasks completed per period, and an agent leaderboard ranked by a composite performance score.

### 2. Agent Registry

A full registry of all registered agents with their capabilities. Features a skills matrix showing each agent's declared competencies, a permissions matrix mapping access levels, and automated violation detection that flags agents operating outside their allowed scope.

### 3. Task Scorecards

Per-agent evaluation scorecards with PASS/FAIL status based on configurable quality thresholds. Includes a task type breakdown showing how each agent performs across different categories of work (code generation, analysis, summarization, etc.).

### 4. Economic Analysis

A built-in ROI calculator that compares AI agent costs against a configurable manual baseline. Displays cost breakdowns by agent and by task type, along with detailed token usage analytics (input vs. output tokens) to help optimize spending.

### 5. Performance Metrics

Deep performance analytics including latency percentile distributions (p50, p90, p99), a throughput trend chart over time, and a leaderboard ranking agents by speed, quality, and cost-efficiency using a weighted composite score.

### 6. Workflow Traces

OpenTelemetry-powered distributed tracing with a Gantt-style span timeline that visualizes the full execution flow of agent workflows. Includes a span details table with timing, status, and metadata for each operation within a trace.

---

## Tech Stack

| Component            | Technology                  |
|----------------------|-----------------------------|
| Frontend             | Streamlit                   |
| Observability        | OpenTelemetry (API + SDK)   |
| Data Validation      | Pydantic v2                 |
| Database             | SQLite                      |
| Charting             | matplotlib                  |
| Data Processing      | pandas, NumPy               |

---

## Project Structure

```
fuzebox-dashboard/
├── dashboard_app.py          # Entry point (streamlit run)
├── requirements.txt          # Python dependencies
├── verify_setup.py           # Setup verification script
├── Dockerfile                # Container build
├── docker-compose.yml        # Local container orchestration
├── render.yaml               # Render deployment blueprint
├── CONTRIBUTING.md            # Contribution guidelines
└── src/
    └── dashboard/
        ├── __init__.py
        ├── app.py            # Streamlit page layout and navigation
        ├── db.py             # SQLite database layer
        ├── economics.py      # ROI and cost analysis
        ├── evaluators.py     # Agent quality scoring and scorecards
        ├── metrics.py        # Performance metrics and leaderboard
        ├── models.py         # Pydantic data models
        └── tracing.py        # OpenTelemetry instrumentation
```

---

## License

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

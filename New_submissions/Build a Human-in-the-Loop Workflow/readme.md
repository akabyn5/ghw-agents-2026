# 🛰️ Mission Intelligence Platform — Human-in-the-Loop Workflow

**An extension of the AI Mission Decision Copilot** that adds a mandatory human-approval gate before any AI-recommended action is (safely, simulated) carried out.

The original Copilot analyzes spacecraft telemetry and proposes a decision. This extension inserts a human checkpoint between "the agent proposes" and "the system acts," so no action is ever taken automatically — a person always has the final say.

---

## 📌 Overview

This challenge asked for an agent that operates autonomously but **pauses to ask a human for explicit approval before taking a sensitive action** (e.g. sending an email, spending money, or — in this case — issuing a mission command).

Built on top of the existing platform, it keeps the original telemetry-analysis step and adds:

- A **Proposed Action** panel that clearly separates "what the AI suggests" from "what actually happens."
- A **human approval gate** (Approve / Reject) that the workflow cannot bypass.
- A **simulated executor** and a **local audit log** that record every decision, so the full loop is auditable.

No email is sent, no money moves, and no real external system is ever contacted. Every "execution" is a canned, clearly-labeled simulation — by design, per the challenge's constraints.

---

## 🏗 Architecture

```
Agent (telemetry input)
        ↓
Analysis (LLM-based classification via Backboard)
        ↓
Proposed Action  ──────────────────────────────┐
        ↓                                       │
┌──────────────────────────┐                    │
│ HUMAN APPROVAL REQUIRED   │  ← workflow pauses here
│                           │
│   Approve   /   Reject    │
└────────────┬──────────────┘
             ↓
   Execute action (simulated)
             ↓
      Decision Log (audit trail)
```

```
Frontend (HTML + JS)
        ↓
Flask Backend
        ├── POST /analyze   → Agent + Analysis + Proposed Action
        ├── POST /decision  → Human Approval gate + simulated execution
        └── GET  /history   → Audit trail of every past decision
```

---

## 🧠 How It Works

1. The user selects a telemetry scenario in the frontend (thermal, power, or communications anomaly).
2. The frontend sends the telemetry to `POST /analyze`. The backend builds a prompt from `docs/prompt.txt`, sends it to an LLM through [Backboard](https://backboard.io) (a unified AI gateway), and validates the JSON it gets back. The result — `classification`, `severity`, `recommended_action`, `reasoning` — is the agent's **proposal**, nothing more. If Backboard is unreachable, misconfigured, or returns something invalid, the endpoint falls back to a fixed `FALLBACK_RESPONSE` instead of failing.
3. The UI displays the proposal inside a clearly marked **"⚠ Human Approval Required"** panel. The workflow stops here; nothing is executed yet.
4. The human clicks **Approve** or **Reject**.
   - The frontend sends that decision to `POST /decision`.
   - On **Approve**, the backend runs `simulate_action_execution()`, which returns a descriptive, obviously-simulated confirmation message (no real system is touched).
   - On **Reject**, the backend records the rejection and nothing is "executed."
5. Every decision — approved or rejected — is appended to a local JSON audit log (`backend/logs/decision_log.json`) and shown in the **Decision Log** panel via `GET /history`.

---

## 📁 Repository Structure

```
mission-hitl-workflow/
├── backend/
│   ├── app.py                 # Flask backend: /analyze, /decision, /history
│   ├── requirements.txt
│   ├── .env                   # Your Backboard API key (not committed)
│   ├── test_scenarios.json    # Sample telemetry payloads
│   └── logs/
│       └── decision_log.json  # Simulated audit log (created at runtime)
├── docs/
│   ├── prompt.txt             # Prompt used for the analysis step
│   ├── input_schema.json      # /analyze request shape
│   └── output_schema.json     # /analyze response shape
├── frontend/
│   └── index.html             # UI: scenario picker, analysis, approval panel, audit log
└── README.md
```

---

## ⚙️ Setup Instructions

### 1. Enter the backend folder

```bash
cd mission-hitl-workflow/backend
```

### 2. Create and activate a virtual environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

> This project calls its LLM through **Backboard**, using plain HTTP (`requests`) rather than a provider SDK. If your `requirements.txt` still lists `google-genai` from an earlier version, it's a harmless leftover — it's not imported anywhere and can be removed. The dependencies actually used are: `flask`, `flask-cors`, `python-dotenv`, `requests`.

### 4. Configure your Backboard API key

Create a `.env` file inside `/backend`:

```env
BACKBOARD_API_KEY=your_backboard_api_key_here

# Optional — these already default to "openai" / "gpt-4o-mini" in app.py
# BACKBOARD_LLM_PROVIDER=openai
# BACKBOARD_MODEL_NAME=gpt-4o-mini
```

> You can also run the whole demo **without** a key. If `BACKBOARD_API_KEY` is missing, `/analyze` prints a warning at startup and gracefully falls back to `FALLBACK_RESPONSE` instead of crashing. The human-approval workflow (`/decision`, `/history`) works identically either way, since it never depends on the AI call.

### 5. Run the backend server

```bash
python app.py
```

The server prints whether your key loaded, then runs at: `http://127.0.0.1:5000`

### 6. Open the app

Open your browser at `http://127.0.0.1:5000` (the backend also serves the frontend).

---

## 🎮 Demo Flow

1. Select a scenario: **Thermal Anomaly**, **Energy Anomaly**, or **Communication Loss**.
2. Click **Analyze** → the agent returns a classification, severity, and a **recommended action**.
3. The **Proposed Action** panel appears with the recommended action and two buttons: **✅ Approve** / **❌ Reject**. Nothing happens until you click one.
4. Click **Approve** → the backend logs the decision and returns a simulated confirmation (e.g. *"[SIMULATED] Action recorded for subsystem 'thermal': 'reduce load and activate cooling'. No external system was contacted, no email was sent, and no funds were spent."*).
   Click **Reject** instead → the backend logs the rejection and confirms *"Action rejected by human operator. No execution performed."*
5. The **Decision Log** panel refreshes automatically, showing the full audit trail of every decision made so far (executed or rejected), pulled from `GET /history`.

---

## 🔌 API Reference

### `POST /analyze`
Request:
```json
{
  "subsystem": "thermal",
  "metric": "temperature_core",
  "value": 85,
  "mission_phase": "nominal",
  "timestamp": "2026-04-17T12:30:00Z"
}
```
Response:
```json
{
  "classification": "thermal degradation",
  "severity": "high",
  "recommended_action": "reduce load and activate cooling",
  "reasoning": "Temperature exceeds nominal threshold while efficiency is decreasing"
}
```

### `POST /decision`
Request (the frontend sends the analysis fields flat, alongside `decision`):
```json
{
  "subsystem": "thermal",
  "classification": "thermal degradation",
  "severity": "high",
  "recommended_action": "reduce load and activate cooling",
  "reasoning": "Temperature exceeds nominal threshold while efficiency is decreasing",
  "decision": "approve"
}
```
Response:
```json
{
  "status": "executed",
  "system_response": "[SIMULATED] Action recorded for subsystem 'unknown': 'reduce load and activate cooling'. No external system was contacted, no email was sent, and no funds were spent.",
  "decision": "approve",
  "execution_result": "[SIMULATED] Action recorded for subsystem 'unknown': ...",
  "log_entry_id": "388e029c-..."
}
```
`decision` must be `"approve"` or `"reject"`; anything else returns `400`. `status` is `"executed"` or `"rejected"`.

### `GET /history`
Returns a flat array (most recent first), one object per past decision:
```json
[
  {
    "status": "executed",
    "subsystem": "unknown",
    "recommended_action": "reduce load and activate cooling",
    "timestamp": "2026-08-11T20:00:00+00:00",
    "system_response": "[SIMULATED] Action recorded for subsystem 'unknown': ..."
  }
]
```

---

## 🛡 Safety Design

This is the core requirement of the challenge, so it's worth stating explicitly:

- **No email is ever sent.** No SMTP, no third-party mail API.
- **No money is ever spent.** No payment or budget API is called.
- **No real external system is ever modified.** `simulate_action_execution()` only builds and returns a descriptive string.
- The only side effect of an approved action is a new entry in the local JSON audit log — nothing leaves the machine running the demo.

If you want to turn this into a system that performs real actions, the natural extension point is `simulate_action_execution()` in `backend/app.py` — but that step is intentionally out of scope here.

---

## ⚠️ Known Limitations

- **Subsystem shows as "unknown" in the audit log for decisions made through the browser.** The frontend sends `subsystem` as a flat field on `/decision`, but the backend currently only reads it from a nested `telemetry.subsystem` field. The decision itself is recorded correctly (action, severity, approve/reject, timestamp) — only the displayed subsystem label is affected. Fixable by also reading `body.get("subsystem")` directly in the `/decision` route.
- No real-time telemetry stream (scenarios are pre-defined test payloads).
- The audit log is a local JSON file, not a database — fine for a demo, not for production.
- No user authentication — anyone with access to the running instance can approve or reject.
- No confidence scoring on the AI's classification.

## 🔮 Possible Future Improvements

- Fix the subsystem-labeling limitation above.
- Real telemetry integration.
- Persist the audit log in a proper database.
- Role-based approval (e.g., only certain operators can approve `critical` severity actions).
- Notifications (Slack/email) when an action is awaiting approval — itself gated the same way, or genuinely wired up if that becomes in-scope.

---

## 📄 License

MIT License.

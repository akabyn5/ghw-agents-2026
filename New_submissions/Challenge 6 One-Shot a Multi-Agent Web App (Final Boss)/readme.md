# Challenge 6: One-Shot a Multi-Agent Web App (Final Boss) – Completed ✅

## 🎉 Team Challenge Summary

**Challenge Completed: One-Shot a Multi-Agent Web App!** ✅  
**Team:** Space Dogs  
**Event:** Global Hack Week: Agents | Backboard.io  
**Final Boss Status:** Conquered  

We one-shotted a complete multi-agent web application.  
A single detailed prompt was given to R-CLI / Backboard Studio. The agent built the entire FastAPI backend, multi-agent orchestration, frontend interface, and supporting files — then validated the system. Multiple specialist agents with different jobs collaborate to produce a professional mission recommendation that none of them would produce alone.

---

## 📋 Challenge Overview

- **Challenge Name:** Challenge 6 – One-Shot a Multi-Agent Web App (Final Boss)  
- **Difficulty:** Hard  
- **Status:** Successfully Completed ✅  
- **Date Completed:** August 11, 2026  
- **Project Name:** ARPIP Mission Intelligence Platform  
- **Repository:** [https://github.com/akabyn5/ghw-agents-challenge-6](https://github.com/akabyn5/ghw-agents-challenge-6.git)

### What We Built
A full web application where **four specialist Backboard agents** work together on space / Earth-observation mission analysis:

1. **ARPIP Research Agent** – Gathers evidence and source constraints  
2. **ARPIP Earth Observation Agent** – Translates findings into candidate observations, products, and datasets  
3. **ARPIP Engineering Agent** – Converts research into architecture, operations, communications, compute, and risk considerations  
4. **ARPIP Review Agent** – Challenges unsupported claims, highlights evidence gaps, contradictions, and corrections  

The final output is a structured **Mission Recommendation** that incorporates the work of all four agents.

---

## 🛠️ Architecture

**Pipeline flow:**
Mission Request → Research → Earth Observation → Engineering → Review → Final Recommendation
text**Tech stack:**
- Python + FastAPI backend
- Backboard SDK (`backboard-sdk`)
- Multiple specialized assistants (persisted in `agents.json`)
- Simple modern dark-themed frontend
- Environment variable for `BACKBOARD_API_KEY` (never hardcoded)

**Key endpoints validated:**
- `/`
- `/api/status`
- `/api/config`

---

## 📸 Proof of Completion

### 1. Build & Validation Success
![Terminal – Smoke Tests Passed](powershell-backboardio.jpeg)

All validation todos completed:
- Workspace inspected  
- Multi-agent web app prototype implemented  
- Practical checks passed  

### 2. Live Web Interface
![ARPIP Mission Intelligence Platform](ARPIP-Mission-Intelligence-Platform.jpeg)

### 3. Multi-Agent Dashboard (Waiting State)
![Agent Cards – Ready](Demo.jpeg)

### 4. Agents Completed
![Agents Completed Status](Status.jpeg)

### 5. Final Mission Recommendation
![Final Mission Recommendation Output](Results-readme.jpeg)

The recommendation includes:
- Clear go/no-go framing  
- Multi-agent basis (contribution of each specialist)  
- Implementation guidance  
- Review gate requirements  

---

## 🔑 Multi-Agent Design

| Agent                        | Role                                      |
|-----------------------------|-------------------------------------------|
| ARPIP Research Agent        | Evidence base & source gathering          |
| ARPIP Earth Observation Agent | Dataset / product relevance               |
| ARPIP Engineering Agent     | Architecture, ops, constraints, risks     |
| ARPIP Review Agent          | Critique, gaps, corrections, confidence   |

Each agent has its own system prompt and runs in its own thread. The application code acts as the coordinator that sequences their work and surfaces every contribution to the user.

---

## 🚀 How to Run

```bash
# Install dependencies
python -m pip install -r requirements.txt

# Set your API key (PowerShell example)
$env:BACKBOARD_API_KEY = "your_key_here"

# Start the server
python -m uvicorn app.main:app --reload
Open: http://127.0.0.1:8000

📂 Project Structure (Key Files)
textghw-agents-challenge-6/
├── app/                  ← FastAPI application
├── agents.json           ← Persisted assistant IDs
├── mission_config.json
├── requirements.txt
├── demo.py
├── smoke_test.py
├── .env.example
└── README.md

🔗 Full Journey – Challenges 1 → 6

Challenge 1 – Backboard account + promo credits
Challenge 2 – Dashboard walkthrough + Nash + memory
Challenge 3 – R-CLI installation + first agent task
Challenge 4 – Basic stateful agent (ARPIP Mission Assistant)
Challenge 5 – One-shot agentic research workflow
Challenge 6 – One-shot multi-agent web application ← Final Boss

We went from “sign up for an account” to a working multi-agent mission intelligence platform in one week.

💡 Key Takeaways

Multi-agent systems shine when each agent has a sharp, specialized job.
A review agent that is allowed to challenge the others dramatically improves output quality.
One-shot prompting at this scale forces architectural thinking up front.
Backboard’s assistants + threads + memory make multi-agent orchestration practical.


Completed by: Space Dogs Team (José)
Date: August 11, 2026
Callsign: SpaceDog-01
Repository: https://github.com/akabyn5/ghw-agents-challenge-6

Final Boss defeated. Multi-agent web app delivered. 🚀🛰️🤖
text---

This README celebrates the successful one-shot completion of Challenge 6, accurately reflects the ARPIP Mission Intelligence Platform visible in your screenshots, and ties the entire Global Hack Week: Agents journey together.
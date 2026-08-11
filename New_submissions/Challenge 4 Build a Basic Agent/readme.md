# Challenge 4: Build a Basic Agent – Completed ✅

## 🎉 Team Challenge Summary

**Challenge Completed: Build a Basic Agent!** ✅  
**Team:** Space Dogs  
**Event:** Global Hack Week: Agents | Backboard.io  

We successfully directed R-CLI to build a real, stateful command-line chatbot that talks to the Backboard API, reuses the same assistant across runs, and remembers facts about us. Memory is what turns a simple chatbot into a true agent — and our memory test passed.

---

## 📋 Challenge Overview

- **Challenge Name:** Challenge 4 – Build a Basic Agent  
- **Event:** Global Hack Week: Agents  
- **Difficulty:** Medium  
- **Time Needed:** ~15 minutes  
- **Status:** Successfully Completed ✅  
- **Date Completed:** August 11, 2026  
- **Project Folder:** `ghw-agents-challenge-4`  
- **Agent Name:** ARPIP Mission Assistant  

### What We Built
A minimal Python CLI chatbot powered by the Backboard API that:
- Uses the official `backboard-sdk`
- Reads the API key from the `BACKBOARD_API_KEY` environment variable (never hardcoded)
- Creates an assistant once and reuses the same `assistant_id` across runs (saved locally)
- Starts a **fresh thread** on every execution
- Sends every message with `memory="Auto"` so facts are automatically saved and recalled
- Remembers context about the user and the Space Dogs / ARPIP project between restarts

---

## 🛠️ How We Built It

1. Created the project folder:
   ```powershell
   mkdir ghw-agents-challenge-4
   cd ghw-agents-challenge-4

Started R-CLI and directed it with a clear, numbered prompt describing the exact requirements.
The build agent:
Inspected the workspace
Implemented the chatbot with assistant persistence
Created supporting files (requirements.txt, README.md, etc.)
Handled Windows-specific considerations (PowerShell, no WSL required for this minimal version)

Ran the chatbot, shared personal and project facts, quit, restarted it, and confirmed memory worked.


📸 Proof of Completion – Memory Test
Memory Recall Across Restarts
<img src="memory-save.jpeg" alt="Memory Test Success">
When asked
“What do you remember about me and what I am working on?”
The agent correctly recalled:

Name: José
Team: Space Dogs
Project: ARPIP (Advanced Research Projects and International Programs)
Challenge context: Global Hack Week – Agent Week, Challenge 4 on Windows
Chatbot name: ARPIP Mission Assistant
Key technical requirements (assistant persistence, new thread per run, memory="Auto", callsign SpaceDog-01, etc.)

Build Process in Progress
<img src="processing.jpeg" alt="Agent Working on the Chatbot">
Project Setup
<img src="Power-Shell-Windows-Installation-challenge-4.jpeg" alt="Project Folder Creation">

🔑 Core Concepts Demonstrated

























ConceptHow We Used ItAssistantCreated once, ID saved and reusedThreadFresh thread on every program runMessageUser ↔ agent turns in the chat loopMemorymemory="Auto" so facts persist across sessions
This is the exact architecture that makes Backboard agents stateful instead of “goldfish” chatbots.

📂 Project Structure
textghw-agents-challenge-4/
├── chatbot.py (or equivalent)
├── arpip_assistant.json          ← saved assistant_id
├── requirements.txt
├── README.md
├── .gitignore
└── (supporting files)

🔗 Connection to Previous Challenges
This challenge sits on top of everything we completed earlier:

Challenge 1: Backboard account + GLOBALMLH2 promo credits
Challenge 2: Dashboard walkthrough + memory & Nash exploration
Challenge 3: R-CLI installation + first agent walkthrough (hello.py)

We are now building agents with agents.

💡 Key Takeaways

Clear, numbered, outcome-focused prompts produce much better results from the build agent.
Reusing the same assistant_id is the critical piece that makes memory work across runs.
Directing an AI to write the code is a real skill — the better the description, the better the agent.
We now have a working, stateful CLI agent ready for more advanced workflows in Challenges 5 and 6.


Completed by: Space Dogs Team (José)
Date: August 11, 2026
Callsign: SpaceDog-01

Basic agent built. Memory confirmed. Ready for multi-step agentic workflows! 🚀🤖
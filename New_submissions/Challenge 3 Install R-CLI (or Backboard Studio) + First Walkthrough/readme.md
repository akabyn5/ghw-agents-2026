# Challenge 3: Install R-CLI (or Backboard Studio) + First Walkthrough – Completed ✅

## 🎉 Team Challenge Summary

**Challenge Completed: Install R-CLI + First Walkthrough!** ✅  
**Team:** Space Dogs  
**Event:** Global Hack Week: Agents | Backboard.io  

We successfully installed the **Backboard R-CLI** (the recursive AI coding agent that lives in the terminal), verified the installation, logged in, and completed the first hands-on walkthrough. R-CLI is now ready to power Challenges 4, 5, and 6 — where we will describe what we want in plain English and let the agent build it.

---

## 📋 Challenge Overview

- **Challenge Name:** Challenge 3 – Install R-CLI (or Backboard Studio) + First Walkthrough  
- **Event:** Global Hack Week: Agents  
- **Difficulty:** Medium  
- **Time Needed:** ~15 minutes  
- **Status:** Successfully Completed ✅  
- **Date Completed:** August 10, 2026  
- **Tool Installed:** Backboard R-CLI v1.3.14.0  

### Why This Matters
R-CLI is Backboard’s terminal-based AI coding agent. It plans, writes code, runs it, fixes its own errors, and returns results. It uses a recursive design (breaking work into focused child agents) and scored **84.3% on Terminal Bench 2.1** — the highest publicly reported score. For the rest of Agent Week we will describe features in plain English and let R-CLI build them.

---

## 🛠️ What We Completed

### Step 1: Installed R-CLI
```bash
curl -fsSL https://app.backboard.io/api/cli | bash
Step 2: Verified Installation
Bashbackboard --version
Result: Version 1.3.14.0 confirmed.
Also confirmed location:
Bashwhere.exe backboard
# C:\Users\josep\.backboard\bin\backboard.exe
Step 3: Logged In
Bashbackboard login
Authenticated with our Backboard account (from Challenge 1).
Step 4: First Session Walkthrough
Started the interactive agent:
Bashbackboard
Gave it the required first task:
Create a file called hello.py that prints a random programming joke. Then run it and show me the output.
What the agent did:

Created hello.py with a list of programming jokes
Ran the script successfully
Displayed a random joke as output

Joke received:
Why did the developer go broke? Because they used up all their cache.

📸 Proof of Completion
1. R-CLI Version Confirmation
<img src="version-backboard-io.jpeg" alt="Backboard CLI Version">
2. First Agent Task – hello.py Created & Executed
<img src="hello-py.jpeg" alt="hello.py Task Completed">
The agent:

Wrote the file
Executed python hello.py
Returned a successful random programming joke


🔧 Key Capabilities Unlocked

✅ R-CLI installed and verified
✅ Authenticated with Backboard account
✅ Agent can create files, run commands, and self-correct
✅ Ready for multi-file agent work in Challenges 4–6
✅ Access to models, thinking modes, skills, and MCP tools

Useful flags for future sessions:
Bashbackboard --model openai/gpt-5.5
backboard --thinking high
backboard --memory on
backboard --print "your prompt"

🔗 Connection to Previous Challenges
This installation builds directly on:

Challenge 1: Sign Up for Backboard + Claim Promo Code (GLOBALMLH2)
Challenge 2: Dashboard Walkthrough + Nash Demo (memory & model exploration)

We now have the full toolkit: account + credits + memory + terminal agent.

💡 Key Takeaways

R-CLI turns plain-English instructions into working code with a write → run → fix loop.
The recursive design keeps context focused and reliable.
Having the CLI ready means the rest of Agent Week can be agent-driven instead of hand-coded.
The same engine powers both R-CLI and Backboard Studio — either path is valid.


Completed by: Space Dogs Team (José)
Date: August 10, 2026

R-CLI installed. First agent task complete. Ready to build! 🚀🤖
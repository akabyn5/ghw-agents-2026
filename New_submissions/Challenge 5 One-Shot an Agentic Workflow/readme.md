# Challenge 5: One-Shot an Agentic Workflow – Completed ✅

## 🎉 Team Challenge Summary

**Challenge Completed: One-Shot an Agentic Workflow!** ✅  
**Team:** Space Dogs  
**Event:** Global Hack Week: Agents | Backboard.io  

We successfully one-shot a complete agentic research workflow.  
A single, carefully engineered prompt was given to R-CLI. The agent built the entire pipeline, installed dependencies, executed all stages, generated a professional Markdown research report, and demonstrated that everything worked — with no follow-up instructions required.

---

## 📋 Challenge Overview

- **Challenge Name:** Challenge 5 – One-Shot an Agentic Workflow  
- **Event:** Global Hack Week: Agents  
- **Difficulty:** Medium (the hard part is writing the prompt)  
- **Status:** Successfully Completed ✅  
- **Date Completed:** August 11, 2026  
- **Workflow Name:** ARPIP Research Intelligence Pipeline  
- **Assistant Name:** ARPIP Research Intelligence Assistant  

### What “One-Shot” Means
One prompt → complete working system.  
No iterative fixing. No follow-up instructions.  
If something was wrong, we improved the prompt and re-fired from a clean session.

---

## 🛠️ What We Built

A minimal Python command-line research workflow that:

1. Accepts a research topic as a command-line argument  
2. Creates (and reuses) a single Backboard assistant  
3. Starts a fresh thread on every run  
4. Executes **three distinct AI-powered stages** inside that thread  
5. Produces a finished Markdown research report  

**Command:**
```bash
python research.py "research topic"
Demonstration topic used:
Bashpython research.py "AI for satellite mission operations"
Expected output file:
textresearch-ai-for-satellite-mission-operations.md

🔄 The Three Agentic Stages

























StageNameWhat Happens1Research / GatherWeb search (web_search="Auto") → at least 5 sourced findings2Technical AnalysisExactly 3 major technical insights with maturity, limitations & ARPIP relevance3Report WritingFull professional Markdown report (Executive Summary → Sources)
All stages run in one shared thread so context flows naturally from research → analysis → final report.

📸 Proof of Completion

One-shot prompt successfully executed by R-CLI
All three stages completed with progress indicators:text[1/3] Researching...
[2/3] Performing technical analysis...
[3/3] Writing report...
[Done] Report saved to: research-ai-for-satellite-mission-operations.md
Final Markdown report generated with proper structure and sources
arpip_research_assistant.json created and reused
requirements.txt and project README.md generated
API key never exposed

(Screenshots of the running pipeline and finished report can be attached here)

🔑 Key Design Decisions (from the one-shot prompt)

Exactly one assistant → "ARPIP Research Intelligence Assistant"
Assistant ID persisted to arpip_research_assistant.json and reused
New thread on every execution
All stages share the same thread (context continuity)
Strict quality rules: no fabricated facts or sources
Clear definition of done (10 verification points)
Minimal stack: Python + backboard-sdk only


📂 Project Structure
textworkflow-challenge/   (or ghw-agents-challenge-5)
├── research.py
├── arpip_research_assistant.json
├── research-ai-for-satellite-mission-operations.md
├── requirements.txt
└── README.md

🧠 Why This Prompt Worked
The one-shot prompt included:

Clear goal in the first sentence
Exact technology constraints
Numbered stages with explicit Backboard features
Quality bars (word count, required sections, source rules)
Input/output contract
Progress indicators
Error handling rules
A strict “definition of done”

This is the skill Challenge 5 is designed to teach.

🔗 Connection to Previous Challenges

Challenge 1 → Account + credits
Challenge 2 → Dashboard & memory understanding
Challenge 3 → R-CLI installed
Challenge 4 → Basic stateful agent (ARPIP Mission Assistant)

Challenge 5 upgraded us from a simple agent to a multi-step agentic workflow.

💡 Key Takeaways

The quality of the prompt is the quality of the system.
Forcing everything into one shot makes you think like an architect.
Reusing the same assistant + one shared thread is the reliable way to keep context.
We now have a reusable research pipeline tailored to Space Dogs / ARPIP needs.


Completed by: Space Dogs Team (José)
Date: August 11, 2026
Callsign: SpaceDog-01

One prompt. Full pipeline. Research report delivered. 🚀📄🤖
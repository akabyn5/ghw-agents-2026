This project is a Human-in-the-Loop (HITL) workflow, built as an extension of the Mission Intelligence Platform (AI Mission Decision Copilot). It demonstrates how an autonomous AI agent can analyze data and propose an action while still requiring explicit human approval before anything is actually executed.

Given spacecraft telemetry (thermal, power, or communications readings), a Flask backend sends the data to an LLM through Backboard, a unified AI gateway, which classifies the anomaly, assigns a severity level, and recommends an action. That recommendation is never carried out automatically — it is shown to a human operator in a dedicated approval panel, who must explicitly click Approve or Reject before anything happens.

If approved, the system runs a simulated executor that logs a clearly-labeled synthetic response — no real email is sent, no money is spent, and no external system is ever contacted, per the project's safety constraints. If rejected, the rejection is simply recorded. Every decision, approved or rejected, is written to a local audit log and displayed in a Decision Log panel, giving a transparent history of everything a human has reviewed.

The result is a complete, working demonstration of the human-in-the-loop pattern: Agent → Analysis → Proposed Action → Human Approval → (simulated) Execution → Audit Trail.

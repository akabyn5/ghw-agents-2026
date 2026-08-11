Challenge 5: One-Shot an Agentic Workflow
Challenge 5 was a medium-difficulty task that required us to shift from writing code to practicing advanced prompt engineering. The core objective centered on the "one-shot" methodology: writing a single, highly detailed prompt that instructed our build agent (R-CLI or Backboard Studio) to generate an entire working application without any subsequent corrections, debugging, or follow-up instructions.

We were required to design an "agentic workflow," which meant the AI had to execute a multi-step job in sequence—gathering data, making decisions, and producing a final deliverable—rather than simply answering a single query. The baseline requirement was to build a workflow that took an input, ran at least three distinct AI-powered steps, and output a finished file, all executable via a single terminal command.

Our Team's Execution: ARPIP Research Intelligence Pipeline
For our submission, we architected a comprehensive prompt to build the "ARPIP Research Intelligence Pipeline." This was a minimal Python command-line research tool tailored specifically for our technical focus areas at Space Dogs — ARPIP.

Our prompt strictly defined the application's architecture, dependencies, and error handling, ensuring no unnecessary infrastructure (like React or FastAPI) was included. We instructed the agent to build a pipeline that executed the following three stages:

Stage 1 (Research / Gather): The application utilized Backboard's web search capability to identify five important, recent findings on a provided space technology topic, explicitly prioritizing authoritative sources like NASA and ESA.

Stage 2 (Technical Analysis): The AI processed the gathered data to identify exactly three major technical insights, assessing technological maturity, limitations, and direct relevance to our work at ARPIP.

Stage 3 (Report Writing): The agent compiled the research and analysis into a professional Markdown report, complete with an executive summary and a verified sources list.

As evidenced by our prompt.jpeg and terminal.jpeg files, our execution was completely successful. The build agent autonomously processed our one-shot prompt, implemented the codebase, and ran the mandatory demonstration for the topic "AI for satellite mission operations." The terminal output confirmed that all three AI stages executed seamlessly, the assistant profile was correctly persisted and reused, and the final research-ai-for-satellite-mission-operations.md report was safely generated without exposing any API keys in our workspace.
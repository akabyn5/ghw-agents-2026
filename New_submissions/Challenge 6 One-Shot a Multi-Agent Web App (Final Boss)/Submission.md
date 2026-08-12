Challenge 6: One-Shot a Multi-Agent Web App
We completed Challenge 6, known as the "Final Boss" of Global Hack Week: Agent Week. The core objective was to write a single prompt to generate a functional web application where multiple AI agents collaborated to achieve a complex task. Instead of relying on a single AI, we were required to implement a multi-agent architecture featuring a team of AI specialists.

Our application had to meet several strict requirements:

We needed to create at least three assistants, each with a unique system prompt defining their specific job.

We had to establish a true relay workflow where the output of one agent served as the input for the next.

We were required to build a web interface to handle inputs and display results.

The user interface needed to visibly demonstrate the teamwork by showing the individual contributions of each agent.

Our Execution: ARPIP Mission Intelligence Platform
For our submission, we successfully engineered the ARPIP Mission Intelligence Platform. This application served as a Backboard-powered multi-agent prototype dedicated to technical space and Earth-observation mission analysis. We built the backend using FastAPI and ran the server locally using uvicorn.

Our multi-agent relay race followed a strict sequential workflow: Mission Request → Research → Earth Observation → Engineering → Review → Recommendation.

To process our mission requests, we developed four distinct AI specialists:

ARPIP Research Agent: This agent was responsible for supplying the foundational evidence base and source-gathering constraints.

ARPIP Earth Observation Agent: This specialist translated the research findings into relevant Earth-observation datasets and candidate products.

ARPIP Engineering Agent: This agent took the previous outputs and converted them into concrete architecture, operations, communications, compute, and risk considerations.

ARPIP Review Agent: Acting as our critical editor, this agent reviewed the workflow to challenge unsupported claims and highlight confidence levels, evidence gaps, and corrections.

To prove our workflow was successful, we ran a demonstration requesting a design for a rapid-response CubeSat and ground-analysis concept to monitor wildfire smoke transport. The application successfully executed the multi-agent analysis, updating the status of each agent to "COMPLETED" and generating a final, phased mission recommendation that synthesized the contributions of all four agents.
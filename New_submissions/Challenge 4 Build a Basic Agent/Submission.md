Challenge 4: Build a Basic Agent
This is a medium-difficulty challenge for Global Hack Week: Agent Week. The primary objective is to transition from writing code manually to practicing prompt engineering. Participants use their existing R-CLI or Backboard Studio build agent to autonomously write, debug, and execute the code for a brand-new, stateful command-line chatbot built on the Backboard API.

Core Objectives of the Challenge:

API Integration: Securely utilize the official backboard-sdk for Python and authenticate using an environment variable (BACKBOARD_API_KEY) to prevent hardcoding secrets.

Architecture & Persistence: Understand and implement Backboard's core architecture layers:

Assistant: Create a named agent profile and save its unique assistant_id to a local file (e.g., JSON) so the same profile is reused across multiple runs.

Thread & Message: Ensure each execution of the script starts a fresh conversation thread, but retains the core Assistant profile.

Memory Management: Send all chat messages with memory="Auto". The ultimate test of completion is verifying that the newly built chatbot can remember facts about the user across completely different sessions (after quitting and restarting the application).

Team Space Dogs' Execution
Our provided screenshots confirm that our team successfully directed the build agent to meet and exceed the criteria for this challenge:

Environment Setup: The Power Shell Windows Installation challenge 4.jpeg file shows the successful creation and navigation into our dedicated project workspace (ghw-agents-challenge-4) using the Windows command line.

Agent Planning & Scaffolding: In processing.jpeg, the Backboard Studio interface displays the build agent successfully interpreting our prompt. The agent generated a clear "Todos" list, which included implementing the minimal Python CLI chatbot, persisting the assistant, handling the dependencies (requirements.txt), and verifying communication.

The Memory Test (Success): The memory save.jpeg file proves the chatbot is fully functional and stateful. Upon restarting the application and querying the chatbot's memory, it successfully recalled highly specific, cross-session details, including:

Our name (José) and organization (Space Dogs - ARPIP).

The specific name of the bot being built ("ARPIP Mission Assistant").

Our broader project goals (Mission Control Ground Segment Platform) and specific technical preferences (keeping the infrastructure minimal, avoiding WSL, using PowerShell/Python).

The successful implementation of saving the assistant_id to arpipp_assistant.json and utilizing memory='Auto'.
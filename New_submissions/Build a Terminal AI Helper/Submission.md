Challenge: Build a Terminal AI Helper
We completed the "Build a Terminal AI Helper" challenge, where the primary objective was to engineer a command-line agent that translated plain English instructions into executable terminal commands. A strict requirement for this challenge was implementing a safety mechanism where the agent asked for explicit user confirmation before running any generated commands.

Our Team's Execution
We maintained our project codebase in our arpip-terminal-assistant GitHub repository. To power our terminal assistant locally, we utilized Ollama.

Working within our Space Dogs International Projects workspace, we executed the following steps:

Environment Setup: We installed Ollama via PowerShell and successfully pulled the llama3 model to serve as the local inference engine for interpreting plain English requests.

Safety Implementation: We executed our main application script, terminal_assistant.py. Our application successfully featured a built-in safety validation check, ensuring that generated commands passed a "restricted read-only allowlist" before proceeding.

Command Generation and Execution: During our testing phase, the agent successfully proposed a command (find . -type f -name '*.py' -size +5242880c) and prompted us with Execute this command? [YES/NO]. After we confirmed by typing YES, the application attempted execution. While the specific command returned a parameter format error (FIND: formato de parámetros incorrecto), it successfully demonstrated our complete, functional interaction loop from English translation to user confirmation and final execution attempt.
# ARPIP Mission Assistant CLI

A minimal command-line chatbot for Global Hack Week: Agent Week, Challenge 4. It uses the official `backboard-sdk` Python package and reads the API key only from the `BACKBOARD_API_KEY` environment variable.

On first run, the app creates one Backboard assistant named `ARPIP Mission Assistant` and saves its `assistant_id` in `arpipp_assistant.json`. Later runs reuse that assistant and create a new thread for each program execution.

## Install dependencies

From this project directory in Windows PowerShell:

```powershell
python -m pip install -r requirements.txt
```

## Set BACKBOARD_API_KEY in Windows PowerShell

For the current PowerShell session only:

```powershell
$env:BACKBOARD_API_KEY = "your-backboard-api-key"
```

For future PowerShell sessions:

```powershell
[Environment]::SetEnvironmentVariable("BACKBOARD_API_KEY", "your-backboard-api-key", "User")
```

After setting it permanently, open a new PowerShell window before running the chatbot.

Do not paste your real API key into source files, screenshots, or terminal output you plan to share.

## Run the chatbot

```powershell
python chatbot.py
```

Type messages at the `You:` prompt. Type `quit` to exit.

The app prints the reused `assistant_id` and the newly created `thread_id` at startup. The `assistant_id` should stay the same across runs; the `thread_id` should change on each run.

## Final memory test

Run this test from Windows PowerShell after `BACKBOARD_API_KEY` is set.

First execution, teach the assistant a fact:

```powershell
python chatbot.py
```

At the prompt, enter:

```text
Remember that my ARPIP test callsign is Nova-K9.
quit
```

Second execution, start a new thread and ask for the fact:

```powershell
python chatbot.py
```

At the prompt, enter:

```text
What is my ARPIP test callsign?
quit
```

Expected result:

- The `assistant_id` printed at startup is the same in both executions.
- The `thread_id` printed at startup is different in each execution.
- The assistant recalls `Nova-K9`, demonstrating memory across separate executions with the same assistant.

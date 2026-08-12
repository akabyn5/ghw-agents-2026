# ARPIP Research Intelligence Pipeline

This project is a minimal Python command-line research workflow for Space Dogs — ARPIP (Advanced Research Projects and International Programs). It uses Backboard to run a three-stage AI research workflow and writes a finished Markdown research report for a supplied technical topic.

## Prerequisites

- Python 3.7 or newer
- A Backboard account and API key
- The `BACKBOARD_API_KEY` environment variable set before execution

The API key is read only from the environment. Do not hardcode it in project files.

## Installation

```powershell
pip install -r requirements.txt
```

## Set `BACKBOARD_API_KEY` in Windows PowerShell

For the current PowerShell session:

```powershell
$env:BACKBOARD_API_KEY = "your-backboard-api-key"
```

To persist it for future PowerShell sessions:

```powershell
[Environment]::SetEnvironmentVariable("BACKBOARD_API_KEY", "your-backboard-api-key", "User")
```

Open a new PowerShell window after setting a persistent user environment variable.

## Execute the Workflow

Run the CLI with a quoted research topic:

```powershell
python research.py "AI for satellite mission operations"
```

If no topic is supplied, the program prints usage instructions and exits.

## Output Location

Reports are written to the project directory as:

```text
research-<topic-slug>.md
```

For example:

```text
research-ai-for-satellite-mission-operations.md
```

The assistant identifier is persisted locally in:

```text
arpip_research_assistant.json
```

## Architecture

The pipeline uses exactly one saved Backboard assistant named `ARPIP Research Intelligence Assistant`. On the first successful run, the assistant ID is saved to `arpip_research_assistant.json`; later runs reuse that assistant. Each execution starts one new Backboard thread under that assistant, then all workflow stages continue in the same thread so each stage can use prior context.

## Workflow Stages

1. **Research / Gather** — Uses Backboard with `web_search="Auto"` to collect at least five recent, sourced findings where available.
2. **Technical Analysis** — Uses the Stage 1 findings in the same thread to produce exactly three technical insights or research angles.
3. **Report Writing** — Uses the full thread context to create a professional Markdown report with findings, technical analysis, relevance to ARPIP, limitations, future opportunities, and sources.

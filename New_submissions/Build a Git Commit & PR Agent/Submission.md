# Git Commit & PR Agent

This project is a Git Commit & PR Agent, built as a developer-tooling extension of the Mission Intelligence Platform's engineering workflow. It demonstrates how a lightweight, AI-assisted CLI can read a developer's local changes and propose a ready-to-use commit message or Pull Request summary, while still leaving the final decision of what gets written to git history entirely in the developer's hands.

Given the output of `git diff` — staged changes, or the diff between any two branches — the CLI reads the raw diff and per-file statistics, then sends them to an LLM through the Anthropic API, which classifies the type of change and drafts a properly-scoped commit subject and body, or, for Pull Requests, a title, a change summary, a testing checklist, and a list of potential risks. That output is never committed or pushed automatically — it is printed to the terminal for the developer to review, who must explicitly re-run the tool with `--apply` before anything is written to the repository.

If an `ANTHROPIC_API_KEY` is available and the API call succeeds, Claude writes the message directly. If the key is missing, or the call fails for any reason, the tool falls back to a local, rule-based heuristic generator — no network call, no cost, and no external system ever contacted — so the developer's workflow is never blocked. Every generated message, whether from Claude or the heuristic engine, goes through the same review step before being applied, and nothing is silently written to the repository.

The result is a complete, working demonstration of the diff-to-message pattern: Git Diff → Diff Parsing & Stats → LLM (or Heuristic Fallback) → Proposed Commit/PR Message → Human Review → Applied Commit / Saved PR Summary.

## Quick Start

```bash
export ANTHROPIC_API_KEY="sk-ant-..."   # optional — heuristic mode is used otherwise

git add .
python tools/git_commit_pr_agent.py commit           # preview a commit message
python tools/git_commit_pr_agent.py commit --apply    # generate it and commit

python tools/git_commit_pr_agent.py pr                # preview a PR summary vs main/master
```

# Dice Smart Match Analyzer

A semantic resume-to-job matching layer built on top of **Dice's official MCP Server** (`mcp.dice.com/mcp`).

## The problem this solves

Dice recently launched an MCP server that lets AI assistants search Dice's job database using natural language. It's great for *finding* jobs — but it stops there. It doesn't tell a candidate **why** a job is a good fit, where their skill gaps are, or how to position their resume for that specific role.

This project adds that missing layer.

## What it does

1. **Connects to Dice's live MCP server** (`dice_smart_match.ipynb`) using the official MCP Python SDK over Streamable HTTP — no API key needed, exactly as documented in Dice's own MCP integration guide
2. **Pulls real job listings** via the `search_jobs` tool
3. **Runs semantic match scoring** using an LLM (Groq, OpenAI-compatible) — not just keyword overlap:
   - Overall match score (0–100)
   - Matched skills
   - Missing skills / gaps
   - A tailored one-line resume summary suggestion for that specific job
4. **Visual dashboard** (`dice_smart_match.html`) — a standalone interactive UI demonstrating the scoring output and match breakdown per job

## Why this matters for Dice

Dice's own product reviews frequently mention unclear candidate-job fit and outdated/duplicate profiles. An explainable matching layer — showing *why* a Match Score was given, not just the number — is a natural extension of the AI Boolean enhancer and Match Score features Dice already ships for recruiters, applied here from the candidate's side.

## Files

| File | Description |
|---|---|
| `dice_smart_match.ipynb` | Core pipeline — connects to Dice's MCP server, retrieves jobs, runs LLM-based semantic scoring |
| `dice_smart_match.html` | Interactive dashboard demo of the scoring output |

## Tech stack

Python · MCP SDK (Streamable HTTP) · Groq (OpenAI-compatible LLM API) · Pandas · Matplotlib · Chart.js

## Run it yourself

1. Open `dice_smart_match.ipynb` in Google Colab
2. Add your free Groq API key in the config cell
3. Run all cells — it connects live to `mcp.dice.com/mcp` and scores real job listings against a sample resume

---

Built by [Greeshma](https://github.com/greeshmab21) — exploring what an explainable matching layer could look like on top of Dice's MCP server.

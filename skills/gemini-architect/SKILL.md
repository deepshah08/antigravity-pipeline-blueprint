---
name: gemini-architect
description: "Offload high-level planning, system architecture, brainstorming, and trade-off analysis to Google AI Studio Gemini API quota (strictly models >= 3.5)."
---

# Gemini Architect & Ideation Skill (>= 3.5 Models Only)

This skill allows Antigravity to offload intensive reasoning, system architecture design, trade-off comparisons, and deep code reviews to Gemini via the Google AI Studio API, strictly utilizing modern models ($\ge 3.5$) and preserving your Antigravity agent quotas for file editing, tool execution, and local verification.

## Active Model Tiers ($\ge 3.5$ Only)

1. **Primary Generation / Ideation:** `gemini-3.7-flash` (with fallback to `gemini-3.6-flash`, `gemini-3.5-flash`, `gemini-3.5-flash-lite`).
2. **Primary Agent Interaction:** `antigravity-preview-05-2026` (via Interactions API).
3. **Legacy Filter:** All models $< 3.5$ (e.g. 1.5, 2.0, 2.5) are permanently ignored.

## Tools Provided via MCP (`gemini-architect`)

- `gemini_architect`: Generates production-grade architecture blueprints, data flows, target file structures, and step-by-step Antigravity implementation plans.
- `gemini_brainstorm`: Explores creative approaches, failure modes, trade-offs, and comparison tables.
- `gemini_review`: Reviews specs or code with actionable feedback.
- `gemini_query`: Direct conversational query to Gemini 3.7 Flash or Antigravity Preview.

## Terminal Usage

```bash
# Query Gemini 3.7 Flash
gemini-cli "Summarize event sourcing pros and cons"

# Query Antigravity Agent Preview (05-2026)
python3 ~/.gemini/config/tools/gemini_mcp_server.py --antigravity "Brainstorm agent orchestration"

# Architecture plan generation
gemini-architect "Design a distributed consensus mechanism"
```

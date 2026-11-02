# Antigravity Multi-Agent Pipeline Blueprint 🚀

**The Reusable Source of Truth & Blueprint for Orchestrating Autonomous Multi-Agent Software Development Pipelines.**

---

## 📌 Executive Summary

This repository serves as the official, version-controlled architecture blueprint for running autonomous, multi-agent AI software engineering workflows. It relies strictly on **Google AI Studio Gemini API endpoints** ($\ge 3.5$) and **local Antigravity orchestration**, completely eliminating external cloud sandbox dependencies (Google Jules has been decommissioned):

1. **Primary Orchestrator (Local Antigravity Agent):** High-level architectural planning, bucket tracking, gate reviews, and merge controls.
2. **Cloud Reasoning & Architecture (Google AI Studio Gemini API):** Parallel system design, trade-off analysis, ideation, and deep code review via `gemini-3.7-flash` and the `gemini-architect` MCP tool suite.
3. **Local Execution Subagents (Antigravity):** Isolated branch/workspace execution and local test verification (`pytest`, `npm test`).
4. **CI/CD Review & Deployment (GitHub Actions):** Automated `gemini-3.6-flash` PR code reviews and zero-downtime static PWA deployments to GitHub Pages.

---

## 🛠️ Model Usage & Quota Hierarchy

To maximize throughput while strictly conserving high-tier token quotas, follow this operational hierarchy:

$$\text{Gemini 3.7 Flash / AI Studio API} \longrightarrow \text{Antigravity Local Subagents} \longrightarrow \text{Antigravity Primary Orchestrator}$$

---

## 📜 Version History & Changelog

| Version | Release Date | Key Enhancements |
| :--- | :--- | :--- |
| **v3.0.0** | 2026-11-01 | **Current Master:** Completely decommissioned Google Jules; migrated to Google AI Studio Gemini API (`gemini-3.7-flash` / `gemini-architect`) and local Antigravity subagent execution. |
| **v2.2.0** | 2026-08-11 | Added `jules-auto-reviewer` & `keenable-cli` reusable skills, automated cloud scraper workflows (`workflow_dispatch`, `schedule` cron), and link sanitization. |
| **v2.0.0** | 2026-08-10 | Integrated 5-min subagent latency rule, GitHub Actions `gemini-3.6-flash` PR reviews, and GitHub Pages deployment. |
| **v1.2.0** | 2026-08-09 | Added 5-minute polling latency rule for Flash Session Managers to save 80%+ context tokens. |
| **v1.1.0** | 2026-08-09 | Introduced asynchronous Flash Session Manager subagent handshakes for PR review/merges. |
| **v1.0.0** | 2026-08-09 | Initial release: Primary Orchestrator + cloud execution. |

---

## 📁 Repository Structure

```text
antigravity-pipeline-blueprint/
├── README.md                          # Master overview & quickstart
├── VERSION                            # Current blueprint version tag (3.0.0)
├── architecture/
│   ├── v1.0.0-initial.md             # Initial single-agent baseline
│   └── v3.0.0-master.md              # Current Gemini API + Antigravity architecture
├── skills/
│   ├── gemini-architect/              # Gemini AI Studio architecture & ideation skill
│   └── keenable-cli/                  # Keenable web search & page fetching CLI skill
└── templates/
    ├── task-tracker.md                # Reusable Bucketed Execution Tracker
    ├── subagent-manager-prompt.md     # Subagent Manager execution prompt
    └── github-actions/
        ├── deploy-gh-pages.yml       # GitHub Pages PWA & Cloud Scraper deployment workflow
        └── gemini-code-review.yml    # Gemini 3.6 Flash PR review workflow
```

---

## 🚀 Quickstart: Applying to Any New Project

To apply this pipeline architecture to a new project:

1. **Copy `templates/task-tracker.md`** into your project's root as `task.md`.
2. **Organize Work into Sequential Buckets** (e.g. Bucket 1: Foundation, Bucket 2: Core Features, Bucket 3: Polish).
3. **Offload Architectural Design & Spec Review** to Google AI Studio Gemini API via `gemini-architect`.
4. **Dispatch Local Antigravity Subagents** using the prompt template in `templates/subagent-manager-prompt.md`.
5. **Gate Review & Merge:** As subagents complete tasks, the Primary Orchestrator conducts an Antigravity Gate Review, runs automated tests, and merges into `main`.
6. **Auto Deploy:** GitHub Actions builds and deploys the project live to GitHub Pages.

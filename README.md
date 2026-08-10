# Antigravity Multi-Agent Pipeline Blueprint 🚀

**The Reusable Source of Truth & Blueprint for Orchestrating Autonomous Multi-Agent Software Development Pipelines.**

---

## 📌 Executive Summary

This repository serves as the official, version-controlled architecture blueprint for running autonomous, multi-agent AI software engineering workflows. It combines:

1. **Primary Orchestrator (High-Reasoning Model):** High-level architectural planning, bucket tracking, and PR gate reviews.
2. **Jules Executors (Cloud Sessions):** Parallel code generation and execution in isolated cloud sandboxes.
3. **Flash Session Managers (Low-Cost Subagents):** Asynchronous session monitoring using 5-minute wait timers for maximum token efficiency.
4. **CI/CD Review & Deployment (GitHub Actions):** Automated `gemini-3.6-flash` PR code reviews and zero-downtime static PWA deployments to GitHub Pages.

---

## 🛠️ Model Usage & Quota Hierarchy

To maximize throughput while strictly conserving high-tier token quotas, follow this operational hierarchy:

$$\text{Jules (100 daily sessions)} \longrightarrow \text{Gemini Flash (Medium/Low)} \longrightarrow \text{Gemini 3.1 Pro} \longrightarrow \text{Opus / High-Tier Orchestrator}$$

---

## 📜 Version History & Changelog

| Version | Release Date | Key Enhancements |
| :--- | :--- | :--- |
| **v2.0.0** | 2026-08-10 | **Current Master:** Integrated 5-min subagent latency rule, GitHub Actions `gemini-3.6-flash` PR reviews, and GitHub Pages deployment. |
| **v1.2.0** | 2026-08-09 | Added 5-minute polling latency rule for Flash Session Managers to save 80%+ context tokens. |
| **v1.1.0** | 2026-08-09 | Introduced asynchronous Flash Session Manager subagent handshakes for PR review/merges. |
| **v1.0.0** | 2026-08-09 | Initial release: Primary Orchestrator + Jules cloud execution. |

---

## 📁 Repository Structure

```text
antigravity-pipeline-blueprint/
├── README.md                          # Master overview & quickstart
├── VERSION                            # Current blueprint version tag
├── architecture/
│   ├── v1.0.0-initial.md             # Initial single-agent baseline
│   └── v2.0.0-master.md              # Current state-of-the-art architecture
└── templates/
    ├── task-tracker.md                # Reusable Bucketed Execution Tracker
    ├── session-manager-prompt.md      # Asynchronous Flash Session Manager prompt
    └── github-actions/
        ├── deploy-gh-pages.yml       # GitHub Pages PWA deployment workflow
        └── gemini-code-review.yml    # Gemini 3.6 Flash PR review workflow
```

---

## 🚀 Quickstart: Applying to Any New Project

To apply this pipeline architecture to a new project:

1. **Copy `templates/task-tracker.md`** into your project's root as `task.md`.
2. **Organize Work into Sequential Buckets** (e.g. Bucket 1: Foundation, Bucket 2: Core Features, Bucket 3: Polish).
3. **Dispatch Jules Sessions** for each task inside a bucket.
4. **Spawn Flash Session Managers** using the prompt template in `templates/session-manager-prompt.md` with **300s (5-min) wait timers**.
5. **Gate Review & Merge:** As subagents complete PRs, the Primary Orchestrator conducts an Antigravity Gate Review and merges into `main`.
6. **Auto Deploy:** GitHub Actions builds and deploys the project live to GitHub Pages.

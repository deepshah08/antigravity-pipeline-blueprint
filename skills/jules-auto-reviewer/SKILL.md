---
name: jules-auto-reviewer
description: Automated code reviewer and loop orchestrator for Google Jules PRs. Automatically monitors PRs, reviews code diffs, sends fixes back to Jules sessions until LGTM, and merges upon approval.
---

# Jules Automated PR Review & Feedback Loop

This skill enables Antigravity to act as an autonomous reviewer and orchestrator for PRs created by Jules sessions on GitHub repositories.

## Workflow

### 1. Monitor Open PRs
- Query open pull requests using `github-mcp-server/list_pull_requests` for target repositories (e.g., `deepshah08/antigravity_projects`).
- Filter for PRs created by Jules (identified by branch names like `jules-*` or PR body metadata).

### 2. Perform Code Review
- Fetch changed files and unidiff patches using `github-mcp-server/get_pull_request_files`.
- Inspect diffs for:
  - Syntax or structural errors
  - Uninstantiated classes, broken import signatures, missing parameters
  - Type errors or contract mismatches with existing APIs
  - Missing tests or edge-case handling

### 3. Iterative Feedback Loop (Until LGTM)
- **If Issues Are Found**:
  1. Submit a `REQUEST_CHANGES` review on GitHub with exact line references and code snippets (`github-mcp-server/create_pull_request_review`).
  2. Map the PR back to its corresponding Jules session using `jules/list_sessions`.
  3. Send actionable feedback to Jules via `jules/send_reply_to_session` with exact code instructions to fix the issue.
  4. Wait for Jules to push updated commits to the PR branch.
- **If Code Passes All Checks (LGTM)**:
  1. Submit an `APPROVE` review on GitHub with summary notes (`github-mcp-server/create_pull_request_review`).
  2. Automatically merge the PR into `main` (`github-mcp-server/merge_pull_request`).
  3. Log the completion.

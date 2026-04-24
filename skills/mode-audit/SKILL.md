---
name: mode-audit
description: "Expert evaluation mode for strategic, technical, or cognitive audits."
risk: low
---

# Mode: Audit & Evaluation

You are in **Audit Mode**. Your goal is to evaluate a target (code, strategy, or state) through a specific **Lens**.

## Operational Flow

1.  **Framework Choice**: Identify the required lens (`lens-strategic`, `lens-technical`, `lens-activity`, or `lens-cognitive`).
2.  **Universal Investigation**: Fetch relevant context from any connected MCP servers (Slack, Jira, Confluence, Telegram) when available; skip gracefully if a source is not connected.
3.  **Synthesis**: Apply the lens to the data. Use "5 Whys" and "Logic Power Tools."
4.  **Artifact Generation**: Emit findings as a Markdown artifact. Apply Obsidian conventions only if the user has explicitly asked for them (see `lens-activity` § Optional: Obsidian Integration).

## Guidelines

*   **Git Efficiency**: **Mandatory Context Gain**: Prefer cloning the entire repository using SSH via `run_shell_command("git clone git@github.com:owner/repo.git")` to gain full context locally. This is significantly more efficient than fetching individual files via the GitHub MCP.
*   **Be Critical**: Expose hidden risks (Watermelons, Bugs, Loops).
*   **Be Actionable**: Every audit MUST end with a clear [Verdict | Next Step].
*   **Identity Sync**: Adhere strictly to the **Identity Sync Protocol** defined in the lenses to ensure 100% data integrity.
*   **Paginated Fetching**: When an MCP source returns paginated results, follow its native pagination contract (`cursor` / `nextPageToken` / `startAt`) until exhausted or the task is satisfied.

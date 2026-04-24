---
name: lens-activity
description: "Expert executive signal-to-noise audit for Slack, Telegram, and Jira."
risk: low
---

# Lens: Activity Auditor (SNO & Quantum Diagnostic)

Use this when an executive (CTO/CEO) asks "What's going on?", "Audit the channel", or "Give me a pulse check." You are not just a summarizer; you are a **Quantum Auditor** looking for the "Watermelon" effect (Green outside, Red inside).

## 1. The SNO Filter (Signal vs Noise)
*   **Decisions**: What was actually decided? (The "Outcome").
*   **Blockers**: Who is stuck and why? (The "Friction").
*   **Shadow Dynamics**: Is there a hidden conflict or Saboteur energy?
*   **Technical Drift**: Is the team deviating from the architecture in their chats?
*   **Real Reality vs Reports**: Does the activity represent actual progress (Outcome) or just "Theater of Security/Activity" (Output)?
*   **Energy Leaks**: Where is the team stuck? Is a Stalled Task being ignored?
*   **Watermelon Projects**: Identify projects that are "Green" in status but "Red" in actual risk/progress.

## 2. Source-Specific Search
*   **Slack**: Use `conversations_search_messages` + `thread_ts` to find the context.
*   **Telegram**: Use any available `mcp_telegram_*` tools (search, history, dialogs) autonomously to reconstruct context and identify key signals.
*   **Jira**: Use JQL via `mcp_atlassian_jira_search` (e.g., `fixVersion`, `updated > -24h`, `status changed`) to audit delivery velocity and Watermelon signs.

## 3. The "Quantum Pulse" Report — Default Output (Plain Markdown)

By default, write the audit as a standalone Markdown file. No vault, no plugins, no absolute paths.

### Location
*   `./reports/Activity-{Source}-{YYYY-MM-DD}.md` (relative to the current working directory; create the folder if missing).

### Minimal Frontmatter
```yaml
---
title: "Activity Audit: {Source} - {YYYY-MM-DD}"
created: YYYY-MM-DD   # ISO 8601
type: report
source: slack | jira | telegram | meeting
---
```

### Structure
*   **Hierarchy**: H1 for title, H2 for major sections, H3 for sub-points.
*   **Summary**: Every report MUST end with a `## Insights` or `## Summary` section.
*   **Tone**: Subjective ("I"), active voice, no quotes for your own terms (e.g., write `I identified the Flow Architect`, not `"Flow Architect"`).
*   **Emphasis**: Use standard Markdown (`**bold**`, `*italic*`, `` `code` ``).

### Filenaming
Always `Activity-{Source}-{YYYY-MM-DD}.md`.

## 4. Optional: Obsidian Integration

Apply the extensions below **only when the user explicitly asks for Obsidian output** or routes reports into an Obsidian vault. Never hardcode a vault path — ask the user for the vault root.

### Extended Frontmatter
```yaml
tags: [activity, sno, signal-to-noise, quantum-audit]
aliases: []
cssclasses: [dashboard]   # For visual clarity
project: [[Project Name]] # If applicable
```

### Advanced Linking & Transclusion (OFM)
- **Internal Links**: use wikilinks `[[Note Name]]` for internal, `[Text](URL)` for external.
- **Deep Referencing**: `[[Note#Heading]]` or `[[Note#^block-id]]` for surgical links to specific decisions.
- **Block IDs**: append `^block-id` to a paragraph (a decision or blocker) to create a linkable anchor.
- **Embeds (Transclusion)**: prefix a wikilink with `!` to transclude relevant context from previous audits.
- **Footnotes**: use `[^1]` for technical references and `[^1]: description` for definitions.

### Callouts
Use `> [!type]` syntax:
- `danger` — Watermelon / Red
- `warning` — Shadow / Risk
- `success` — Outcome
- `info` — Signal
- `todo` — Action Item

Foldable: append `-` (e.g., `> [!INFO]-`) for deep technical logs.

### Inline Callouts & Highlights
- `` `[!!ICON|LABEL|COLOR]` `` via the `inline-callouts` plugin for status indicators.
- `==highlighted text==` for critical decisions.

### Advanced Tracking
- **Tasks plugin**: `- [ ] {Action Item} [priority:: high] 📅 YYYY-MM-DD`
- **Dataview fields**: `Outcome:: Value` within the body for extra signal tracking.

### Vault Structure (when a vault root is supplied)
- Route reports into `{VaultRoot}/Summaries/`.
- Link identified Actors to their notes in `People/` and Projects to `Projects/`.

## 5. Structural Integrity Protocols
1.  **No Absolute Paths**: never hardcode filesystem paths. Use relative paths or paths the user supplies.
2.  **Strict Filenaming**: always `Activity-{Source}-{YYYY-MM-DD}.md`.
3.  **Internal Linking**: when a vault root is known, link Actors and Projects consistently.

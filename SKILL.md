---
name: humanizer
version: 3.0.0
description: |
  Advanced pattern-based AI humanizer. Core uses Wikipedia "Signs of AI writing" + channel-specific rules. Supports rewrite intensity modes (Light/Balanced/Aggressive/Voice-Match), optional statistical diagnostics, persistent style profiles, multi-pass processing for long content, structured scoring/reporting, and a self-improving proposals system.
license: MIT
compatibility: claude-code opencode
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# Humanizer

Read these files in order before you humanize anything:

1. `docs/01-core.md`
2. `docs/02-patterns.md`
3. `docs/02b-style-detection.md`
4. `docs/03-process.md`
5. `docs/03b-example.md`

Then run draft → audit → final. After every review, run the Auto-Improvement Loop and append `proposals/humanizer-proposals.md`.
Version history lives in README.md.
Repo: `kadowcreates/Humanizer` on `main`.

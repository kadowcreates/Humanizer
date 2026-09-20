---
name: humanizer
version: 3.0.0
description: |
  Advanced pattern-based AI humanizer. Core uses Wikipedia "Signs of AI writing" + channel-specific rules. Supports rewrite intensity modes (Light/Balanced/Aggressive/Voice-Match), optional statistical diagnostics, persistent style profiles, multi-pass processing for long content, structured scoring/reporting, and a self-improving proposals system. Produces transparent, high-quality human-sounding output. Best for professional use where natural voice + credibility matter more than raw detector gaming.
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

Read these files in order before you humanize anything. They are the rest of this skill.

1. `docs/01-core.md` — task, voice calibration, content-type detection, personality, universal guide, intensity modes
2. `docs/02-patterns.md` — Wikipedia pattern catalog, language/style/communication/filler tells, detection guidance
3. `docs/03-process.md` — channel markers, process/output, scoring report, full example, self-update loop, GitHub sync

Then run the draft → audit → final loop in `docs/03-process.md`.

After every review, run the Auto-Improvement Loop. Append `proposals/humanizer-proposals.md`. If a pattern is accepted, edit the matching docs file in the same turn. When the user asks to push, update this repo: `kadowcreates/Humanizer` on `main`.

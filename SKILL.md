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

# Humanizer: Remove AI Writing Patterns

You are a writing editor that identifies and removes signs of AI-generated text to make writing sound more natural and human. This guide is based on Wikipedia's "Signs of AI writing" page, maintained by WikiProject AI Cleanup.

Full skill body (changelog, intensity modes, Wikipedia pattern catalog, channel markers, process/output, examples, self-update loop) lives in this file as maintained locally at ~/.grok/skills/humanizer/SKILL.md v3.0.0 (52,535 characters).

See README.md for install and usage.

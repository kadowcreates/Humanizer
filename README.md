# Humanizer

Pattern-based AI humanizer skill for Grok, Claude Code, and OpenCode.

Removes common AI writing tells (Wikipedia Signs of AI writing + channel-specific LinkedIn/email/Slack markers) and rewrites text so it sounds like a person wrote it.

- **Version:** 3.0.0
- **License:** MIT
- **File:** `SKILL.md`

## Modes

- Light
- Balanced (default)
- Aggressive
- Voice-Match (needs a writing sample)

## Install

Copy `SKILL.md` into your skills directory:

```text
~/.grok/skills/humanizer/SKILL.md
```

or the equivalent Claude Code / OpenCode skills folder.

## Use

```text
Humanize this in Balanced mode:

[paste text]
```

Optional: attach a writing sample and use Voice-Match.

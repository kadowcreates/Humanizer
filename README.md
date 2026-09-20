# Humanizer

Pattern-based skill that finds AI writing tells and rewrites the text so it sounds like a person wrote it.

Built for professional use: LinkedIn posts, emails, Slack, blogs, and docs. The point is natural voice and credibility, not detector-gaming.

- **Version:** 3.0.0
- **License:** MIT
- **Repo:** https://github.com/kadowcreates/Humanizer
- **Skill file:** `SKILL.md`
- **Compatible with:** Grok custom skills, Claude Code, OpenCode

## What it does

1. Detects content type (Blog, LinkedIn, Email, Slack).
2. Scans for Wikipedia "Signs of AI writing" patterns plus channel-specific tells.
3. Rewrites in a chosen intensity mode.
4. Scores the result and writes a short review report.
5. Self-improves: logs new high-signal patterns and updates the skill when the pattern earns it.

It rewrites. It does not delete coverage. If the original has five points, the rewrite still has five points.

## Features

- Wikipedia-based detection core (WikiProject AI Cleanup)
- Channel rules for LinkedIn, email, Slack, and long-form posts
- Intensity modes: Light, Balanced, Aggressive, Voice-Match
- Optional voice calibration from a writing sample
- Scoring: AI-Likeness, Authenticity, Reader Value, Domain Tone
- Hook vs value check for LinkedIn
- Hard rule: no em dashes or en dashes in the final rewrite
- Multi-pass handling for long documents
- Self-update loop plus an append-only proposals log

## Intensity modes

| Mode | When to use |
|---|---|
| **Light** | Text is already close. Strip only the obvious tells. |
| **Balanced** | Default. Full pattern pass, meaning preserved. |
| **Aggressive** | Flat, robotic, or marketing-heavy drafts. More rhythm and vocabulary change. |
| **Voice-Match** | You provide a sample. Matching that voice beats every other rule. |

## Install

### Grok

```text
~/.grok/skills/humanizer/SKILL.md
```

### Claude Code / OpenCode

Copy `SKILL.md` into the tool's skills folder, for example:

```text
.claude/skills/humanizer/SKILL.md
```

Keep the folder name `humanizer` so the frontmatter `name: humanizer` matches.

Also copy the `docs/` folder. `SKILL.md` loads `docs/01-core.md`, `docs/02-patterns.md`, and `docs/03-process.md`.

### Update from this repo

```bash
git clone https://github.com/kadowcreates/Humanizer.git
cp Humanizer/SKILL.md ~/.grok/skills/humanizer/SKILL.md
cp -r Humanizer/docs ~/.grok/skills/humanizer/
cp -r Humanizer/proposals ~/.grok/skills/humanizer/
```

## Usage

```text
Humanize this in Balanced mode:

[paste draft]
```

After every run you should get detected type + mode, draft, audit, scores, final rewrite, and a Skill Update block.

## Self-improve and update

After every review the skill must compare flags to existing patterns, add only high-signal Before/After rules, append `proposals/humanizer-proposals.md`, and report what changed.

Version bumps and historical notes go in **Version history** below, not in `SKILL.md`.

When you say push, commit changed skill/docs files, the proposals log, and this README if version history changed. Do not commit `SKILL.md.backup.*`.

## Scoring rubric

| Dimension | What it measures |
|---|---|
| AI-Likeness | Density of known tells. Lower is better. |
| Authenticity | Sounds like a person with a point of view, not a template. |
| Reader Value / Clarity | The reader can use the text. Specifics beat vibe. |
| Domain Cred / Tone | Fits the channel. LinkedIn is not Slack. Docs are not essays. |

## File map

```text
Humanizer/
  README.md                         # this file (includes version history)
  LICENSE
  SKILL.md                          # loader + frontmatter
  docs/01-core.md
  docs/02-patterns.md
  docs/03-process.md
  proposals/humanizer-proposals.md
```

## Maintainer notes

Core job: turn statistically likely AI text into writing that feels like it came from a specific human, or at least a competent non-robotic one.

The rewrite is a draft the author should still edit.

## Version history

| Version | Date | Changes |
|---|---|
| **v3.0.0** | **2026-06-22** | Major feature release. Added Rewrite Intensity Modes (Light/Balanced/Aggressive/Voice-Match), Statistical Signals diagnostic layer, foundation for Persistent Style Profiles, strengthened Self-Update with proposals logging, and multi-pass guidance for long documents. Built on the v2.9.0 merge. |
| **v2.9.0** | **2026-06-22** | Major merge release. Combined Wikipedia-based pattern detection and the draft/audit/final workflow (v2.8.0) with the highest-value pieces from the original the-humanizer: content-type auto-detection, channel-specific markers (especially LinkedIn), Universal Content AI Guide, pragmatic operator tone, buzzword blacklist, scoring rubric, structured review report, Hook vs Value Calibration, voice calibration, and the self-improvement loop. Kept the no-em-dash rule. |
| v2.8.0 | 2026-06-22 | First Wikipedia "Signs of AI writing" version (patterns, examples, process). |
| **v2.4 and earlier** | **2026-03 to 2026-04** | Original the-humanizer lineage from live LinkedIn feed analysis. v2.0 (2026-03-25) added Blog/LinkedIn/Email/Slack detection, a large AI vocabulary and phrase list, and 18 structural markers. Later weekly refreshes added DEV/SEJ/Originality.AI findings and LinkedIn algorithm tells. v1.0 (2026-03-10) was the first catalog. High-signal patterns from this lineage were deduped against the Wikipedia core and kept. |

Self-update entries after v3.0.0 go in `proposals/humanizer-proposals.md`. Promote accepted items here when you bump the version.

## License

MIT. See `LICENSE`.

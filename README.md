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

Or pull if you already cloned it:

```bash
cd Humanizer && git pull
cp SKILL.md ~/.grok/skills/humanizer/SKILL.md
cp -r docs proposals ~/.grok/skills/humanizer/
```

## Usage

```text
Humanize this in Balanced mode:

[paste draft]
```

Voice-Match:

```text
Humanize this in Voice-Match mode.
Use this sample of my writing:

[sample]

Draft to rewrite:

[draft]
```

LinkedIn-specific:

```text
Humanize this LinkedIn post in Aggressive mode. Keep the ask. Kill the engagement bait.
```

After every run you should get:

1. Detected content type + mode
2. Draft rewrite
3. "What still feels AI" audit
4. Scores + structured report
5. Final rewrite (no em/en dashes)
6. Skill Update block (new patterns or none)

## Self-improve and update

This is not a static prompt. After every review the skill is required to run its own update step.

### What happens after each humanize pass

1. Compare flags from this review against patterns already in the skill files.
2. If a new high-signal pattern showed up, add it as a concrete Before/After rule.
3. Append a dated entry to `proposals/humanizer-proposals.md`.
4. Report:

```text
## Skill Update
- [X] new pattern(s) added: ...
- [ ] no new patterns found this review
```

Rules for adding patterns:

- Must be flaggable, not vague.
- Must include a Before/After example from the text just reviewed (anonymize if needed).
- No duplicates.
- Channel-specific tells go in `docs/03-process.md`. Universal tells go in `docs/02-patterns.md`.

### Proposals log

File: [`proposals/humanizer-proposals.md`](proposals/humanizer-proposals.md)

Each entry records:

- Date
- Content type
- Mode used
- New pattern or improvement
- Example
- Accepted / deferred / rejected

Accepted items get written into the matching docs file. Deferred items stay in the log until a later pass proves them.

### How you tell it to update

```text
Run the humanizer self-update on the last rewrite. Log proposals. If the pattern is high-signal, patch the skill files.
```

```text
Promote accepted proposals into the skill files and bump the changelog.
```

```text
Push the updated humanizer skill back to GitHub.
```

When you say push, the expected commit is:

- `SKILL.md` and/or `docs/*.md` (if patterns were added)
- `proposals/humanizer-proposals.md` (always append-only)
- `README.md` only if install/usage changed

Do not commit local backup files (`SKILL.md.backup.*`).

### What good self-improvement looks like

Good: "Tailing negation fragments after a complete clause (`no guessing`) now have a before/after under Negative Parallelisms."

Bad: "Make it sound more human." That is not a pattern.

The skill should get stricter and more specific over time. It should not grow a junk drawer of one-off gripes.

## Scoring rubric

| Dimension | What it measures |
|---|---|
| AI-Likeness | Density of known tells. Lower is better. |
| Authenticity | Sounds like a person with a point of view, not a template. |
| Reader Value / Clarity | The reader can use the text. Specifics beat vibe. |
| Domain Cred / Tone | Fits the channel. LinkedIn is not Slack. Docs are not essays. |

Scores are 1-10. They are a diagnostic, not a vanity metric.

## File map

```text
Humanizer/
  README.md                         # this file
  LICENSE                           # MIT
  SKILL.md                          # loader + frontmatter
  docs/01-core.md                   # task, voice, modes
  docs/02-patterns.md               # pattern catalog
  docs/03-process.md                # channels, report, self-update
  proposals/humanizer-proposals.md  # append-only improvement log
```

## Maintainer notes

Core job: turn statistically likely AI text into writing that feels like it came from a specific human, or at least a competent non-robotic one.

Design bets:

- Wikipedia patterns = precision core.
- Channel layer = where the text will actually live.
- Scores + report = force a real audit, not just a prettier draft.
- No em/en dashes in finals = remove one of the loudest remaining tells.
- Self-update loop = the catalog does not freeze in June 2026.

The rewrite is a draft the author should still edit. It is not a claim that the output "is" the user's voice.

## License

MIT. See `LICENSE`.

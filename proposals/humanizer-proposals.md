# Humanizer proposals log

Append-only. Newest entries at the top.

Status values: `accepted` (written into skill files), `deferred` (needs another example), `rejected` (too vague, duplicate, or false positive risk).

---

## Template

```markdown
### YYYY-MM-DD
- Content type:
- Mode:
- Status:
- Pattern / change:
- Section target:
- Example (anonymized):
  - Before:
  - After:
- Notes:
```

---

### 2026-09-19
- Content type: n/a (repo bootstrap)
- Mode: n/a
- Status: accepted
- Pattern / change: Split the 54k skill into loader + docs so GitHub can hold the full catalog. README now documents install, modes, scoring, and the self-update loop.
- Section target: README.md; SKILL.md; docs/; proposals/humanizer-proposals.md
- Example: n/a
- Notes: Local Grok skill path still has the single-file SKILL.md. Repo uses split files for push size.

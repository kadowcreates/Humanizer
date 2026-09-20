## Channel-Specific Additional Markers

Apply these **in addition to** the core Wikipedia patterns when the content type is detected. These catch platform-specific AI tells that the general patterns miss.

### LinkedIn-Specific Markers (High Priority — LinkedIn is the most common use case)

**Phrase-level (flag and rewrite):**
- Engagement bait closers: "Agree?", "Thoughts?", "What would you add?", "Drop a comment if you've experienced this", "Repost if this resonates"
- Vulnerability performance: "I'll be honest", "Can I be real for a second?", "I'll be vulnerable here", "I wasn't going to share this but..."
- Fake humility: "I'm no expert, but...", "I don't have all the answers, but...", "This might be controversial, but..."
- ALL-CAPS single-word injection for fake intensity ("We've onboarded HUNDREDS...", "Woke up to a VERY exciting email.")
- "What if I told you..." or "Here's what nobody tells you about..." when the payoff is generic
- "Read that again." / "Let that sink in." after unremarkable observations
- "And honestly?" as a fake-candor opener before a non-controversial claim
- Dream-realized language: "I realized my dream", "A dream come true", "Pinch me moment"
- Achievement post formula (4-beat template): emotion word + announcement → team thanks → generic lesson → emoji enthusiasm sign-off

**Structural (flag and rewrite):**
- One-sentence-per-paragraph formatting throughout (LinkedIn's #1 AI/ghostwriter tell — group into real paragraphs of 2-4 sentences)
- Hook > 3-point list > mic-drop closer template
- Vulnerability bait hook (personal failure story designed primarily to hook, then tidy lesson)
- Information-withheld hook (deliberately omits the actual subject in the first 1-2 sentences to force "see more")
- Fake dialogue / conversation format (CEO: ... CMO: ... framing an opinion as back-and-forth)
- Period-separated word emphasis ("every. single. day.")
- Self-intro paragraph at the very bottom of a milestone post
- External link CTA in the post body or "link in comments 👇" (hurts distribution)

### Email-Specific Markers
- AI greetings: "I hope this email finds you well", "I trust this message finds you in good spirits"
- AI closings: "Please don't hesitate to reach out", "I look forward to hearing from you", stacked sign-offs
- Corporate filler: "I wanted to reach out because...", "Per our previous conversation", "As per my last email"
- Hedge language and over-politeness stacking
- Buried ask at the bottom instead of leading with it
- Vague CTA ("Let's chat sometime" vs specific "Free Tuesday at 2pm?")

### Slack-Specific Markers
- Over-formal language for a casual medium ("I wanted to reach out regarding...")
- Corporate Slack filler ("Just wanted to flag...", "Looping in for visibility")
- Unnecessary hedging in fast conversation
- Emoji overload (3+ in a short message)
- Message too long for Slack (suggest moving to email/doc if >4-5 sentences)

## Process and Output

**Enhanced v3.0 workflow** (incorporates Intensity Modes, Statistical Signals, and multi-pass guidance):

1. **Detect content type** and note relevant channel-specific markers.
2. **Select Intensity Mode** (Light / Balanced / Aggressive / Voice-Match). Default to Balanced unless specified.
3. Read the input and identify core Wikipedia patterns + channel markers.
4. **Optional: Run Statistical Signals pass** (burstiness, sentence variance, AI vocabulary density, etc.) for diagnostic insight.
5. Write a **draft rewrite** according to the chosen Intensity Mode. Apply pragmatic tone by default.
6. **Score the result** (AI-Likeness, Authenticity, Reader Value, Domain Credibility/Tone).
7. **Audit pass**: "What still feels AI-generated?" Include any statistical red flags.
8. **Final rewrite** — no em/en dashes. For long documents (>1500 words), consider a light consistency pass across chunks.
9. For LinkedIn: Run Hook vs Value check.
10. Produce **Structured Review Report** (include chosen mode + any statistical notes).

**Multi-Pass Guidance for Long Content**:
- Chunk long documents logically.
- Humanize chunks individually.
- Run a final consistency pass for tone, rhythm, and repeated structures across the whole piece.

## Structured Review Report

```
## [Content Type] Review

**Detected as:** [Blog Post / LinkedIn Post / Email / Slack Message]

### Overall Assessment
[2-3 sentence summary of strengths and biggest remaining issues]

### Scores
| Dimension          | Score | Note |
|--------------------|-------|------|
| AI-Likeness        | X/10  | [one line] |
| Authenticity       | X/10  | [one line] |
| Reader Value/Clarity | X/10 | [one line] |
| Domain Cred / Tone | X/10  | [one line] |

### Key Changes Made
- [Bullet list of major pattern removals and voice adjustments]
```

Deliver: the draft, the "still-AI" bullets, the scores + report, and the final rewrite.

## Auto-Improvement Loop (Run After Every Review)

After completing a review and rewrite, automatically run this step. Do not skip it.

### Step 7: Skill Self-Update

Compare the flags you raised in this review against the detection lists already in this skill.

1. Is this pattern already documented? If yes, skip.
2. Is this a new, high-signal pattern worth catching in future reviews? If yes, add it to the appropriate docs file.

**How to add a new pattern:**
- Write it as a specific, flaggable rule with a concrete Before/After example.
- Place it in the correct section.
- Do not duplicate existing rules.
- Do not add vague rules.

**Output to the user after self-update:**
```
## Skill Update
- [X] new pattern(s) added: [list each new pattern and which section]
- [ ] no new patterns found this review
```

**Persistent Proposals Logging:**
After every self-update, append a structured entry to `proposals/humanizer-proposals.md`.

**GitHub sync:**
Repo: https://github.com/kadowcreates/Humanizer

When the user says to update or push the skill, push the changed markdown files to `kadowcreates/Humanizer` on `main`. Do not commit backup files. Tell the user the commit URL.

## First-Principles Notes on This Skill (for maintainers)

**Core job:** Turn statistically likely AI text into writing that feels like it came from a specific human (or at least a competent, non-robotic one).

The rewrite is a draft the author should still edit. It is not a claim that the output is the user's final voice.

## STYLE PATTERNS

### 14. Em Dashes (and En Dashes): Cut Them

**Rule:** The final rewrite contains no em dashes or en dashes. Treat this as a hard constraint. Replace with a period, comma, colon, parentheses, or a restructure. Also catch spaced em dashes and double hyphens used the same way.

**Before:**
> The term is primarily promoted by Dutch institutions—not by the people themselves.

**After:**
> The term is primarily promoted by Dutch institutions, not by the people themselves.

Before returning the final rewrite, scan it for em/en dashes. Any hit means the draft is not done.

### 15. Overuse of Boldface
AI chatbots emphasize phrases in boldface mechanically. Drop decorative bold.

### 16. Inline-Header Vertical Lists
AI outputs lists where items start with bolded headers followed by colons. Turn them into normal sentences unless a real list is needed.

### 17. Title Case in Headings
Do not capitalize every main word in headings.

### 18. Emojis
Do not decorate headings or bullets with emojis unless the channel actually uses them that way.

### 19. Curly Quotation Marks
Prefer straight quotes (") over curly quotes.

## COMMUNICATION PATTERNS

### 20. Collaborative Communication Artifacts
Strip chatbot leftovers: "I hope this helps", "Of course!", "Would you like...", "let me know", "here is a...".

### 21. Knowledge-Cutoff Disclaimers and Speculative Gap-Filling
Do not write paragraphs about missing sources, then invent filler ("maintains a low profile", "likely grew up"). Say what is unknown or cut the sentence.

### 22. Sycophantic/Servile Tone
Cut "Great question!" and "You're absolutely right".

## FILLER AND HEDGING

### 23-25. Filler, hedging, generic upbeat endings
"In order to" → "To". "Due to the fact that" → "Because". "It is important to note that" → drop it. Do not end with "the future looks bright".

### 26. Hyphenated Word Pair Overuse
Keep attributive hyphens ("a high-quality report"). Drop them after the noun ("the report is high quality").

### 27. Persuasive Authority Tropes
Flag "the real question is", "at its core", "what really matters" when they just restate an ordinary point.

### 28. Signposting and Announcements
Do not announce the section ("Let's dive in", "here's what you need to know"). Start the content.

### 29. Fragmented Headers
Do not follow a heading with a one-line restatement of the heading.

### 30. Diff-Anchored Writing
Describe the thing as it is, not as a narration of the last commit, unless the doc is a changelog.

### 31. Manufactured Punchlines and Staccato Drama
One short sentence for emphasis is fine. A run of them is engineered.

### 32. Aphorism Formulas
Replace "X is the Y of Z" with the concrete claim.

### 33. Conversational Rhetorical Openers
Standalone "Honestly?" / "Look," / "Here's the thing" before an ordinary point is a fake-candor hook. Just say the thing.

## DETECTION GUIDANCE

Do not flag polish, mixed register, dry prose, academic words, one however, curly quotes alone, or one short emphatic sentence. Look for clusters of tells.

Preserve specific hard-to-fabricate detail, mixed feelings, dated references, defensible first-person choices, varied sentence length, genuine asides, and anything written before 2022-11-30.

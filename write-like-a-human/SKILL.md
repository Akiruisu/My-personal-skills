---
name: write-like-a-human
description: >
  Apply this skill any time you are writing long-form text: essays, articles, blog posts,
  reports, emails, scripts, stories, documentation, or any prose longer than ~3 paragraphs.
  Use it whenever the user asks you to "write", "draft", "compose", or "generate" any
  sustained piece of writing — even if they don't explicitly ask for human-sounding output.
  This skill corrects the statistical patterns that make LLM text detectable: banned vocabulary,
  uniform sentence rhythm, essay-bot structure, promotional tone, over-formatting, compulsive
  em dash use, false range constructions, negative parallelisms, and hedging. Do not skip this
  skill for "short" pieces — if you're writing more than three paragraphs, load it.
---

# SKILL: Write Like a Human

## Why this matters
LLMs produce statistically average text — meaning they converge toward the most common patterns in their training data. This creates a recognizable "AI voice" that readers increasingly detect. These rules are distilled from Wikipedia's *Signs of AI Writing* page and corroborating research. Following them makes output sound like a real person wrote it.

---

## RULES

### 1. VOCABULARY — The Banned List
Never use these words unless they are genuinely the best choice AND you've already avoided them everywhere else in the piece. They are overused by LLMs to the point of being a fingerprint:

> delve, intricate, tapestry, pivotal, underscore, landscape, foster, testament, enhance, crucial, vibrant, comprehensive, notable, significant, moreover, furthermore, multifaceted, nuanced, realm, journey (metaphorical), beacon, captivating, fascinating, breathtaking, majestic, stunning, rich cultural heritage, robust, seamless, transformative, game-changer, leveraging synergies

If you catch yourself about to type any of these, stop and replace with a concrete, specific word that actually describes the thing.

**Bad:** "This pivotal development fostered a multifaceted understanding of the landscape."
**Good:** "This changed how engineers thought about heat distribution in compact motors."

---

### 2. TONE — No Promotional Drift
AI defaults to advertisement-speak, especially about culture, places, or people. Avoid:
- Unearned superlatives ("one of the most important figures in...")
- Tourism-brochure adjectives ("nestled among rolling hills")
- Framing everything as historically significant or legacy-defining
- Calling things "fascinating," "remarkable," or "unique" without proving it

If something is important, *show* why — don't assert it.

---

### 3. SENTENCE RHYTHM — Vary It
AI produces sentences of nearly identical length and structure. This is one of the fastest ways readers sense something is off.

Rules:
- Mix short sentences with long ones. Deliberately.
- Don't start three sentences in a row the same way.
- Use fragments occasionally when emphasis calls for it. Like this.
- Let the rhythm match the content: tense moments = short sentences; complex explanations = longer ones.

**Bad (uniform):** "The system processes data in real time. It then sends signals to the actuator. The actuator responds within 50 milliseconds. This improves efficiency significantly."

**Good (varied):** "The system processes data in real time and pushes signals to the actuator — response time hovers around 50 ms. That's fast enough to matter."

---

### 4. STRUCTURE — No Essay-Bot Templates
AI defaults to rigid three-part structure: intro → body → summary. Avoid:
- Opening with "In today's fast-paced world..." / "In the dynamic landscape of..."
- Restating the intro in a conclusion paragraph word-for-word
- "In summary," / "In conclusion," / "Overall," / "To summarize," — unless the piece is genuinely long enough to need a recap
- Ending every section with a tidy wrap-up sentence that just repeats what was already said

Start with the most interesting thing, not a preamble. End when there's nothing left to say.

---

### 5. NEGATIVE PARALLELISMS — Cut Them
The "It's not X, it's Y" construction is one of the strongest AI tells:

- "It's not just a tool, it's a revolution."
- "This isn't about efficiency — it's about transformation."
- "He didn't fail. He learned."

Occasional use is fine in human writing. AI uses it compulsively. If you have more than one in a piece, delete all but maybe one.

---

### 6. FORMATTING — Less Is More
AI over-formats. Rules:
- Don't bold random phrases mid-paragraph for emphasis. If it's important enough to bold, restructure the sentence around it instead.
- Don't bullet everything. A list of 2–4 things can almost always be a sentence: "The system has three failure modes: overheating, signal loss, and firmware corruption."
- Avoid "Term: Definition" bullet structure unless it's genuinely a glossary.
- Don't use emojis in headings.
- Don't add a bullet format like: `**Key insight:** This matters because...`

---

### 7. TRANSITIONS — Rotate or Cut
Over-used connectors to minimize:
> Furthermore, Moreover, Additionally, In addition, It is worth noting, It is important to note, On the other hand, That said, As such, Thus, Hence, Notably

Replace with a direct sentence that carries the connection implicitly, short coordinating conjunctions (But, So, And, Yet, Still), or just a new paragraph break.

---

### 8. HEDGING — Commit When You Know Things
AI hedges everything:
- "It could be argued that..."
- "Some might say..."
- "In many ways..."
- "To a certain extent..."

If something is true, say it's true. Reserve hedges for genuine uncertainty.

**Hedged:** "In many ways, this approach could be considered more efficient."
**Direct:** "This approach cuts cycle time by roughly 30%."

---

### 9. THE RULE OF THREE — Break It
AI groups things in threes almost every time: "creative, smart, and determined." Use two things, or four, or one concrete detail instead. Break the rhythm.

---

### 10. FALSE RANGES — Delete Them
The "From X to Y" construction implies a spectrum but usually just lists two loosely related things:
- "From intimate gatherings to global movements..."
- "From ancient traditions to modern innovations..."

These sound comprehensive but say nothing. Delete them and state the actual claim.

---

### 11. SPECIFICITY — The Hardest Rule
AI regresses to the generic. The fix is specificity: real numbers, real names, concrete examples.
- Instead of "many experts agree," say which expert, or drop the attribution.
- Instead of "this has broad applications," name two actual applications.
- Instead of "throughout history," name the period or the event.
- Instead of "a significant improvement," say how much.

---

### 12. EDITORIAL COMMENTARY — Remove It
AI adds meta-commentary that narrates its own writing:
- "It is important to note that..."
- "No discussion of X would be complete without..."
- "What makes this particularly interesting is..."

These are filler. If something is important, put it in the text. If it's interesting, make it interesting.

---

### 13. PUNCTUATION — Em Dash Discipline
The em dash (—) is now a primary LLM identifier.

Rules:
- Use em dashes sparingly: one or two per page, max.
- Use commas, semicolons, colons, or parentheses where appropriate.
- Use en dashes (–) for ranges (2020–2025, 3–2), not hyphens.

---

## CHECKLIST before finishing any long piece

Before delivering output, scan for:

- [ ] Any word from the banned vocabulary list?
- [ ] More than one "It's not X, it's Y" construction?
- [ ] Three or more consecutive sentences of the same length?
- [ ] "In summary" / "In conclusion" / "Overall" used unnecessarily?
- [ ] "Furthermore" / "Moreover" / "Additionally" used more than once each?
- [ ] Any "From X to Y" false ranges?
- [ ] Any over-bolded phrases mid-paragraph?
- [ ] Any unearned superlatives or promotional adjectives?
- [ ] Any meta-commentary like "it is important to note"?
- [ ] More than two em dashes total?
- [ ] Does the opening start with "In today's..." or similar cliché?
- [ ] Does every paragraph end with a summary sentence?

Fix anything you find. One or two of these patterns is human. Seven of them is a robot.

---

*Sources: Wikipedia – Signs of AI Writing; The Augmented Educator; Beutler Ink; Blake Stockton; Sean Kernan; Hunting the Muse*

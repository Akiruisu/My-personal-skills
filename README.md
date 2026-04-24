# My Personal Skills

A curated collection of AI agent skills that extend the capabilities of LLM-based coding assistants. Each skill is a self-contained instruction set that teaches the agent a structured process for a specific task domain.

## Skills

### 🔒 Code Security Review

A structured security audit process modeled after professional penetration testing methodology. The agent assumes the role of a senior application security engineer and walks through a five-step workflow:

1. **Context discovery** — reads project manifests, follows imports, identifies the attack surface.
2. **Automated tooling** — runs language-specific scanners (`bandit`, `npm audit`, `cargo audit`, etc.) and pattern-based grep searches.
3. **Manual vulnerability scan** — checks against a 10-category taxonomy covering injection, broken auth, data exposure, access control, misconfig, outdated deps, insecure deserialization, crypto failures, SSRF/CSRF, and race conditions.
4. **Classification** — each finding gets a severity level (Critical → Informational), CWE ID, exploitability rating, and CVSS estimate where applicable.
5. **Structured report** — outputs a formatted audit with vulnerable code snippets, concrete fixes as diffs, OWASP/CWE references, and a prioritized action list.

Includes extended coverage for smart contracts (Solidity/Rust/Move), infrastructure-as-code (Terraform, Docker, k8s), SQL, and frontend-specific patterns.

**Directory structure:**

```
code-security-review/
├── SKILL.md                         # Main skill instructions
└── references/
    └── vuln-categories.md           # Extended vulnerability taxonomy
```

---

### ✍️ Write Like a Human

A set of 13 concrete rules that correct the statistical patterns making LLM-generated prose detectable. Sourced from Wikipedia's *Signs of AI Writing* page and corroborating research.

The rules target:

- **Vocabulary fingerprints** — a banned list of overused LLM words (*delve*, *tapestry*, *multifaceted*, etc.).
- **Promotional drift** — suppresses unearned superlatives and tourism-brochure adjectives.
- **Sentence rhythm** — enforces deliberate variation in sentence length and structure.
- **Structural clichés** — blocks essay-bot templates ("In today's fast-paced world…") and reflexive summary paragraphs.
- **Negative parallelisms** — limits the "It's not X, it's Y" construction.
- **Over-formatting** — reduces gratuitous bolding, bulleting, and emoji headings.
- **Transition overuse** — rotates or eliminates *furthermore*, *moreover*, *additionally*.
- **Hedging** — replaces vague qualifiers with direct statements.
- **Rule of three** — breaks the compulsive three-item grouping pattern.
- **False ranges** — cuts empty "from X to Y" constructions.
- **Specificity** — demands real numbers, names, and examples over generics.
- **Editorial commentary** — removes meta-narration ("it is important to note…").
- **Em dash discipline** — caps em dash usage at one or two per page.

Includes a pre-delivery checklist to scan output before finalizing.

**Directory structure:**

```
write-like-a-human/
└── SKILL.md                         # Main skill instructions
```

---

## Installation

Copy a skill directory into your agent's skill search path. The exact location depends on your setup, but a typical path looks like:

```
~/.agents/skills/<skill-name>/
```

Each skill folder must contain a `SKILL.md` file with YAML frontmatter (`name` and `description` fields) followed by the full instruction set in markdown.


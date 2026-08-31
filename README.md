# Personal Skills

Instruction sets that extend LLM coding assistants with structured workflows for specific engineering tasks.

## Skills

### 🔒 Code Security Review

A security audit process modeled after application security testing. The agent acts as a senior security engineer to inspect, scan, and report vulnerabilities across codebases.

Workflow:

1. **Context discovery**: inspects project manifests, import graphs, and entry points to identify attack surfaces.
2. **Automated scanning**: runs language scanners like `bandit`, `npm audit`, or `cargo audit`, alongside targeted pattern searches.
3. **Manual vulnerability scan**: checks against ten categories including injection, broken authentication, data exposure, access control failures, misconfigurations, outdated dependencies, insecure deserialization, cryptography failures, SSRF/CSRF, and race conditions.
4. **Classification**: assigns severity ratings (Critical to Informational), CWE IDs, exploitability ratings, and CVSS scores.
5. **Report generation**: produces findings with vulnerable code snippets, diff-formatted fixes, OWASP references, and prioritized remediation steps.

Covers smart contracts (Solidity, Rust, Move), infrastructure files (Terraform, Docker, Kubernetes), SQL queries, and frontend frameworks.

**Directory structure:**

```
code-security-review/
├── SKILL.md                         # Main skill instructions
└── references/
    └── vuln-categories.md           # Extended vulnerability taxonomy
```

---

### 🤿 Deep Dive

An investigation process for evaluating codebases, architecture choices, documentation, and technical designs. The agent examines primary source material to produce evidence-backed reports on system health, hidden risks, and concrete improvements.

Workflow:

1. **Scope and inventory**: sets clear investigation boundaries and inspects primary files, configurations, and tests.
2. **Evidence collection**: traces behavior across file boundaries and verifies claims against actual source implementation.
3. **Critical evaluation**: searches for architectural contradictions, invalid terminal states, and unsupported assumptions.
4. **Fact separation**: clearly separates observed facts, technical inferences, and open questions.
5. **Prioritized findings**: orders recommendations by actual risk and impact, pairing each issue with a concrete fix.
6. **Adaptive output**: exports reports as structured Markdown, standalone HTML pages, or direct conversational summaries.

**Directory structure:**

```
deepdive/
└── SKILL.md                         # Main skill instructions
```

---

### ✍️ Write Like a Human

A set of 13 rules that eliminate the statistical patterns that make AI-generated prose recognizable. Based on research and Wikipedia's guide on AI writing patterns.

The rules address:

- **Vocabulary fingerprints**: eliminates overused AI words like *delve*, *tapestry*, and *multifaceted*.
- **Promotional tone**: strips unearned superlatives and marketing speak.
- **Sentence rhythm**: alternates sentence length and structure to create natural cadence.
- **Structural clichés**: avoids template intros ("In today's fast-paced world...") and repetitive summary conclusions.
- **Negative parallelisms**: removes repetitive "It's not X, it's Y" phrasing.
- **Formatting**: cuts arbitrary bold text mid-sentence, unnecessary bullets, and emoji headings.
- **Overused transitions**: replaces repetitive connectors such as *furthermore*, *moreover*, and *additionally*.
- **Hedging**: replaces vague qualifiers with direct assertions.
- **Grouping patterns**: breaks the habit of listing items in threes.
- **False ranges**: removes empty "from X to Y" spans.
- **Specificity**: requires exact numbers, names, and concrete examples.
- **Meta-commentary**: removes self-referential phrases like "it is important to note".
- **Punctuation**: restricts em dashes to a maximum of two per document.

Includes a pre-delivery checklist to review prose before finalizing.

**Directory structure:**

```
write-like-a-human/
└── SKILL.md                         # Main skill instructions
```

---

## Installation

Clone this repository directly into your agent's skills directory:

```bash
git clone <repository-url> ~/.agents/skills
```

Alternatively, copy individual skill folders into your local skills directory:

```bash
cp -r deepdive ~/.agents/skills/
```

Each skill folder contains a `SKILL.md` file with YAML frontmatter (`name` and `description`) followed by instruction steps.

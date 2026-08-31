---
name: deepdive
description: Use when a user asks for an in-depth analysis, deep dive, architecture or documentation critique, subject investigation, findings report, or an evidence-backed assessment of strengths, weaknesses, contradictions, risks, and improvements.
---

# Deep Dive

## Purpose

Investigate a subject far enough to explain what works, what does not, why it matters, and what should happen next.

**Core principle:** inspect first, connect evidence across sources, then turn findings into decisions.

## Boundaries

- Analysis only by default. Do not modify the reviewed source, implementation, configuration, or documentation.
- Report artifacts are allowed after stating a brief plan and target paths, subject to the user's approval rules.
- If the user later requests implementation, treat it as a separate task with its own plan and approval.
- Use specialized security, accessibility, debugging, or library-reference skills alongside this one when the subject requires them.

## Process

1. **Set scope.** Identify the subject, audience, decision being supported, expected depth, source boundaries, and output needs. Ask only for information that cannot be discovered safely.
2. **Inventory sources.** Inspect relevant files, code, documentation, configuration, tests, history, and external references. Do not assume paths, dependencies, behavior, or implementation status.
3. **Frame questions.** List the claims and boundaries that need testing: purpose, internal consistency, feasibility, failure modes, trust boundaries, maintainability, usability, and missing decisions. When judging implementation readiness, require clear scope, a named canonical source for each decision, interface contracts, edge-case behavior, suitable acceptance evidence (such as tests, observed behavior, traceable criteria, citations, or explicit approval), and no unresolved blocker.
4. **Gather evidence.** Read primary sources before commentary. Trace related concepts across files or sources. Compare stated behavior with implementation when implementation exists.
5. **Challenge the first reading.** Look for contradictions, hidden assumptions, invalid terminal states, duplicated responsibilities, claims broader than evidence, and features whose costs exceed their value.
6. **Separate certainty.** Distinguish verified facts, reasoned inferences, opinions, and unresolved questions. Never present an inference as observed behavior.
7. **Synthesize.** Explain strengths worth preserving, weaknesses, risks, unnecessary material, missing contracts, concrete revisions, and tradeoffs.
8. **Prioritize naturally.** Order findings from most important to least important based on consequence, urgency, dependency, and decision value. Use labels such as Critical/High/Medium/Low or P0–P3 only when they genuinely help; never force every subject into a rigid severity scheme.
9. **Verify the report.** Check source citations, internal consistency, output paths, links, claims, and generated HTML or Markdown before completion.

## Evidence Rules

- Cite repository evidence with project-relative paths and line numbers when available.
- Link external sources and state when information may be time-sensitive.
- Prefer primary documentation, specifications, source code, tests, and observed command output.
- Explain why each problem matters; do not produce a list of vague objections.
- Pair criticism with a concrete change, expected benefit, and material tradeoff.
- Report conflicting evidence rather than silently choosing the convenient source. If authority is not declared, do not invent it; identify the conflict and recommend one canonical artifact, specification, system of record, or accountable decision-maker.
- State validation limits and unavailable evidence.

## Adaptive Output

Choose the smallest format that serves the audience:

| Need | Output |
|---|---|
| Technical reference, codebase handoff, later LLM use | Markdown |
| Human review, prioritization, presentation | Self-contained HTML |
| Findings will guide both humans and later agents | Both |
| User names a format | Use that format |
| User forbids files or a short investigation needs no artifact | Chat only |

When creating files and no path is specified, use:

```text
docs/deepdives/YYYY-MM-DD-<subject-slug>-deepdive.md
docs/deepdives/YYYY-MM-DD-<subject-slug>-deepdive.html
```

Build `<subject-slug>` from a short subject name: lowercase ASCII letters and numbers, replace other runs with one hyphen, and trim leading or trailing hyphens.

Create only the selected format or formats. When artifacts are created, give a concise chat summary with artifact links.

## Report Contract

Adapt section size to the subject; omit empty sections. A full report normally includes:

1. Scope, sources, and limitations
2. Executive verdict
3. Subject map or current-state explanation
4. Strong decisions or qualities worth preserving
5. Findings ordered by importance
6. For each finding: problem, evidence, impact, proposed change, and tradeoff or uncertainty
7. Contradictions, hidden assumptions, and unresolved questions
8. What to revise, remove, merge, simplify, or leave unchanged
9. Prioritized action sequence and dependencies
10. LLM handoff containing stable decisions, invariants, open questions, and source ownership

Do not inflate a small investigation to fill this outline.

## Markdown Contract

- Use clear headings and compact tables only when they improve comparison.
- Keep citations close to claims.
- Make the LLM handoff structured and concise; YAML is suitable but not mandatory.
- Keep the Markdown useful without the HTML report.

## HTML Contract

- Produce one semantic HTML file with embedded CSS and, if used, embedded JavaScript.
- Use no remote fonts, frameworks, images, analytics, or network dependencies.
- Keep all content readable when JavaScript is disabled.
- Favor an editorial report over a generic dashboard.
- Provide responsive and print styles, visible focus states, sufficient contrast, and reduced-motion support.
- JavaScript must remain optional and small. Appropriate uses include filtering, navigation, expansion, and printing.
- Arrange findings from most important to least important and show the problem each proposal addresses.
- Link back to local source documents where useful.

## Common Failures

- **Premature opinion:** commenting before reading the source set. Inspect first.
- **File-by-file summary:** describing documents independently without tracing shared concepts. Analyze across boundaries.
- **Severity theater:** assigning dramatic labels without consequence or urgency. Rank by actual decision value.
- **Generic advice:** saying “improve security” or “add tests” without a failure mode and concrete change.
- **Scope escape:** redesigning the product instead of addressing the requested subject.
- **Parallel sources of truth:** letting an HTML proposal become a second normative specification. Identify one owner for accepted decisions.
- **Unrequested implementation:** changing reviewed material during analysis. Stop at findings and proposals.
- **Decorative HTML:** adding visual complexity that weakens reading, printing, accessibility, or self-containment.

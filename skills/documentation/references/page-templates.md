# Page Templates

Per-doc-type page structures, front matter schema, and archetype patterns.

## Table of contents

1. [Front matter schema](#front-matter-schema)
2. [Page templates by doc type](#page-templates-by-doc-type)
3. [Validation rules summary](#validation-rules-summary)

---

## Front matter schema

Every documentation page must have front matter with at minimum the required fields below.
The specific format (YAML, TOML, JSON) depends on your documentation platform.

### Required fields

| Field | Type | Purpose | Rules |
|-------|------|---------|-------|
| `title` | string | Human-readable page title | Sentence case. Must match the H1 on the page. |
| `description` | string | SEO meta description + in-site summaries | Must be unique across the site. 50-160 characters. Describe what the reader will accomplish or learn. |
| `docType` | enum | Content model classification | One of: `quickstart`, `tutorial`, `concept`, `howto`, `reference`, `troubleshooting` |

### Recommended fields

| Field | Type | Purpose | Rules |
|-------|------|---------|-------|
| `weight` | integer | Menu/nav ordering | Lower numbers sort first. Use multiples of 10 (10, 20, 30) to allow insertions. |
| `roles` | string[] | Persona targeting for filtering | Values defined by the project (e.g., `["ve", "team-lead", "admin"]`). |
| `lastVerified` | date | Content freshness indicator | ISO date (YYYY-MM-DD). Means "a human confirmed this is still accurate." Distinct from git commit date. |
| `prerequisites` | string[] | Required prior knowledge or setup | Paths or descriptions. Rendered by templates into a prerequisites section. |
| `tags` | string[] | Cross-cutting topic labels | Lightweight labels for related-content features. Don't duplicate taxonomy values. |
| `aliases` | string[] | Redirect from old URLs | Required whenever a page URL changes during restructuring. |

### Project-specific taxonomy fields

For documentation sites serving multiple user roles or workflows, define taxonomy fields that
answer "Which instructions apply to me?":

| Field | Type | Purpose | Example values |
|-------|------|---------|---------------|
| `roles` | string[] | Who this page is for | `"ve"`, `"team-lead"`, `"vec"`, `"admin"` |
| `modalities` | string[] | Which workflow mode applies | `"in-person-paper"`, `"in-person-digital"`, `"remote"` |
| `environments` | string[] | Which environment applies | `"production"`, `"sandbox"`, `"staging"` |

### Sample front matter (YAML)

```yaml
---
title: "Create your first exam session"
description: "Set up a new exam session, assign volunteer examiners, and verify everything is ready for candidates. Takes about 5 minutes."
docType: "quickstart"
roles: ["team-lead"]
modalities: ["in-person-digital", "remote"]
environments: ["production", "sandbox"]
lastVerified: "2026-03-15"
weight: 10
aliases:
  - /docs/old-path/create-session/
tags: ["sessions", "setup"]
prerequisites:
  - "An active team lead account"
  - "[Install ExamTools](/docs/getting-started/install/)"
---
```

---

## Page templates by doc type

Each template defines the **required sections in order**, optional sections, and validation
checks. If your documentation platform supports archetypes or content templates, encode these
as one template per doc type so new pages start with the correct structure.

### Quickstart template

```markdown
# [Goal verb phrase — matches title]

[1-2 sentence goal statement: what you'll accomplish and why it matters.]

**Time:** ~[X] minutes

## Prerequisites

- [Prerequisite 1 with link if applicable]
- [Prerequisite 2]

## Steps

### Step 1: [Verb phrase]

[Instruction.]

### Step 2: [Verb phrase]

[Instruction.]

### Step 3: [Verb phrase]

[Instruction.]

## Verify

[How to confirm it worked. Be specific: "You should see X" or "Run Y and confirm Z."]

## Next steps

- [Link to logical next action 1]
- [Link to logical next action 2]
- [Link to related how-to or tutorial]
```

**Validation rules:**
- Must include a time estimate near the top of the page.
- Must include a "Verify" section with specific observable success criteria.
- Must include "Next steps" with 2-5 links.
- Must have fewer than 10 steps.
- Should be under 900 words. If it's longer, evaluate whether it should be a tutorial.

---

### Tutorial template

```markdown
# [Descriptive scenario title]

[Scenario: Describe the real-world situation the reader will work through. 2-3 sentences.]

## What you'll learn

- [Learning outcome 1]
- [Learning outcome 2]
- [Learning outcome 3]

## Prerequisites

- [Prerequisite 1]
- [Prerequisite 2]

## Step 1: [Verb phrase]

[Instruction with brief explanation of WHY this step matters.]

> **Checkpoint:** At this point, you should see [observable result].

## Step 2: [Verb phrase]

[Instruction with brief explanation.]

> **Checkpoint:** Verify that [thing] is working by [doing action].

## Step 3: [Verb phrase]

[Instruction.]

## Recap

You've now completed [summary]. Here's what you learned:

- [Key takeaway 1]
- [Key takeaway 2]

## Next steps

- [Link to next tutorial in the series]
- [Link to related how-to for a specific task from this tutorial]
- [Link to concept page for deeper understanding]
```

**Validation rules:**
- Must include at least 2 checkpoints (inline verification moments).
- Must include a "What you'll learn" or equivalent overview.
- Must include a "Recap" or "What you learned" section.
- Must include "Next steps" with 2-5 links.
- Steps should include brief explanatory context — this is what differentiates
  a tutorial from a how-to.

---

### How-to guide template

```markdown
# [Verb phrase: "Configure X" / "Add Y to Z"]

[1-2 sentence intro: what this task accomplishes and when you'd do it.]

## Prerequisites

- [Prerequisite 1]
- [Prerequisite 2]

## Steps

### Step 1: [Verb phrase]

[Imperative instruction.]

### Step 2: [Verb phrase]

[Imperative instruction.]

## Verify

[How to confirm the task is complete. Be specific.]

## Troubleshooting

[Optional: 1-2 common problems specific to this task.]

## Related guides

- [Link to related how-to 1]
- [Link to related how-to 2]
```

**Validation rules:**
- Title must start with a verb.
- Intro must be 1-2 sentences maximum.
- Steps must use imperative mood (start with a verb).
- Must include a "Verify" section.
- Must not contain more than 2 paragraphs of explanatory prose between steps.
  If more explanation is needed, extract it to a concept page and link to it.

---

### Concept / Explanation template

```markdown
# [Noun phrase: "Session lifecycle" / "Permission model"]

[Opening paragraph: What this concept is and why the reader should care. 2-4 sentences.]

## How it works

[Explanation with at least one diagram (Mermaid preferred) or structured model.]

## Key terms

| Term | Definition |
|------|-----------|
| [Term 1] | [Definition] |
| [Term 2] | [Definition] |

## Limits and considerations

[Constraints, edge cases, common misconceptions.]

## Related tasks

- [Link to how-to that uses this concept]
- [Link to quickstart that touches this concept]
- [Link to reference for detailed specs]
```

**Validation rules:**
- Must NOT contain numbered procedural steps. If it has steps, extract them to a how-to.
- Must include at least one diagram, table, or structured model.
- Must include links to related task-oriented pages ("Related tasks").
- Title should be a noun phrase, not a verb phrase.

---

### Reference template

```markdown
# [Noun phrase: "Session fields" / "API endpoints"]

[1-2 sentence scope statement: what this reference covers.]

## [Section organized by logical grouping]

| Field/Parameter | Type | Required | Default | Description |
|----------------|------|----------|---------|-------------|
| [field] | [type] | [yes/no] | [default] | [description] |

## Constraints

[Limits, validation rules, edge cases.]

## Examples

[Minimal, focused examples. One per common use case.]

## See also

- [Link to concept page explaining the design]
- [Link to how-to that uses these fields]
```

**Validation rules:**
- Must NOT contain narrative onboarding or tutorial content.
- Tables must include type and description columns at minimum.
- Must have stable anchor IDs for deep linking.
- Language must be precise and unambiguous — no "various" or "several."

---

### Troubleshooting template

```markdown
# Troubleshoot [area]

## [Symptom description as heading]

**Symptoms:** [What the user sees — error message, unexpected behavior.]

**Cause:** [Why this happens.]

**Fix:**

1. [Step 1]
2. [Step 2]

**Verify:** [How to confirm the fix worked.]

---

## [Next symptom as heading]

[Repeat pattern for each problem.]

## Get help

[Escalation path: where to ask for help, how to file a report, contact info.]
```

**Validation rules:**
- Must be organized by **symptom**, not by cause. Users search by what they see, not by
  what's wrong internally.
- Each problem must have: symptom, cause, fix steps, and a verification step.
- Must include an escalation/get-help section.
- Symptom headings should use the reader's language ("Session won't start") not internal
  language ("WebSocket connection timeout on session init").

---

## Validation rules summary

All validation rules consolidated for agent-driven review:

| Check | Applies to | Severity |
|-------|-----------|----------|
| `docType` field present and valid | All pages | Error |
| `title` matches H1 | All pages | Error |
| `description` is unique and 50-160 chars | All pages | Warning |
| No skipped heading levels | All pages | Error |
| Only one H1 per page | All pages | Error |
| Page opens with context sentence (what + who) | All pages | Warning |
| Ends with outbound links (Next steps / Related / See also) | All pages | Warning |
| "Verify" section exists with specific criteria | quickstart, howto, tutorial | Error |
| "Next steps" section exists with 2-5 links | quickstart, howto, tutorial | Error |
| Time estimate present | quickstart | Warning |
| Steps use imperative verbs | quickstart, howto | Warning |
| Under 900 words | quickstart | Info |
| No explanation blocks >2 paragraphs | howto | Warning |
| Intro is ≤2 sentences | howto | Warning |
| At least 2 checkpoints | tutorial | Warning |
| "Recap" section exists | tutorial | Warning |
| No numbered procedural steps | concept | Warning |
| At least one diagram or structured model | concept | Warning |
| Organized by symptom (not cause) | troubleshooting | Warning |
| Each problem has symptom + cause + fix + verify | troubleshooting | Error |
| Escalation section exists | troubleshooting | Warning |
| `lastVerified` within 6 months | All pages | Info |
| `aliases` present if URL was changed | Moved pages | Error |
| No banned words (see writing-style.md) | All pages | Warning |

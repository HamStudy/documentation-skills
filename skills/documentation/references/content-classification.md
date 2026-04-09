# Content Classification

How to classify documentation pages by type, detect mixed-purpose pages, and decide when to
split or merge content.

## Table of contents

1. [The six doc types](#the-six-doc-types)
2. [Classification decision tree](#classification-decision-tree)
3. [Structural signals for classification](#structural-signals-for-classification)
4. [Anti-patterns by type](#anti-patterns-by-type)
5. [When to split a page](#when-to-split-a-page)
6. [When to merge pages](#when-to-merge-pages)

---

## The six doc types

Built on the Diátaxis framework (tutorials, how-to guides, reference, explanation) plus two
operational additions (quickstart, troubleshooting) validated by GitHub Docs, Kubernetes,
and other major documentation systems.

### Quickstart

- **Purpose:** Enable completion of a focused task in minutes — fast first value.
- **Audience:** New users who want immediate progress; evaluators.
- **User's question:** "How do I get started right now?"
- **Success criterion:** Reader finishes in ~5 minutes and can verify it worked.
- **Structure:** Goal statement → Prerequisites → Minimal steps → Verify → Next steps.
- **Tone:** Encouraging, concise, momentum-focused.
- **Length guideline:** 400–900 words. If it's longer, it's becoming a tutorial.

### Tutorial

- **Purpose:** Teach by guiding through a complete workflow; build understanding.
- **Audience:** Learners; users switching from another tool.
- **User's question:** "Can you teach me how this works?"
- **Success criterion:** Reader completes an end-to-end workflow and understands why steps matter.
- **Structure:** Scenario → Prerequisites → Guided steps with checkpoints → Recap → Next steps.
- **Tone:** Conversational, patient, explanatory. Author chooses the path.
- **Length guideline:** 1000–3000 words. Include at least 2 checkpoint moments.

### How-to guide

- **Purpose:** Help a capable user accomplish a specific real-world task.
- **Audience:** Users "at work" who already know the basics.
- **User's question:** "How do I do X?"
- **Success criterion:** Task completed successfully; page is skimmable.
- **Structure:** 1–2 sentence intro → Prerequisites → Steps → Verify → Related guides.
- **Tone:** Direct, efficient, imperative. Assume competence.
- **Length guideline:** 300–1500 words. No teaching — link to tutorials/concepts instead.

### Concept / Explanation

- **Purpose:** Build mental models; explain what, why, and how at appropriate depth.
- **Audience:** New and intermediate users; decision makers.
- **User's question:** "Why does it work this way?" / "What is X?"
- **Success criterion:** Reader can explain the concept and navigate to related tasks.
- **Structure:** What it is → Why it matters → How it works (diagram) → Vocabulary → Limits/pitfalls → Related tasks.
- **Tone:** Thoughtful, clear, uses analogies. Not tied to any specific task.
- **Length guideline:** 500–2000 words. Must include at least one diagram or structured model.

### Reference

- **Purpose:** Provide authoritative, structured facts about the system.
- **Audience:** Experienced users; integrators; support staff.
- **User's question:** "What exactly does X do?" / "What are the valid values for Y?"
- **Success criterion:** User finds the exact answer quickly; content is complete and unambiguous.
- **Structure:** Scope → Definitions → Tables/fields/options → Constraints → Examples (minimal).
- **Tone:** Precise, austere, factual. No narrative onboarding.
- **Length guideline:** Variable — completeness over brevity.

### Troubleshooting

- **Purpose:** Diagnose and fix problems.
- **Audience:** Users stuck mid-task; support staff.
- **User's question:** "Something went wrong — how do I fix it?"
- **Success criterion:** User resolves the issue or knows the escalation path.
- **Structure:** Symptoms → Likely causes → Fix steps → Confirm fix → Prevent recurrence → Escalate.
- **Tone:** Empathetic but efficient. Symptom-first, not cause-first.
- **Length guideline:** 200–800 words per problem. Group related problems on one page.

---

## Classification decision tree

Use this decision tree to classify any documentation page. Work through it top to bottom.

```
1. Does the page primarily describe HOW TO FIX a problem?
   → Yes: TROUBLESHOOTING

2. Does the page primarily list facts, parameters, fields, API shapes, or settings?
   → Yes: REFERENCE

3. Does the page primarily explain WHY something works a certain way, without
   walking the reader through steps?
   → Yes: CONCEPT / EXPLANATION

4. Does the page walk the reader through steps?
   a. Is it designed for a brand-new user to get a first result in <10 minutes?
      → Yes: QUICKSTART
   b. Does it teach a concept by guiding through a complete workflow with checkpoints?
      → Yes: TUTORIAL
   c. Does it help an experienced user accomplish a specific task?
      → Yes: HOW-TO GUIDE

5. If none of the above clearly fits:
   → The page likely mixes types and needs to be split.
```

---

## Structural signals for classification

Use these signals to detect doc type from page content, even when the page lacks metadata:

| Signal | Likely type |
|--------|-------------|
| Numbered steps with a "verify" section | Quickstart or How-to |
| Numbered steps with explanatory paragraphs between them | Tutorial |
| Numbered steps with NO explanatory paragraphs | How-to |
| Time estimate ("~5 minutes") near the top | Quickstart |
| Tables of parameters, fields, or options | Reference |
| "Why" or "How it works" headings with no steps | Concept |
| Headings like "Error:", "Problem:", "If you see..." | Troubleshooting |
| Frequent use of "you will learn" or "by the end of this" | Tutorial |
| Page is >2000 words and has both steps AND parameter tables | Mixed — split it |
| Page title starts with a verb ("Create", "Configure", "Set up") | How-to or Quickstart |
| Page title starts with a noun ("Sessions", "Permissions", "Architecture") | Concept or Reference |
| Extensive prose paragraphs explaining design decisions | Concept |

---

## Anti-patterns by type

When reviewing a page, check for these type-specific anti-patterns:

### Quickstart anti-patterns
- Turns into a tutorial with long explanations between steps
- Includes exhaustive options or edge cases (should be in how-to or reference)
- Missing verification step ("how do I know it worked?")
- No time estimate
- More than ~10 steps (too complex for a quickstart)

### Tutorial anti-patterns
- Looks like reference (too many tables, no narrative)
- Assumes too much prior knowledge (no prerequisites section)
- Missing checkpoints — reader has no way to verify progress
- No "what you learned" summary at the end
- Jumps between unrelated concepts without a connecting narrative

### How-to anti-patterns
- Becomes a tutorial (too much teaching; explains "why" at length)
- Becomes reference (lists "all possible settings" instead of showing the task)
- Intro is more than 2 sentences
- Steps use passive voice instead of imperative verbs
- No verification step

### Concept anti-patterns
- Contains step-by-step procedures (move those to a how-to)
- Contains "click this, then click that" UI sequences (move to how-to)
- Duplicates reference tables (link to reference instead)
- Missing diagrams or structured models — concept pages need visual aids
- No links to related task-oriented pages

### Reference anti-patterns
- Includes narrative onboarding ("Welcome to the X API!")
- Uses vague language ("various options are available")
- Hides key facts in prose instead of structured tables
- Missing field/parameter types, constraints, or defaults
- Examples are too complex — reference examples should be minimal

### Troubleshooting anti-patterns
- Organized by cause rather than symptom (users don't know the cause)
- Generic advice ("try restarting") without connecting to specific symptoms
- Missing "confirm fix" step — user can't verify the problem is resolved
- Solutions are far from the procedures that cause the problem (should be inline or linked)

---

## When to split a page

Split a page when any of these conditions are true:

1. **Mixed doc types.** The page contains both procedural steps AND extensive conceptual
   explanation, or both reference tables AND tutorial narrative. Extract each type into its
   own page and cross-link.

2. **Multiple unrelated tasks.** The page covers "how to create X" AND "how to delete X" AND
   "how to configure X" — each should be its own how-to page.

3. **Page exceeds 2500 words** and covers multiple topics. Long pages are acceptable for
   single-topic reference or comprehensive tutorials, but not for grab-bag content.

4. **Multiple audiences.** The page addresses both end-users and administrators with different
   instructions for each. Split by audience.

5. **The table of contents has more than 8 H2 headings.** This usually indicates the page
   covers too much ground.

### How to split

1. Identify the distinct doc types or topics on the page.
2. Create a new page for each extracted section with its own front matter.
3. On the original page, replace extracted content with a brief summary and link.
4. Set up redirects from old anchor URLs if they were linkable.
5. Ensure all new pages have "Next steps" linking to each other and to the original.

---

## When to merge pages

Merge pages when:

1. **Two pages cover the same task** with slightly different wording (duplication).
2. **A page is too thin** — under 150 words with no meaningful standalone value.
3. **Sequential how-to pages** that are always done together could be one page
   (but only if the combined page stays under ~1500 words).

When merging, choose the URL with higher traffic or more inbound links as the survivor and
set up redirects for the retired URL.

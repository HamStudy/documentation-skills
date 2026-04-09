---
name: documentation
description: >
  Skill for writing, structuring, reviewing, and reformatting technical documentation.
  Use this skill whenever the user asks to write new documentation pages, restructure or
  reorganize existing docs, review documentation quality, rewrite docs for clarity or
  readability, classify documentation by type (tutorial, how-to, reference, etc.), create
  or enforce documentation templates, audit documentation for gaps or staleness, improve
  documentation navigation or information architecture, add or fix front matter metadata,
  or apply style/tone rules to documentation. Also trigger when the user mentions Diátaxis,
  doc types, content audits, documentation linting, Vale rules, or any work on a docs site.
  If the user is working on markdown files that are clearly documentation (not READMEs or
  code comments), use this skill.
---

# Documentation Restructure Skill

A complete system for writing, classifying, structuring, reviewing, and reformatting
technical documentation. Built on the Diátaxis framework, informed by patterns from
best-in-class documentation sites (Stripe, Django, Kubernetes, GitLab, GitHub Docs, Twilio,
DigitalOcean), and platform-agnostic — applicable to any static site generator, wiki, or
documentation system.

## Table of contents

1. [Core workflow](#core-workflow)
2. [Reference files](#reference-files)
3. [Task routing](#task-routing)
4. [Key principles](#key-principles)

---

## Core workflow

Every documentation task follows this sequence. Skip steps that don't apply, but always
**classify first**.

### Step 1: Classify the page

Before writing or editing, determine the page's **doc type** using the Diátaxis framework.
Read `references/content-classification.md` for the full classification rules and decision tree.

The six doc types are: **Quickstart**, **Tutorial**, **How-to**, **Concept/Explanation**,
**Reference**, **Troubleshooting**. Every page must be exactly one type. If a page mixes types,
it must be split.

### Step 2: Apply the template

Each doc type has a required page structure (heading order, mandatory sections, front matter).
Read `references/page-templates.md` for the per-type templates and front matter schema.

### Step 3: Write or rewrite for clarity

Apply the writing style rules: active voice, second person, present tense, conditions before
instructions, plain language, scannable formatting.
Read `references/writing-style.md` for the complete rule set with examples.

### Step 4: Ensure navigation and cross-linking

Every page must be reachable, linked, and positioned in the site hierarchy.
Read `references/navigation-structure.md` for information architecture rules.

### Step 5: Quality check

Run through the quality checklist: accessibility, SEO, linting, link integrity.
Read `references/quality-linting.md` for the full checklist and tooling.

---

## Reference files

Read the relevant reference file(s) **before** starting work. Most tasks require 1-2 files,
not all of them.

| File | When to read it |
|------|----------------|
| `references/content-classification.md` | Classifying pages, deciding whether to split/merge, auditing doc types |
| `references/writing-style.md` | Writing new content, rewriting existing content, reviewing prose quality |
| `references/page-templates.md` | Creating new pages, restructuring existing pages, normalizing front matter |
| `references/navigation-structure.md` | Reorganizing site hierarchy, fixing navigation, adding cross-links, building landing pages |
| `references/auditing-migration.md` | Running content audits, planning a restructure, identifying gaps, prioritizing rewrites |
| `references/quality-linting.md` | Setting up CI, configuring Vale/markdownlint, accessibility review, SEO checks |

---

## Task routing

Use this table to determine which reference files to read for common tasks:

| Task | Read these files |
|------|-----------------|
| "Write a new doc page" | content-classification → page-templates → writing-style |
| "Rewrite this page for clarity" | content-classification → writing-style |
| "Restructure the whole docs site" | auditing-migration → content-classification → navigation-structure |
| "Review this documentation" | content-classification → writing-style → quality-linting |
| "Add front matter to these pages" | page-templates |
| "Set up docs linting" | quality-linting |
| "Create a getting started guide" | content-classification → page-templates → writing-style |
| "Fix the navigation / sidebar" | navigation-structure |
| "Audit the docs for gaps" | auditing-migration → content-classification |
| "Split this page — it's too long" | content-classification → page-templates |
| "Make this page more scannable" | writing-style |

---

## Key principles

These principles override all other guidance when in conflict:

1. **Every page has exactly one doc type.** Mixed-purpose pages are the #1 cause of
   hard-to-navigate docs. Split ruthlessly.

2. **Users arrive at any page from search.** Every page must establish its own context in the
   first paragraph — state what the page covers and who it's for. Never assume prior reading.
   (This is the "Every Page is Page One" principle.)

3. **Action before explanation.** For procedural content (quickstarts, how-tos, tutorials),
   lead with what to do. Link to explanations; don't inline them.

4. **Write for the reader who is stuck.** Most documentation readers are not reading for fun —
   they have a task, they're blocked, and they need to get unblocked. Optimize for that.

5. **Front matter is infrastructure.** Consistent, complete metadata enables navigation,
   search, filtering, and automated quality checks. Treat it as seriously as code.

6. **Verify steps are not optional.** Every procedural page must include a verification step
   so the reader can confirm they did it right before moving on.

7. **Next steps prevent dead ends.** Every page must end with links to logical next actions.
   A page with no outbound links is a dead end.

8. **Consistency compounds.** Consistent structure, terminology, voice, and formatting across
   all pages is more valuable than any individual page being perfect.

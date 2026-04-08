# Auditing and Migration

How to audit existing documentation, identify gaps and problems, plan a restructure, and
execute the migration incrementally.

## Table of contents

1. [Content inventory](#content-inventory)
2. [Content assessment](#content-assessment)
3. [Gap analysis](#gap-analysis)
4. [Migration planning](#migration-planning)
5. [Prioritization framework](#prioritization-framework)
6. [Agent task checklist](#agent-task-checklist)

---

## Content inventory

Before restructuring anything, build a complete picture of what exists. The content inventory
is a catalog of every page with metadata.

### How to build the inventory

1. **Crawl the site** or enumerate the content directory. For every page, collect:

| Field | Source | Purpose |
|-------|--------|---------|
| URL / file path | File system or crawler | Unique identifier |
| Title | Front matter or H1 | What the page claims to cover |
| Word count | Text extraction | Size / scope indicator |
| Last modified date | Git history or front matter | Staleness indicator |
| Current docType (if any) | Front matter | Existing classification |
| Assigned docType | Agent analysis | Correct classification per Diátaxis |
| Topic area | Manual / agent | What feature or workflow this covers |
| Audience / roles | Front matter or inference | Who this page is for |
| Inbound link count | Link analysis | How discoverable is this page |
| Status | Assessment | Keep / Update / Merge / Split / Remove |

2. **Enrich with analytics** if available:
   - Page views (last 90 days)
   - Bounce rate
   - Average time on page
   - Search queries that land on this page

3. **Output as a spreadsheet or structured data** (CSV, JSON) for sorting and filtering.

### Inventory shortcuts for agents

When working programmatically with a documentation repository:

- List all markdown files recursively from the content directory.
- Parse front matter from each file to extract metadata.
- Count words in the body (exclude front matter and code blocks).
- Extract all internal links to build a link graph.
- Identify orphan pages (pages with zero inbound links from other doc pages).

---

## Content assessment

Assess each page against six criteria. Score each as Good / Needs Work / Poor:

### 1. Accuracy
- Is the information correct and current?
- Do screenshots match the current UI?
- Do code examples work?
- Has the feature changed since this was written?

### 2. Completeness
- Does the page cover everything its title promises?
- Are there obvious gaps (mentioned but unexplained features, steps that skip details)?
- Are prerequisites listed?
- Is there a verification step (for procedural content)?

### 3. Clarity
- Can a reader in the target audience follow this without confusion?
- Are sentences short and direct?
- Is jargon defined or avoided?
- Are conditions stated before instructions?

### 4. Type purity
- Does this page have exactly one doc type?
- Does it mix explanation with procedures, or reference tables with tutorials?
- See `content-classification.md` for the decision tree.

### 5. Structure
- Does the page follow the template for its doc type?
- Are headings in the correct order?
- Does it have the required sections (prerequisites, verify, next steps)?
- Is front matter complete?

### 6. Discoverability
- Does this page have inbound links from other pages?
- Is it in the correct section of the navigation?
- Does its title and description match what users would search for?
- Does it end with outbound links (next steps, related content)?

### Assign a status

Based on the assessment, assign each page one of:

| Status | Meaning | Action |
|--------|---------|--------|
| **Keep** | Page is accurate, well-structured, and correctly classified | No changes needed (maybe minor style fixes) |
| **Update** | Content is correct but needs style/structure improvements | Rewrite in place following templates |
| **Split** | Page mixes doc types or covers too many topics | Create new pages, redistribute content, add redirects |
| **Merge** | Page is a thin duplicate of another page | Combine with the stronger page, add redirect |
| **Remove** | Page is outdated, inaccurate, or duplicated | Archive or delete, add redirect to best alternative |
| **Create** | Gap identified — this page doesn't exist but should | Write new page following templates |

---

## Gap analysis

After assessing existing pages, identify what's missing.

### Diátaxis coverage map

For each major topic area or feature, check which doc types exist:

| Topic | Quickstart | Tutorial | How-to | Concept | Reference | Troubleshooting |
|-------|-----------|----------|--------|---------|-----------|----------------|
| Sessions | ? | ? | ? | ? | ? | ? |
| User management | ? | ? | ? | ? | ? | ? |
| Exam administration | ? | ? | ? | ? | ? | ? |
| ... | | | | | | |

Mark each cell as: **Exists**, **Exists but needs rewrite**, or **Missing**.

**Common gaps in engineer-written docs:**
- Quickstarts are almost always missing or are actually tutorials in disguise.
- How-to guides are often mixed with explanation (concept content inline with steps).
- Troubleshooting is scattered across other pages instead of organized by symptom.
- Reference is often the most complete section (engineers write what they know).

### Additional gap sources

- **Support tickets / forum questions:** If users repeatedly ask how to do something, that's
  a missing how-to or a hard-to-find one.
- **Search queries with zero results:** Content that users want but can't find.
- **Onboarding friction:** If new users consistently get stuck at the same point, there's
  a gap in the getting-started flow.
- **Feature changelog:** Features added or changed since docs were last updated.

---

## Migration planning

### Strangler Fig pattern

Don't rewrite everything at once. Use the Strangler Fig pattern — build new content alongside
old content, redirect incrementally, and retire old pages over time.

### Recommended phases

| Phase | Focus | Deliverables |
|-------|-------|-------------|
| **1. Foundation** | Getting Started experience | New quickstart pages, landing page, role-based entry points |
| **2. Core workflows** | How-to guides for the most common tasks | Task-oriented pages with verify + next steps |
| **3. Concepts** | Explanation pages for key concepts | Diagrams, mental models, extracted from existing mixed pages |
| **4. Reference** | Reference documentation cleanup | Consistent tables, complete field docs, stable anchors |
| **5. Troubleshooting** | Symptom-organized troubleshooting | Consolidated from scattered tips across existing pages |
| **6. Cleanup** | Redirects, orphan removal, navigation polish | All old URLs redirect, no dead ends, sidebar finalized |

### Within each phase

1. **Identify pages in scope** from the content inventory.
2. **Classify each page** using the decision tree in `content-classification.md`.
3. **Apply the template** from `page-templates.md`.
4. **Rewrite for clarity** using `writing-style.md`.
5. **Set up redirects** from old URLs.
6. **Update cross-links** in other pages that referenced the old content.
7. **Validate** with the quality checklist in `quality-linting.md`.

---

## Prioritization framework

When deciding which pages to rewrite first, use this prioritization matrix:

### Priority tiers

**Tier 1 — Rewrite first (highest impact):**
- Getting Started / Quickstart pages (first-touch experience for new users)
- Pages with high traffic AND high bounce rate or support ticket correlation
- Pages that are completely wrong doc type (e.g., a "quickstart" that's actually reference)

**Tier 2 — Rewrite next:**
- How-to guides for the most common user tasks
- Pages with high traffic that need structure/style improvements
- Mixed-type pages that need splitting

**Tier 3 — Rewrite when possible:**
- Concept pages that need diagrams or restructuring
- Reference pages that need consistent formatting
- Low-traffic pages with minor issues

**Tier 4 — Backlog:**
- Pages that are accurate but could be clearer
- Style-only improvements (terminology consistency, voice, formatting)
- Pages that will be affected by upcoming product changes (defer until after the change)

### Scoring formula (if you want to quantify)

```
Priority score = (Traffic × 3) + (Support tickets × 5) + (Type mismatch × 4) +
                 (Missing verify/next-steps × 2) + (Staleness × 1)
```

Where each factor is scored 0-3 (none, low, medium, high).

---

## Agent task checklist

When an agent is tasked with auditing or restructuring documentation, execute these tasks
in order:

### Phase 0: Understand the project

1. Read the repository structure to understand how content is organized.
2. Identify the documentation platform and any custom shortcodes, templates, or conventions.
3. Read any existing style guide or contribution guide.
4. Note the deployment mechanism (where does the built site live, how are previews generated).

### Phase 1: Inventory

1. Enumerate all content files (markdown, etc.) in the docs directory.
2. Parse front matter from each file.
3. Count words, extract headings, and identify doc type signals.
4. Build a link graph (which pages link to which).
5. Identify orphan pages (no inbound links).
6. Output the inventory as structured data.

### Phase 2: Classify

1. For each page, run the classification decision tree from `content-classification.md`.
2. Compare the assigned doc type to the current `docType` in front matter (if any).
3. Flag pages where the classification doesn't match.
4. Flag pages that appear to mix doc types.
5. Record classification confidence (high / medium / low).

### Phase 3: Assess and prioritize

1. Score each page on the six assessment criteria.
2. Assign a status (Keep / Update / Split / Merge / Remove / Create).
3. Run the gap analysis — which doc types are missing for each topic area?
4. Prioritize using the tier framework above.
5. Present findings to the user with a recommended action plan.

### Phase 4: Execute (per page)

For each page being rewritten, follow this checklist:

| Step | Action | Severity |
|------|--------|----------|
| 1 | Classify the page's correct doc type | Must do |
| 2 | Normalize front matter (all required fields) | Must do |
| 3 | Enforce template headings (required sections in correct order) | Must do |
| 4 | Rewrite opening to state goal + audience in first 1-2 sentences | Must do |
| 5 | Make steps imperative (verb-first) with conditions before instructions | Must do |
| 6 | Add or fix "Verify" section with specific observable criteria | Must do |
| 7 | Add "Next steps" / "Related" / "See also" with 2-5 links | Must do |
| 8 | Apply writing style rules (active voice, second person, plain language) | Should do |
| 9 | Add role/modality/environment tags if applicable | Should do |
| 10 | Ensure images have alt text and captions | Should do |
| 11 | Check that all internal links resolve | Should do |
| 12 | Set up redirects if URL changed | Must do (if applicable) |
| 13 | Run linting (Vale, markdownlint) if configured | Should do |

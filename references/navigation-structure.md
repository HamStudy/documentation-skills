# Navigation and Information Architecture

How to organize documentation into a navigable hierarchy, build effective sidebar navigation,
cross-link between pages, and create landing pages that orient readers.

## Table of contents

1. [Information architecture principles](#information-architecture-principles)
2. [Site hierarchy design](#site-hierarchy-design)
3. [Sidebar navigation](#sidebar-navigation)
4. [Landing pages and section indexes](#landing-pages-and-section-indexes)
5. [Cross-linking rules](#cross-linking-rules)
6. [Search and discoverability](#search-and-discoverability)
7. [URL strategy](#url-strategy)
8. [Every Page is Page One](#every-page-is-page-one)

---

## Information architecture principles

### Organize by user need, not by product architecture

The #1 mistake in engineer-written docs is mirroring the internal code structure. Users don't
think in modules and classes — they think in tasks and goals.

- Bad: Sidebar mirrors the codebase (`/api/`, `/models/`, `/controllers/`)
- Good: Sidebar mirrors user workflows (`/getting-started/`, `/managing-sessions/`,
  `/exam-day/`, `/after-the-exam/`)

### Limit hierarchy depth

- Maximum **3 levels** of navigation: Section → Subsection → Page.
- If you need a 4th level, the section is too broad — split it into two top-level sections.
- Every page must be reachable in **3 clicks or fewer** from the homepage.

### Keep top-level sections manageable

- Target **5-9 top-level sections** (Miller's Law — the number of items people can hold in
  working memory).
- More than 9 creates decision paralysis; fewer than 4 suggests under-organization.

### Organize by topic, then by content type

The primary axis of organization should be **topic or feature area** (Sessions, Users, Exams),
not content type (Tutorials, Reference, How-tos). Within each topic area, include pages of
different content types as needed.

**Exception:** A top-level "Reference" section collecting all reference pages is acceptable
as a secondary navigation path, alongside topic-based sections. Similarly, a top-level
"Troubleshooting" section works well as a cross-cutting collection.

---

## Site hierarchy design

### Recommended top-level structure

For a documentation site serving multiple user roles with workflow-heavy content:

```
docs/
├── getting-started/          # Quickstarts and first-time setup
│   ├── index                 # Landing: "Choose your path"
│   ├── role-a-quickstart
│   ├── role-b-quickstart
│   └── requirements
├── [feature-area-1]/          # Major feature area (e.g., "sessions")
│   ├── index                 # Landing: overview + links to sub-pages
│   ├── create-thing           # How-to
│   ├── manage-thing           # How-to
│   ├── thing-lifecycle        # Concept
│   └── thing-fields           # Reference
├── [workflow-phase]/           # Workflow-oriented (e.g., "exam-day")
│   ├── index
│   ├── task-a
│   ├── task-b
│   └── troubleshoot-phase
├── reference/                 # Cross-cutting reference
│   ├── index
│   ├── permissions
│   ├── environments
│   └── glossary
└── troubleshooting/           # Cross-cutting troubleshooting
    ├── index
    ├── common-errors
    └── get-help
```

### Feature-area vs. workflow organization

Two valid strategies exist and can be mixed:

**Feature-area** (e.g., "Sessions", "Users", "Reports"): Groups all content about one feature.
Good when users are exploring capabilities or looking up specific features.

**Workflow** (e.g., "Before the exam", "Exam day", "After the exam"): Groups content by
chronological sequence. Good when users follow a predictable flow.

**Best practice:** Use workflow organization for the primary onboarding path (getting started
→ first workflow → advanced workflows), with feature-area sections for reference and deep dives.

---

## Sidebar navigation

### Design rules

1. **Scope the sidebar to the current section.** Don't show the entire site tree at once.
   When the reader is in "Sessions," show only session-related pages. Top-level sections
   should always be visible as a way to switch contexts.

2. **Use collapsible sections** with auto-expand on the active page's section.

3. **2-3 visible nesting levels maximum.** Deeper nesting makes the sidebar unusable on both
   desktop and mobile.

4. **Label task/how-to content with verb phrases:** "Create a session," "Configure permissions."
   Label conceptual/reference content with noun phrases: "Session lifecycle," "Permission model."

5. **Order by learning path for guides** (chronological / logical sequence), by
   importance/frequency for reference (most-used first). Reserve alphabetical ordering only
   for API reference listings.

6. **Highlight the current page** in the sidebar with a clear visual indicator (bold,
   background color, or left border).

7. **Include a "Getting Started" link** at or near the top of the sidebar, visible from
   every section.

### Common sidebar mistakes

- Showing the entire site tree at once (overwhelming for sites with 50+ pages)
- Nesting deeper than 3 levels (users can't track their position)
- Using internal/code terminology for labels ("AdminController" instead of "Manage admins")
- Alphabetical ordering of how-to guides (use task-flow ordering instead)
- No visual indicator of the current page

---

## Landing pages and section indexes

Every major section (anything with sub-pages) must have a **landing page** (index page) that
serves as a navigation hub.

### What a good landing page contains

1. **1-2 sentence overview** of what this section covers.
2. **Card grid or structured link list** of sub-pages, each with a title and 1-sentence
   description. Group related pages visually.
3. **A prominent "Start here" or "Getting started" link** if the section has a recommended
   entry point.
4. **Links to the most popular pages** in the section (if analytics data is available).

### Landing page template

```markdown
# [Section name]

[1-2 sentence overview: what this section covers and who it's for.]

## Get started

- **[Quickstart title](link)** — [1-sentence description]

## Guides

- **[How-to title](link)** — [1-sentence description]
- **[How-to title](link)** — [1-sentence description]

## Learn more

- **[Concept title](link)** — [1-sentence description]

## Reference

- **[Reference title](link)** — [1-sentence description]
```

### Landing page rules

- Never put substantive content on a landing page — it's for navigation only.
- Don't duplicate content from sub-pages. Link to them.
- Keep the page short — if a user has to scroll to find the link they need, the landing
  page has too much on it.
- Order links by the most common user path, not alphabetically.

---

## Cross-linking rules

Cross-linking is the single most effective way to improve documentation discoverability. Users
follow links inline; they navigate to related content from "See also" sections; and search
engines use link structure to determine relevance.

### Inline contextual links

- Link to related concepts, terms, or pages the first time they're mentioned on a page.
- Don't link the same term multiple times on the same page — first mention only.
- Use descriptive link text that tells the reader what they'll find at the destination.
  Never "click here" or "see this page."
- Link to the most specific anchor possible, not just the page.

### End-of-page links

Every page must end with outbound links. The section name depends on the doc type:

| Doc type | Section name | Content |
|----------|-------------|---------|
| Quickstart | "Next steps" | 2-5 links to logical next actions |
| Tutorial | "Next steps" | Next tutorial, related how-tos, concept pages |
| How-to | "Related guides" | Related how-tos, relevant reference |
| Concept | "Related tasks" | How-tos and tutorials that apply this concept |
| Reference | "See also" | Related reference pages, relevant concept pages |
| Troubleshooting | "Get help" | Escalation path, community links, related troubleshooting |

### Link density guidelines

- Aim for **5-15 contextual links per page** (inline + end-of-page combined).
- Fewer than 3 links suggests the page is an island — find connections.
- More than 25 links suggests the page is trying to do too much — split it.
- **Zero orphan pages.** Every page must have at least one inbound link from another page.
  An orphan page is invisible to readers browsing the docs.

### Prerequisite links

When a page depends on prior setup or knowledge, link to it explicitly in the Prerequisites
section rather than assuming the reader has done it:

```markdown
## Prerequisites

- [An active account](/docs/getting-started/create-account/)
- [ExamTools installed](/docs/getting-started/install/)
- Familiarity with [session concepts](/docs/sessions/session-lifecycle/)
```

---

## Search and discoverability

### Search is not optional

Every documentation site with more than ~20 pages needs search. Without it, users who don't
find what they need in the sidebar will leave.

### Search implementation guidelines

- Bind `Cmd/Ctrl+K` as a keyboard shortcut to open search.
- Index at the **heading level**, not just the page level — this dramatically improves
  relevance for long pages.
- Show hierarchical context in results: "Sessions > Create a session > Step 3."
- Popular options for static sites include Pagefind (self-hosted, lightweight), Algolia
  DocSearch (free for open source), and Typesense.

### Search analytics

If your search tool provides analytics, use them. Key metrics:

- **Queries with zero results:** These are content gaps. Either the content doesn't exist
  (write it) or it exists but isn't findable (fix titles/headings/metadata).
- **Queries with high refinement rates:** The user's first search didn't find what they
  needed — the content may exist but have poor discoverability.
- **Most-searched terms:** These should map to prominent sidebar entries and landing page
  links. If they don't, the navigation is misaligned with user needs.

---

## URL strategy

### URL design rules

- Use **lowercase with hyphens**: `/docs/getting-started/create-session/`
- Never use underscores, camelCase, or spaces in URLs.
- Keep URLs short and descriptive. Remove filler words: `/docs/sessions/create/` not
  `/docs/sessions/how-to-create-a-new-session/`
- URLs should be **stable and permanent**. Once published, a URL is a contract.
- When a page moves, always set up a redirect from the old URL.

### Redirect rules during restructuring

- Every moved or renamed page **must** have a redirect from its old URL.
- Prefer server-side redirects (301) over client-side redirects for performance and SEO.
- Maintain a machine-readable redirects file (or use your platform's built-in alias/redirect
  mechanism) as a single source of truth.
- Validate redirects in CI by crawling old URLs against a deploy preview.
- Keep redirects indefinitely — external sites and bookmarks may reference old URLs for years.

---

## Every Page is Page One

This principle (from Mark Baker, 2013) is critical for documentation sites where most traffic
arrives from search engines:

### Rules

1. **Every page must establish its own context** in the first paragraph. State what the page
   covers and who it's for. Don't assume the reader came from the previous page.

2. **Every page must state its prerequisites** explicitly. Link to them — don't just name them.

3. **Every page must be self-contained enough to be useful** even if the reader has never
   visited the site before. This doesn't mean every page must be exhaustive — it means every
   page must orient the reader and link to what they need.

4. **Breadcrumbs reinforce context.** Show `Docs > Section > Current Page` breadcrumbs on
   every page deeper than the top level. The current page should be plain text (not a link).

5. **On-page table of contents** (right sidebar or top-of-page) showing H2-H3 headings with
   scroll-spy highlighting helps readers orient on long pages. This is essential for any page
   longer than ~3 screen-lengths.

### The first-paragraph test

For every page, read only the first paragraph. Can you answer:
- What does this page cover?
- Who is this page for?
- What should I already know before reading this?

If any answer is unclear, rewrite the opening.

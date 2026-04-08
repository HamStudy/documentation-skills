# Quality and Linting

Automated quality enforcement, accessibility, SEO, and CI/CD pipeline patterns for
documentation.

## Table of contents

1. [Quality checklist](#quality-checklist)
2. [Vale prose linting](#vale-prose-linting)
3. [Markdown linting](#markdown-linting)
4. [Link checking](#link-checking)
5. [Accessibility](#accessibility)
6. [SEO basics](#seo-basics)
7. [CI/CD pipeline pattern](#cicd-pipeline-pattern)
8. [Maintenance and freshness](#maintenance-and-freshness)

---

## Quality checklist

Run this checklist against every documentation page, whether during writing, review, or
automated CI:

### Content quality

- [ ] Page has exactly one doc type and follows the template for that type
- [ ] Opening paragraph states what the page covers and who it's for
- [ ] Procedural pages have a Verify section with specific success criteria
- [ ] Page ends with outbound links (Next steps / Related / See also)
- [ ] No banned words ("simply," "just," "easy," "obviously," etc.)
- [ ] Active voice, second person, present tense throughout
- [ ] Conditions stated before instructions
- [ ] Sentences under 25 words
- [ ] Terminology is consistent with the project glossary

### Structure quality

- [ ] Front matter has all required fields (title, description, docType)
- [ ] Title matches the H1
- [ ] Only one H1 per page
- [ ] No skipped heading levels (H2 → H4)
- [ ] Headings are descriptive (scannable without reading body text)
- [ ] Code blocks have language identifiers
- [ ] Lists are parallel in structure

### Link quality

- [ ] All internal links resolve (no broken links)
- [ ] All external links resolve (no broken links)
- [ ] No orphan pages (page has at least one inbound link)
- [ ] Link text is descriptive (no "click here")

### Accessibility

- [ ] All images have alt text
- [ ] Alt text is purpose-focused, not just descriptive
- [ ] Tables have header rows
- [ ] No information conveyed only through color
- [ ] Heading hierarchy supports screen reader navigation

### SEO and metadata

- [ ] Description is unique and 50-160 characters
- [ ] Title is descriptive and includes key terms users would search for
- [ ] URL is clean, lowercase, hyphenated
- [ ] Redirects exist for any changed URLs

---

## Vale prose linting

**Vale** is the recommended prose linter for documentation. It understands Markdown (and
other markup formats), is highly configurable via YAML rules, and has pre-built packages
for major style guides.

### Recommended configuration

Create a `.vale.ini` file at the project root:

```ini
StylesPath = .vale/styles
MinAlertLevel = suggestion

Vocab = ProjectName

Packages = Google, write-good, alex, Readability

[*.md]
BasedOnStyles = Vale, Google, write-good
```

### Recommended packages

| Package | What it checks | Notes |
|---------|---------------|-------|
| **Google** | Google Developer Documentation Style Guide rules | Covers voice, tense, word choice, formatting |
| **Microsoft** | Microsoft Writing Style Guide rules | Alternative to Google; covers similar ground. Pick one as primary. |
| **write-good** | Passive voice, weasel words, wordy phrases | Lightweight supplement to Google/Microsoft |
| **alex** | Insensitive, condescending, or exclusionary language | Flags "simply," "just," "obviously," etc. |
| **Readability** | Flesch-Kincaid grade level, sentence length | Target grade 8-10 for general technical docs |

### Key custom rules to add

Create custom Vale rules in YAML for project-specific enforcement:

**Terminology enforcement** (`Substitution` rule type):
```yaml
# .vale/styles/ProjectName/Terms.yml
extends: substitution
message: "Use '%s' instead of '%s'."
level: warning
swap:
  repo: repository
  log in: sign in
  admin: administrator
```

**Banned phrases** (`existence` rule type):
```yaml
# .vale/styles/ProjectName/Banned.yml
extends: existence
message: "Remove '%s' — it's condescending or adds no value."
level: warning
tokens:
  - simply
  - just
  - easy
  - easily
  - obviously
  - of course
  - straightforward
  - as mentioned above
  - click here
  - please note
```

**Sentence length** (`occurrence` rule type):
```yaml
# .vale/styles/ProjectName/SentenceLength.yml
extends: occurrence
message: "Sentence exceeds 30 words. Consider splitting."
level: suggestion
scope: sentence
max: 30
token: '\w+'
```

### Deployment strategy

- Start with `suggestion` level for most rules. Only set `error` for rules with zero
  existing violations — otherwise CI will block every PR.
- Gradually promote rules from `suggestion` → `warning` → `error` as violations are fixed.
- Use a `Vocab` directory with `accept.txt` and `reject.txt` to handle project-specific
  terms (product names, acronyms, jargon that Vale doesn't know).

---

## Markdown linting

**markdownlint** (DavidAnson/markdownlint) enforces structural Markdown consistency. It
catches formatting problems that affect rendering and readability.

### Most important rules for documentation

| Rule | Name | Why it matters |
|------|------|---------------|
| MD001 | heading-increment | Headings must increase by one level (no H2 → H4 skip) |
| MD003 | heading-style | Consistent heading style (ATX `#` preferred) |
| MD025 | single-h1 | Only one H1 per document |
| MD036 | no-emphasis-as-heading | Don't use bold text as a fake heading — use proper headings |
| MD040 | fenced-code-language | Fenced code blocks must specify a language |
| MD044 | proper-names | Enforce capitalization of proper nouns (configurable) |
| MD012 | no-multiple-blanks | No consecutive blank lines |
| MD047 | single-trailing-newline | Files end with a single newline |

### Configuration

Create a `.markdownlint.json` or `.markdownlint-cli2.jsonc` in the project root:

```json
{
  "MD001": true,
  "MD003": { "style": "atx" },
  "MD013": false,
  "MD025": true,
  "MD036": true,
  "MD040": true,
  "MD044": {
    "names": ["ExamTools", "HamStudy"],
    "code_blocks": false
  }
}
```

Note: MD013 (line length) is typically disabled for documentation because prose lines are
variable length and hard-wrapping at 80 characters hurts diff readability.

---

## Link checking

Broken links erode user trust and waste reader time. Check links automatically.

### Recommended tools

| Tool | Type | Best for |
|------|------|---------|
| **lychee** | CLI / GitHub Action | Fast, Rust-based, supports Markdown and HTML, good CI integration |
| **markdown-link-check** | CLI / GitHub Action | Markdown-specific, simple configuration |
| **htmltest** | CLI | Works on built HTML output |

### Configuration tips

- Run link checks on **every PR** targeting docs content.
- Also run a **scheduled nightly check** to catch external links that have gone stale.
- Maintain an **allowlist** for known flaky URLs (sites that rate-limit or block CI).
- Configure **retry logic** (at least 2 retries with backoff) for transient failures.
- Check both internal and external links, but separate them in reporting — internal
  broken links are always bugs; external broken links may be transient.

### lychee example configuration

```yaml
# .lychee.toml
exclude = ["example\\.com", "localhost"]
accept = [200, 204, 301, 302, 307, 308]
timeout = 20
max_retries = 3
```

---

## Accessibility

Documentation must be accessible to all readers, including those using screen readers,
keyboard navigation, or other assistive technologies.

### Key rules for documentation authors

1. **All images must have alt text.** Alt text should describe the *purpose* of the image,
   not just its appearance. "Dashboard showing the Create Session button in the top-right
   corner" not "Screenshot of the dashboard."

2. **Don't skip heading levels.** Screen readers use heading hierarchy to navigate. Skipping
   from H2 to H4 breaks this navigation.

3. **Use meaningful headings and labels.** Headings should be descriptive enough that a user
   navigating by headings alone can find what they need.

4. **Don't convey information only through color.** If a callout box is red for "danger,"
   also include the word "Danger" or "Warning" in text.

5. **Tables must have header rows.** Use proper `<th>` elements (most Markdown renderers
   handle this from Markdown table syntax automatically).

6. **Link text must be descriptive.** "Learn more about session configuration" not
   "click here" or "learn more."

7. **Keep table complexity reasonable.** Tables with more than 6 columns or deeply nested
   content are difficult to navigate with assistive technology. Consider splitting into
   smaller tables or using definition lists.

### Automated accessibility checks

- Use Vale's **alex** package to flag insensitive or condescending language.
- Use markdownlint's **MD001** (heading increment) to enforce heading hierarchy.
- If the site is built to HTML, run **axe** or **pa11y** against the built pages.

---

## SEO basics

Good SEO for documentation means users can find your docs from search engines. Most SEO
for docs sites comes from good content structure, not from tricks.

### Essential SEO checklist

1. **Every page must have a unique `description`** (50-160 characters) in front matter.
   This becomes the meta description in HTML.

2. **Titles should include terms users search for.** "Create a session" is better than
   "Session creation workflow" because users search "how to create a session."

3. **URLs must be clean and descriptive.** `/docs/sessions/create/` not
   `/docs/s/session_create_new_v2/`

4. **Ensure the site generates a sitemap** and that it's submitted to search engines.

5. **Canonical URLs must be set** — especially if content exists at multiple URLs
   (with and without trailing slashes, www vs non-www).

6. **Every moved page must have a 301 redirect** from the old URL. Broken URLs lose
   accumulated search authority.

7. **Descriptive link text helps search engines** understand page relationships.
   Internal cross-linking with good anchor text is the highest-ROI SEO activity for docs.

---

## CI/CD pipeline pattern

Documentation quality checks should run automatically on every pull request, just like
code tests.

### Recommended pipeline stages

```
PR opened (docs content changed)
  ├── Stage 1: Build
  │   └── Build the documentation site — catches template errors, broken shortcodes
  ├── Stage 2: Lint
  │   ├── Vale (prose style)
  │   └── markdownlint (Markdown structure)
  ├── Stage 3: Links
  │   └── lychee or markdown-link-check (broken link detection)
  ├── Stage 4: Preview
  │   └── Deploy preview to a temporary URL for human review
  └── Stage 5: Review
      └── Human reviews rendered preview for accuracy, layout, navigation
```

### CI configuration principles

- **Only run docs checks when docs files change.** Use path filters to avoid running
  documentation CI on code-only PRs.
- **Fast feedback:** Linting and link checks should complete in under 2 minutes.
- **Non-blocking initially:** When first introducing linting to an existing project, run
  checks as warnings (non-blocking) until existing violations are cleaned up. Then switch
  to blocking.
- **Preview deploys are essential.** Many documentation problems are only visible in the
  rendered output (layout issues, broken navigation, rendering glitches). A deploy preview
  on every PR catches these.

### Example GitHub Actions workflow (conceptual)

```yaml
name: Documentation Quality
on:
  pull_request:
    paths: ['docs/**', 'content/**']
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Vale
        uses: errata-ai/vale-action@v2
        with:
          files: docs/
      - name: markdownlint
        uses: nosborn/github-action-markdown-cli@v3
        with:
          files: docs/
      - name: Link check
        uses: lycheeverse/lychee-action@v1
        with:
          args: --verbose docs/
```

Adapt the paths, tool versions, and job structure to your specific platform and build system.

---

## Maintenance and freshness

Documentation rots. Features change, UIs update, and procedures become inaccurate. Proactive
maintenance prevents docs from becoming a liability.

### Freshness rules

1. **Every page should have a `lastVerified` date** in front matter, set by a human who
   confirmed the content is still accurate.

2. **Pages not verified in 6+ months** should be flagged for review. Automate this with a
   script that checks `lastVerified` dates.

3. **Screenshot-heavy pages go stale faster** than prose-only pages. Prioritize these for
   review when the UI changes.

4. **Tie documentation reviews to the release cycle.** When a feature ships or changes,
   the docs for that feature must be reviewed and updated as part of the release.

5. **Every page should have an owner** — a person or team responsible for keeping it accurate.
   Record this in front matter or a separate ownership file.

### Documentation debt

Treat documentation debt like technical debt:

- Track it explicitly (in a backlog, issue tracker, or the content inventory spreadsheet).
- Prioritize by impact: high-traffic pages with known inaccuracies come first.
- Allocate regular time for docs maintenance — don't only update docs when something is
  visibly broken.
- Include "docs updated" in the definition of done for feature work.

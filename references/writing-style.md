# Writing Style Guide

Voice, tone, and formatting rules for documentation. Every rule in this file is enforceable —
either by an agent during writing/review, or by Vale linting in CI.

## Table of contents

1. [Voice and tone](#voice-and-tone)
2. [Grammar and structure rules](#grammar-and-structure-rules)
3. [Formatting for scannability](#formatting-for-scannability)
4. [Terminology and word choice](#terminology-and-word-choice)
5. [Bad-to-good rewrite patterns](#bad-to-good-rewrite-patterns)
6. [Callout boxes](#callout-boxes)
7. [Code blocks](#code-blocks)
8. [Images and diagrams](#images-and-diagrams)

---

## Voice and tone

The target voice is **a knowledgeable colleague** — friendly, direct, and respectful of the
reader's time. Not a professor lecturing; not a marketer selling. A peer helping.

**Core attributes:**
- **Clear** over clever. No wordplay, no idioms that don't translate globally.
- **Direct** over diplomatic. "Do X" not "You might consider doing X."
- **Confident** over hedging. "This creates a session" not "This should create a session."
- **Respectful** of the reader's intelligence. Don't over-explain the obvious, but don't
  assume knowledge that isn't in the prerequisites.

**Tone varies by doc type:**
- **Quickstart/How-to:** Efficient and action-oriented. Minimal prose between steps.
- **Tutorial:** Warmer and more conversational. Brief explanations between steps are welcome.
- **Concept:** Thoughtful and explanatory. Analogies and diagrams encouraged.
- **Reference:** Terse and precise. No conversational filler.
- **Troubleshooting:** Empathetic ("If you see this error...") but efficient.

---

## Grammar and structure rules

These rules are ordered by impact. Apply all of them.

### 1. Use active voice

The subject performs the action. Passive voice obscures who does what.

- Bad: "The session is created by the team lead."
- Good: "The team lead creates the session."
- Bad: "The configuration file should be edited."
- Good: "Edit the configuration file."

**Exception:** Passive is acceptable in reference docs when the actor is irrelevant
("Sessions are automatically archived after 90 days").

### 2. Use second person ("you")

Address the reader directly. Never use "the user," "one," or "we" (unless "we" genuinely
means the organization).

- Bad: "The user should verify their setup."
- Good: "Verify your setup."
- Bad: "We recommend configuring the timeout."
- Good: "Configure the timeout."

### 3. Use present tense

Describe what happens now, not what will happen.

- Bad: "The system will display an error."
- Good: "The system displays an error."
- Bad: "Clicking Submit will save your changes."
- Good: "Clicking Submit saves your changes."

### 4. Put conditions before instructions

When a step has a condition, state the condition first. This prevents the reader from
starting an action they can't complete.

- Bad: "Click Submit, but if you haven't added your callsign, verify it first."
- Good: "If you haven't verified your callsign, verify it now. Then click Submit."
- Bad: "Run the deploy script (make sure you have SSH access first)."
- Good: "Make sure you have SSH access. Then run the deploy script."

### 5. Keep sentences short

Target under 25 words per sentence. Split anything longer.

- Bad: "When you have configured the environment variables and verified that the database
  connection is active, you can proceed to run the migration script which will update the
  schema."
- Good: "Configure the environment variables. Verify the database connection is active.
  Then run the migration script to update the schema."

### 6. One idea per sentence

Don't chain concepts with semicolons or "and." Each sentence should express one thought.

### 7. Front-load important information

At every level — page, section, paragraph, sentence — put the most important information
first. The reader may stop reading at any point.

- Bad: "After considering the various deployment options and reviewing the documentation,
  you should use the production environment."
- Good: "Use the production environment."

### 8. Use imperative mood for steps

Every step in a procedure starts with a verb commanding the reader to act.

- Bad: "The next thing to do is to open the settings page."
- Good: "Open the settings page."
- Bad: "You should click the Create button."
- Good: "Click **Create**."

### 9. Use contractions

Contractions make prose feel natural: "don't" instead of "do not," "you're" instead of
"you are," "it's" instead of "it is."

**Exception:** Don't contract in warnings or cautions where emphasis matters
("Do **not** delete the production database").

### 10. Use serial (Oxford) commas

Always include the comma before the final item in a list.

- Bad: "The system supports remote, in-person and paper exams."
- Good: "The system supports remote, in-person, and paper exams."

---

## Formatting for scannability

### Headings

- Use **sentence case**: "Configure your database" not "Configure Your Database."
- Make headings descriptive enough to understand without reading body text. A reader scanning
  only headings should be able to find what they need.
- Never skip heading levels (H2 → H4). Always go H1 → H2 → H3 → H4.
- H1 is the page title (matches `title` in front matter). Only one H1 per page.
- H2 for major sections. H3 for subsections. H4 sparingly.
- Use verb phrases for procedural headings: "Create a session," "Configure permissions."
- Use noun phrases for conceptual/reference headings: "Session lifecycle," "Permission model."

### Lists

- Use **numbered lists** only for sequential steps where order matters.
- Use **bulleted lists** for non-sequential items.
- Each list item should be a complete thought, not a sentence fragment.
- Keep list items parallel in structure (all start with verbs, or all are noun phrases).
- Avoid lists longer than 7-9 items — split into sub-groups if needed.

### Paragraphs

- Target **2-3 sentences per paragraph** for web reading.
- Paragraphs over 5 sentences should be split.
- The first sentence of each paragraph should convey the paragraph's main point.

### Emphasis

- **Bold** for UI element names: Click **Create Session**.
- `Code font` for code, commands, file paths, parameter names, values: Run `hugo serve`.
- *Italics* for introducing a new term on first use only: A *session* is a scheduled exam event.
- Don't combine emphasis (no bold-italic, no bold-code unless it's a UI element that
  happens to be a code term).

### Tables

- Use tables for structured data with 3+ rows and 2+ columns.
- Every table needs a header row.
- Keep cells concise — if a cell needs a paragraph, the table is the wrong format.
- For wide tables, consider whether the data would be better as a definition list or
  separate subsections.

---

## Terminology and word choice

### Banned words and phrases

These words are banned because they make struggling readers feel inadequate or add no value:

| Banned | Why | Use instead |
|--------|-----|-------------|
| simply | Condescending — implies the task is trivial | (delete it) |
| just | Same as "simply" when used as minimizer | (delete it, or restructure) |
| easy / easily | If it were easy, the reader wouldn't need docs | (delete it) |
| obviously | If it were obvious, it wouldn't need documenting | (delete it) |
| of course | Same as "obviously" | (delete it) |
| straightforward | Same as "easy" | (delete it) |
| note that | Filler — if it's important enough to say, say it directly | (delete it) |
| please | Overly formal for technical docs | (delete it) |
| in order to | Verbose | "to" |
| utilize | Pretentious | "use" |
| leverage | Jargon | "use" |
| commence | Formal | "start" or "begin" |
| terminate | Formal (unless talking about processes) | "stop" or "end" |
| subsequently | Formal | "then" or "next" |
| facilitate | Vague | "enable," "help," "allow," or something specific |
| functionality | Vague | "feature" or name the specific thing |
| click here | Non-descriptive link text | Describe the destination |
| as mentioned above/below | Fragile reference | Link to the specific section |

### Controlled vocabulary

Maintain a project glossary with these rules:
- Pick ONE term for each concept and use it everywhere. Don't alternate between synonyms.
- Spell out acronyms on first use per page: "Volunteer Examiner (VE)."
- After first use, use the acronym consistently.
- Record the preferred term, banned alternatives, and definition in a glossary file.

### Anthropomorphism

Don't give human qualities to software.

- Bad: "Kubernetes wants you to define a pod."
- Good: "Kubernetes requires a pod definition."
- Bad: "The system thinks the session is complete."
- Good: "The system marks the session as complete."

---

## Bad-to-good rewrite patterns

Use these patterns when rewriting existing documentation:

### Pattern: Vague, indirect voice → Direct, specific

**Before:** "We recommend that a user should verify their setup prior to starting."
**After:** "Before you start, verify your account is active and your signature is on file."

### Pattern: Buried condition → Condition first

**Before:** "Click Submit, but if you haven't added your callsign, verify it first."
**After:** "If you haven't verified your callsign, verify it now. Then click Submit."

### Pattern: Tutorial bloat in a how-to → Extract explanation

**Before:** "Sessions are important because they're the core object of the platform. The
concept of a session originated from..." (5 paragraphs of explanation, then steps)
**After:** "Create a session so you can register candidates and administer exams.
This takes about 2 minutes." (Then steps. Link to the concept page for background.)

### Pattern: Wall of text → Structured steps

**Before:** "To create a session, first go to the dashboard and look for the Create button
in the top right corner, then fill in the required fields including date, time, and location,
and make sure you select the right exam level, then click Save."
**After:**
1. Open the dashboard.
2. Click **Create** in the top-right corner.
3. Fill in the date, time, and location.
4. Select the exam level.
5. Click **Save**.

### Pattern: Passive description → Active instruction

**Before:** "The configuration can be updated by modifying the settings file."
**After:** "Update the configuration by editing the settings file."

### Pattern: Unnecessary hedging → Confident statement

**Before:** "You might want to consider possibly enabling two-factor authentication."
**After:** "Enable two-factor authentication."

### Pattern: Long compound sentence → Multiple short sentences

**Before:** "After the session is created and all VEs have been assigned, you can then
proceed to open registration, which will allow candidates to sign up."
**After:** "Create the session and assign all VEs. Then open registration.
Candidates can now sign up."

---

## Callout boxes

Use callout boxes (admonitions, alerts, or whatever your documentation platform calls them)
sparingly. Too many reduces their impact. Follow this severity hierarchy:

| Type | Use for | Typical icon/color |
|------|---------|-------------------|
| **Tip** | Best practices, shortcuts, time-savers | Green / lightbulb |
| **Note** | Supplementary information that's useful but not critical | Blue / info |
| **Important** | Key information that affects outcomes | Yellow / alert |
| **Warning** | Potential problems, data loss, or security implications | Orange / warning |
| **Caution / Danger** | Serious consequences — irreversible actions, production impact | Red / stop |

**Rules:**
- Maximum 2 callouts per page section (between H2 headings).
- Never put steps inside a callout. Callouts are for supplementary info.
- If you're tempted to put the entire important content in a callout, it should be body text.
- Callout text should be 1-3 sentences. If longer, it's regular content.

---

## Code blocks

- Always include a language identifier for syntax highlighting: ````bash`, ````json`,
  ````yaml`, ````toml`.
- Include a blank line before and after every code block for raw readability.
- Don't include shell prompts (`$`, `#`) unless distinguishing user vs root is important.
- For terminal commands, prefer `bash`. For payloads, use `json`. For config, use `yaml`/`toml`.
- Keep examples minimal and runnable. Move optional flags and advanced variations into
  collapsible sections or separate pages.
- If showing output, label it clearly: "Expected output:" or use a separate code block.

---

## Images and diagrams

- Prefer **Mermaid diagrams** (or equivalent text-based diagram tools) for conceptual flows
  and lifecycle explanations — they're version-controllable and don't go stale as easily
  as screenshots.
- Use **screenshots** only when UI placement is essential and the UI is reasonably stable.
- Every image must have:
  - **Alt text:** Purpose-focused, concise (not "Screenshot of the dashboard" but
    "Dashboard showing the Create Session button in the top-right corner").
  - **Caption:** Explains what the reader should notice or do with the image.
- Screenshots should be cropped to show only the relevant UI area, not the entire screen.
- Mark screenshot-heavy pages with a `lastVerified` date in front matter — screenshots go
  stale faster than prose.

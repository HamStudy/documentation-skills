# Review Passes

The multi-pass workflow for reviewing and editing educational content. Read this before
any review or editing task. Each pass has a single job — mixing jobs is where
overexplaining, tonal wobble, and fabrication sneak in.

## Table of contents

1. [Why separate passes](#why-separate-passes)
2. [Pass 1: Blueprint](#pass-1-blueprint)
3. [Pass 2: Drafting](#pass-2-drafting)
4. [Pass 3: Structure and engagement](#pass-3-structure-and-engagement)
5. [Pass 4: Clarity and audience](#pass-4-clarity-and-audience)
6. [Pass 5: Style and voice](#pass-5-style-and-voice)
7. [Pass 6: Accuracy and sourcing](#pass-6-accuracy-and-sourcing)
8. [Pass 7: Reader validation](#pass-7-reader-validation)
9. [Readability targets](#readability-targets)
10. [Agent prompts](#agent-prompts)

---

## Why separate passes

When you try to fix depth, tone, accuracy, and structure simultaneously, each concern
interferes with the others. You add a clarifying sentence that fixes depth but
introduces a cliché. You cut a cliché but lose a necessary transition. You rewrite for
tone but introduce a factual error.

Separate passes with defined roles prevent this. Each pass has one job and clear
criteria. The order matters: structural decisions (blueprint) must precede prose
decisions (style), and accuracy checking comes last because earlier passes may
introduce new text.

---

## Pass 1: Blueprint

**Job:** Lock scope using backward design. See `depth-calibration.md` for details.

**Inputs:** Chapter topic, target audience, and (if applicable) the question pool or
learning objectives the chapter must address.

**Outputs:** A completed chapter blueprint:
- Outcome statement (1–2 sentences)
- Core mental model (3–7 elements)
- Core vs. Niche tagging for all content
- Retrieval prompts (5–10)
- Off-ramps for further learning

**Criteria:**
- [ ] Every element in the core mental model is necessary for the outcome statement
- [ ] No element in the "Niche" list is needed to understand a "Core" element
- [ ] Retrieval prompts require recall, not recognition
- [ ] Off-ramps use real search terms and standard names

---

## Pass 2: Drafting

**Job:** Write the section using a consistent structure. Don't self-edit — that's for
later passes.

**Structure:** Pick one opening framework per section (ABT, SCQA, or BLUF — see
`structure-and-flow.md`). Then follow the default pattern:

1. Opening framework (1–3 sentences establishing motivation)
2. Segmented explanation (3–7 chunks, each with its own sub-header)
3. At least one worked example or concrete scenario
4. A check question or retrieval prompt
5. Bridge to the next section

**Rules during drafting:**
- Write fast. Prioritize coverage over polish.
- Follow the blueprint. If something isn't in the core mental model, it either goes
  in an optional sidebar or gets cut.
- One idea per paragraph.
- Define every new term at first use.
- Use the Familiar → Bridge → New scaffolding pattern within each chunk.
- Vary the opening framework from the previous section.

---

## Pass 3: Structure and engagement

**Job:** Verify that the section's structure creates narrative momentum, that the
reader feels motivated to learn each concept before the explanation arrives, and that
sections connect through consequence or complication — not mere sequence. See
`structure-and-flow.md` for the full framework.

**The "therefore or but" diagnostic:**
Write a one-sentence summary of each section. Connect consecutive summaries with
"therefore," "but," or "and then." If most connections are "and then," the structure
needs reorganizing — rearrange so each section naturally motivates or complicates the
next.

**Motivation checklist:**
- [ ] The reader feels the **relevance** of the topic before the explanation begins —
      through a concrete problem, a surprising fact, a scenario, or visible stakes
- [ ] Motivation is **embedded in narrative**, not announced with meta-commentary
      ("This is important because...", "Why should we care about...?",
      "You might be wondering...")
- [ ] The opening would **not reverse-engineer** to a visible template — it sounds
      like a human who knows the topic chose where to begin, not like a formula was
      applied

**Engagement architecture checklist:**
- [ ] The section opens with a **hook** — a surprising fact, micro-narrative,
      counterintuitive statement, or information gap (1–3 sentences)
- [ ] **Context and motivation** follow the hook naturally — why this matters, shown
      through story or example, not stated directly
- [ ] The **explanation** builds from concrete to abstract using Familiar → Bridge → New
- [ ] At least one **worked example or concrete application** shows the concept in
      action
- [ ] The section ends with a **bridge** to the next section — through foreshadowing,
      a new question, a callback, or a consequence

**Connection checklist:**
- [ ] **Callbacks** reference earlier concepts where relevant ("Remember when we
      discussed X? Now imagine what happens when...")
- [ ] **Running examples** evolve across sections where possible, gaining complexity
      as understanding deepens
- [ ] **Foreshadowing** hints at concepts that will be fully developed later, creating
      anticipation without requiring understanding
- [ ] **Transitions** between sections are thematic, not mechanical — no "Next, we'll
      discuss..." or "Moving on to..."
- [ ] Opening frameworks **vary** across consecutive sections — not three ABT openings
      in a row

**If the section fails:**
- No felt motivation → rewrite the opening using one of the four motivation patterns
  (problem-first, stakes-through-story, what-breaks-without-it, curiosity-first)
- Meta-commentary motivation → delete the announcement and let the scenario/example
  create the motivation directly
- "And then" connections → rearrange sections so each flows from the previous through
  consequence or complication
- Missing callbacks → identify earlier concepts that connect and add explicit references
- Missing bridge → add a forward-looking sentence that creates an information gap or
  raises a question the next section addresses
- Monotonous opening patterns → switch to a different framework (ABT → BLUF → SCQA)

---

## Pass 4: Clarity and audience

**Job:** Ensure the content is comprehensible to the target audience and structurally
sound.

**Method:** Score against the CDC Clear Communication Index criteria (adapted):

- [ ] **Main message** is stated in the first 2–3 sentences of the section
- [ ] **Main message** is repeated or reinforced near the end
- [ ] Each paragraph contains **one main idea** only
- [ ] **Headings** accurately describe the content that follows
- [ ] **Numbers** are presented with context (comparisons, not raw figures)
- [ ] **Technical terms** are defined at first use
- [ ] No term is used before it is defined
- [ ] No concept references another concept that hasn't been introduced yet
- [ ] The **reading path** is linear — no forward references that require
      understanding content that hasn't appeared yet

**If the section fails any of these:**
- Missing main message → rewrite the opening to state it directly
- Multi-idea paragraphs → split or delete
- Undefined terms → add parenthetical definitions
- Forward references → reorder content or add a brief preview

---

## Pass 5: Style and voice

**Job:** Apply plain language, check rhythm, remove clichés, verify tone. See
`voice-and-style.md` for the full rules and `anti-patterns.md` for cliché detection.

**Checklist:**
- [ ] Active voice is used by default (passive only when the actor is unknown or
      irrelevant)
- [ ] No condescension markers ("obviously," "simply," "just," "of course," etc.)
- [ ] Collaborative language replaces instructional language ("let's" not "you must")
- [ ] Sentence lengths vary — no more than 3 consecutive sentences of similar length
- [ ] No more than 2 consecutive sentences begin with the same word
- [ ] Transition-word starters are limited (remove any that don't change meaning)
- [ ] No repeated metaphors, analogy templates, or sentence patterns
- [ ] Nominalizations have been converted to verbs where possible
- [ ] New information appears at the end of sentences (old-before-new principle)
- [ ] Clutter words have been eliminated (see table in `voice-and-style.md`)
- [ ] The conversational test passes — every sentence sounds like something a human
      would say, not something a textbook would print
- [ ] No phrases from the AI cliché list in `anti-patterns.md` appear without
      deliberate justification

---

## Pass 6: Accuracy and sourcing

**Job:** Verify every factual claim. See `analogies-and-accuracy.md` for the SIFT
method and sourcing standards.

**Method:** For every sentence that asserts a real-world fact, label it:

- **[A]** Common knowledge — universally known, doesn't need a source
- **[B]** Defined earlier in the book — consistent with prior content
- **[C]** Derived from a stated calculation — math checks out
- **[D]** Requires an external source — must be verified

For every [D]:
- Identify the best primary or authoritative source
- Apply SIFT if the claim seems surprisingly neat, dramatic, or convenient

Flag for removal or rewriting:
- Anecdotes presented as real events without a verifiable source
- Statistics without context (sample size, date, population)
- "Origin stories" for terms or technologies that can't be traced
- Attributed quotes that can't be verified
- Idioms or phrases that don't appear to be real/standard

**The conversion rule:** Any assertion that can't be sourced should be reframed as
an illustration (hypothetical scenario) that makes the same pedagogical point, or
cut entirely.

---

## Pass 7: Reader validation

**Job:** Simulate a novice reader's experience. This is the final quality gate.

**Method:** For each section, answer these three questions as if you have no
background in the topic:

1. **"What is the point?"** — Can you state the main message in one sentence?
2. **"What should I remember?"** — Can you identify the 2–3 key takeaways?
3. **"What would I Google to learn more?"** — Do you know the right search terms?

Flag any section where these questions can't be answered after one careful read.
Also flag:

- Moments where you'd feel confused or lost
- Places where you'd need to re-read to understand
- Points where your attention would wander
- Transitions that feel abrupt or unmotivated

**With real readers:** If possible, run 2–5 think-aloud sessions where representative
readers narrate what they think each paragraph means. This catches:
- Where the "minimum viable" explanation is missing a step (underexplained)
- Where the main point is buried under detail (overexplained)

---

## Readability targets

Use readability metrics as **smoke detectors, not fire marshals.** Their limitations
are well documented — they don't measure comprehension, organization, or whether the
right things were explained.

### Target ranges (grades 7–8 reading level)

| Metric | Target | Hard ceiling |
|--------|--------|-------------|
| Flesch-Kincaid Grade Level | 7.0–8.0 | 9.0 |
| Flesch Reading Ease | 60–70 | Below 50 is a red flag |
| Average sentence length | 15–20 words | 25 words |
| Average word length | 1–2 syllables | — |

### What formulas miss

The biggest predictors of actual readability are **word concreteness** and **deep
cohesion** (Coh-Metrix research) — neither of which traditional formulas capture.

To improve real readability beyond formula scores:
- Use explicit connectives ("because," "therefore," "however," "for example")
- Maintain referential overlap between consecutive sentences (repeat key terms
  or use clear pronouns)
- Prefer concrete, imageable words over abstract ones
- Anchor every abstraction with a concrete example
- Make causal relationships explicit — never rely on the reader to infer "why"

The American Press Institute benchmark: comprehension is 100% for sentences of 8
words or fewer, 90% at 14 words, below 10% at 43+ words.

---

## Agent prompts

These prompts can be used to structure each pass when working with AI assistance.

### MVT planner (Pass 1)

```
ROLE: Minimum Viable Teaching (MVT) planner
TASK: Given a chapter draft, produce:
1) a one-sentence "reader outcome"
2) three "must-know" mental model bullets
3) five practice questions that require recall (not recognition)
4) a list of "optional deep dive" items that can be moved out of the mainline
CONSTRAINTS: keep must-know to what's required to meet the outcome; everything
else becomes optional.
```

### Engagement reviewer (Pass 3)

```
ROLE: Structure and engagement reviewer
TASK: For each section in the chapter:
1) Identify the motivation strategy used in the opening. Classify it as:
   problem-first, stakes-through-story, what-breaks-without-it, curiosity-first,
   ABT, SCQA, BLUF, or meta-commentary.
   Flag any that are meta-commentary ("Why should we care...",
   "This is important because...", "You might be wondering...").
2) Write a one-sentence summary of the section. Then connect consecutive
   summaries with "therefore," "but," or "and then." Flag any "and then"
   connections.
3) Check for callbacks to earlier sections, foreshadowing of later sections,
   and whether a bridge to the next section exists.
4) Check that the reader would feel motivated to learn the concept BEFORE the
   explanation begins — not told to care, but shown why it matters.
OUTPUT:
- motivation pattern for each section (with flags for meta-commentary)
- section-to-section connection map (therefore / but / and then)
- list of missing callbacks, bridges, or foreshadowing opportunities
- specific rewrites for any meta-commentary openings
```

### Clarity editor (Pass 4)

```
ROLE: Clarity editor
TASK: Identify the single main message of this section. If it is not stated in
the first 2–3 sentences, rewrite the opening to put it there.
THEN: Mark any paragraph that contains more than one main idea. Split it or
delete what is not needed.
OUTPUT: revised opening + list of paragraphs changed and why.
```

### Style and rhythm editor (Pass 5)

```
ROLE: Anti-cliché and rhythm editor
TASK: Find repeated metaphors, idioms, sentence openers, and templates.
OUTPUT:
- a list of repeated phrases (with counts)
- suggested replacements that are literal or domain-specific
- 5–10 sentence-level rewrites that vary rhythm (mix short and longer sentences)
```

### Accuracy gatekeeper (Pass 6)

```
ROLE: Accuracy gatekeeper
TASK: For every sentence that asserts a real-world fact, label it:
[A] common knowledge
[B] defined earlier in the book
[C] derived from a stated calculation
[D] requires an external source
Then:
- for every [D], ask: "What is the best primary or authoritative source?"
- flag any anecdotes, origin stories, or quote-like text that lacks a source
OUTPUT: a punch list of sentences that must be verified or rewritten.
```

### Novice simulator (Pass 7)

```
ROLE: Novice simulator
TASK: Pretend you are a motivated reader with no background.
For each section, answer:
- "What is the point?"
- "What do you want me to do or remember?"
- "What term would I Google to learn more?"
Flag any moment where you cannot answer those questions after one read.
```

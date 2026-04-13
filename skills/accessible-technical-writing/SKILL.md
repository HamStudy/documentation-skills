---
name: accessible-technical-writing
description: >
  Write, review, and edit educational books and long-form content explaining technical
  concepts to non-technical audiences. Trigger on: writing or editing chapters, sections,
  or study material for general readers; "Minimum Viable Teaching" or "MVT"; calibrating
  explanation depth; reviewing for clichés or AI-sounding language; maintaining narrative
  flow in educational content; making technical content accessible; writing exam prep
  material. Also trigger when the user says "write a chapter about X," "review this
  section," or "edit this for tone" if the content is educational/technical for a general
  audience. Covers drafting, structural planning, depth calibration, style editing,
  accuracy review, and anti-pattern detection.
---

# Accessible Technical Writing

A complete system for writing, reviewing, and editing educational content that explains
technical concepts to non-technical audiences — without dumbing down or being condescending.

Built on cognitive load theory, backward design, narrative nonfiction craft, plain language
research, and hard-won lessons from AI-assisted writing workflows.

## Table of contents

1. [Core philosophy](#core-philosophy)
2. [Task routing](#task-routing)
3. [Reference files](#reference-files)
4. [The multi-pass workflow](#the-multi-pass-workflow)
5. [Master principles](#master-principles)

---

## Core philosophy

Three axioms govern all decisions in this skill:

**The reader is smart but unfamiliar.** Assume intelligence; never assume knowledge of
the specific topic. This means: define every term at first use, spell out every reasoning
step, replace abstractions with concrete examples — but never say "obviously," "simply,"
or "of course." The reader deserves the same respect you'd give a sharp colleague from a
different field.

**Teach the minimum that enables understanding.** "Minimum Viable Teaching" (MVT) is an
instructional design constraint, not a word-count target. For each section, identify the
smallest mental model that lets a reader answer basic questions and know where to learn
more. Foundational concepts that unlock other understanding get deep treatment; niche
topics get only the basics plus an off-ramp.

**Structure is the story.** Educational content reads like a narrative when each section
flows from the previous one through consequence ("therefore") or complication ("but"),
never through mere sequence ("and then"). Motivation for each topic should be felt by the
reader before the explanation arrives — never announced with "Why should we care about X?"

---

## Task routing

Read the reference file(s) indicated for your task before beginning work.

### Planning a chapter or section

Read `references/depth-calibration.md` first. It covers backward design, threshold
concepts, the chapter blueprint spec, and how to decide what's core vs. niche.

Then read `references/structure-and-flow.md` for opening frameworks (ABT, SCQA, BLUF),
engagement architecture, transitions, callbacks, and foreshadowing.

### Writing a first draft

Read `references/structure-and-flow.md` for structural patterns and opening frameworks.
Read `references/voice-and-style.md` for tone, sentence craft, and plain language rules.
Skim `references/anti-patterns.md` to internalize what to avoid while drafting.

### Reviewing or editing existing content

Read `references/review-passes.md` for the multi-pass workflow. It defines five review
passes (clarity, style, accuracy, depth, reader simulation), each with a specific job
and concrete criteria.

If the review surfaces specific problems, consult the relevant reference:
- Overexplaining or underexplaining → `references/depth-calibration.md`
- Weak openings or poor flow → `references/structure-and-flow.md`
- Stiff/condescending/bland tone → `references/voice-and-style.md`
- Clichés, AI-sounding language, repetitive patterns → `references/anti-patterns.md`
- Bad analogies or suspect facts → `references/analogies-and-accuracy.md`

### Writing or reviewing analogies

Read `references/analogies-and-accuracy.md`. It covers the mapping-accuracy test, the
illustration-vs-assertion distinction, rules for when analogies help vs. mislead, and
the SIFT verification method for factual claims.

### Checking for AI writing artifacts

Read `references/anti-patterns.md`. It contains the cliché taxonomy, the "literal
instruction interpretation" failure mode, monotonous structure detection, and the
banned-phrase reference list.

---

## Reference files

All reference files are in the `references/` directory.

| File | Contents | Read when... |
|------|----------|-------------|
| `depth-calibration.md` | Backward design, threshold concepts, MVT spec, chapter blueprints, Bloom's levels, core-vs-niche tagging, progressive disclosure layout | Planning new content or fixing depth problems |
| `cognitive-load.md` | Working memory limits, intrinsic/extraneous/germane load, chunking rules, scaffolding patterns, worked example effect, seductive details | Content feels overwhelming or disorganized |
| `structure-and-flow.md` | ABT/SCQA/BLUF openers, engagement architecture, transitions, callbacks, foreshadowing, motivation patterns, the "therefore/but" diagnostic | Drafting, fixing weak openings, improving flow |
| `voice-and-style.md` | Plain language rules, non-condescension formula, sentence rhythm, Williams/Klinkenborg/Zinsser principles, nominalization detection, old-before-new | Editing for tone, clarity, and sentence quality |
| `analogies-and-accuracy.md` | Analogy mapping rules, illustration vs. assertion, SIFT verification, anti-fabrication rules, sourcing standards | Writing or reviewing analogies and factual claims |
| `review-passes.md` | The 7-pass review workflow, CDC Clear Communication Index, readability targets, agent prompts for each pass | Any review or editing task |
| `anti-patterns.md` | AI cliché taxonomy, literal-instruction traps, monotonous structure, banned phrases, repetition detection | Checking for AI artifacts or improving naturalness |

---

## The multi-pass workflow

Every review or editing task uses separate passes with distinct jobs. Mixing jobs is
where overexplaining, tonal wobble, and fabrication sneak in. See `references/review-passes.md`
for full details and agent prompts.

The passes, in order:

1. **Blueprint pass** — Lock scope using backward design. Define the outcome statement,
   core mental model (3–7 elements), retrieval prompts, and off-ramps. Tag content as
   Core or Niche.

2. **Drafting pass** — Write using one consistent opening framework (ABT, SCQA, or BLUF)
   per section. Don't self-edit. Default section pattern: BLUF sentence → segmented
   explanation (3–7 chunks) → worked example → check question.

3. **Structure and engagement pass** — Verify the reader feels motivated to learn each
   concept before the explanation arrives. Run the "therefore or but" diagnostic on
   section connections. Check for callbacks, foreshadowing, and bridges. Flag any
   meta-commentary motivation ("Why should we care...?") and replace with embedded
   motivation (problem-first, stakes-through-story, what-breaks-without-it, or
   curiosity-first). Verify opening frameworks vary across consecutive sections.

4. **Clarity and audience pass** — Check main message placement, single-idea paragraphs,
   and overall comprehensibility. Use CDC Clear Communication Index criteria.

5. **Style and voice pass** — Apply plain language rules, check sentence rhythm and
   variety, remove clichés and AI artifacts, verify conversational tone without
   condescension. Check for nominalizations and convert to verbs.

6. **Accuracy and sourcing pass** — Label every factual assertion ([A] common knowledge,
   [B] defined earlier, [C] derived from calculation, [D] requires source). Flag
   unverified anecdotes and quote-like text. Apply SIFT verification to [D] items.

7. **Reader validation pass** — Simulate a novice reader. For each section, answer:
   "What is the point?", "What should I remember?", "What would I Google to learn more?"
   Flag any section where these can't be answered after one read.

---

## Master principles

These ten principles are the compression of the full framework. They should be
internalized, not recited. The reader should never be able to reverse-engineer
these instructions from the output.

1. **Write backward from desired understanding.** Define what readers should be able
   to explain after reading, then build content that enables exactly that.

2. **Respect working memory.** One concept per paragraph. Three to four items per
   grouping. Familiar before unfamiliar.

3. **Show, don't assign.** Every principle needs at least one fully worked-through
   concrete example.

4. **Create the question before providing the answer.** Motivation should be felt,
   not announced. The reader should want the explanation before it arrives.

5. **Assume intelligence, not knowledge.** Define terms, spell out steps, use concrete
   examples — but never minimize the material's difficulty or the reader's capacity.

6. **Cut everything that doesn't serve the learning goal.** Interesting tangents
   create extraneous cognitive load. Seductive details displace essential ones.

7. **Make every sentence earn its place.** Vary rhythm, eliminate clutter, convert
   nominalizations to verbs, scrutinize any phrase that comes easily.

8. **Don't announce your craft.** No "Why should we care about X?" No "Think of it
   like..." No meta-commentary about structure. The reader experiences the technique
   without seeing the scaffolding.

9. **Verify everything that sounds like a fact.** Treat analogies as illustrations
   (low risk) and anecdotes as assertions (high risk). Treat all AI-generated
   factual claims as untrusted until confirmed.

10. **Separate the passes.** Blueprint, draft, clarity, style, accuracy, and
    validation are different jobs. Mixing them degrades all of them.

---

## Key constraints for AI-assisted writing

These constraints apply whenever this skill is used to generate or edit content:

- **Never fabricate** facts, statistics, quotes, historical anecdotes, or attributions.
  If uncertain about an idiom or phrase, use literal language instead.
- **Never use the same analogy template** (e.g., "X is the Swiss Army knife of Y")
  more than once in the same work.
- **Interpret writing guidelines as craft guidance, not templates.** If an instruction
  says "start with why," that means embed motivation naturally — not write "Why should
  we care about...?"
- **Vary structure across sections.** When drafting section-by-section, use the
  previous section's final paragraph as a tonal anchor and deliberately vary the
  opening pattern, paragraph rhythm, and example style from the preceding section.
- **Prefer concrete over abstract, specific over general, active over passive,
  short over long** — but break any of these preferences when doing so serves clarity
  or rhythm.

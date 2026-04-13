# Depth Calibration

How to decide what to teach, how deeply, and what to leave out. Read this before
planning any new chapter or section, or when diagnosing overexplaining/underexplaining.

## Table of contents

1. [Backward design](#backward-design)
2. [Threshold concepts](#threshold-concepts)
3. [The chapter blueprint spec](#the-chapter-blueprint-spec)
4. [Depth triage: the three rings](#depth-triage-the-three-rings)
5. [Progressive disclosure as layout](#progressive-disclosure-as-layout)
6. [Retrieval practice](#retrieval-practice)
7. [Bloom's taxonomy for depth targets](#blooms-taxonomy-for-depth-targets)

---

## Backward design

Wiggins and McTighe's *Understanding by Design* provides the operational framework.
Instead of asking "how much should I explain?", ask:

> "What must the reader be able to do or answer by the end of this section, and what
> is the smallest mental model that makes that possible?"

The process has three stages:

1. **Desired results** — What the reader can answer or do after reading. Write this
   as a concrete outcome statement (1–2 sentences). Not "understand electronics" but
   "explain the relationship between voltage, current, and resistance, and use it to
   predict what happens when one changes."

2. **Evidence** — What would prove the reader understood? Write 5–10 retrieval prompts
   that require recall, not recognition. These become the section's "check yourself"
   questions.

3. **Learning plan** — The smallest explanation + examples that enable the reader to
   meet the outcome. Only content that serves the defined outcome belongs in the
   mainline text. Everything else is optional enrichment.

Content that doesn't serve the outcome must either be cut, moved to an optional sidebar,
or reduced to a one-sentence signpost ("There's much more to X, but for our purposes,
the key thing to know is...").

## Threshold concepts

Meyer and Land (2003) identified that certain ideas function as portals: once you
understand them, many other pieces fall into place; if you miss them, everything
downstream feels random.

Threshold concepts are:
- **Transformative** — they change how you see the domain
- **Irreversible** — you can't unsee them once understood
- **Integrative** — they connect previously unrelated ideas
- **Often troublesome** — they may conflict with intuition

Threshold concepts deserve **two to three times more space** than non-threshold concepts
of similar complexity. A simple concept that unlocks everything that follows matters
more than a complex concept that's only relevant in one niche scenario.

To identify threshold concepts, ask: "If a reader missed this one idea, what else would
stop making sense?" If the answer is "a lot" — it's a threshold concept. Give it deep,
careful treatment with multiple examples and explicit connections forward.

## The chapter blueprint spec

Every chapter or major section should have a concrete specification that makes editing
decisions defensible. Create this before drafting.

```
CHAPTER BLUEPRINT: [Title]

OUTCOME STATEMENT (1–2 sentences):
What the reader can now answer or do after reading this section.

CORE MENTAL MODEL (3–7 elements):
The non-negotiable things that must be true in the reader's mind for
the outcome to make sense. Each element is one clear statement.

CONTENT TAGGING:
- CORE: [list items that are widely applicable, prerequisite, or
  threshold concepts — these get full treatment]
- NICHE: [list items that only matter in specific contexts — these
  get recognition-level coverage only]

RETRIEVAL PROMPTS (5–10):
Questions that require recall, not recognition. The reader should be
able to answer these after one careful read.

OFF-RAMPS:
"Where to learn more" items using real search terms and standard names,
so readers can continue independently. These reduce the temptation to
over-explain in the mainline text.
```

## Depth triage: the three rings

Every concept falls into one of three rings of priority:

**Inner ring — Enduring understandings.** The big ideas that should stick long after
details fade. These get the deepest treatment: multiple examples, worked-through
scenarios, explicit connections to other concepts, and retrieval practice.

**Middle ring — Important to know and do.** Key facts, principles, and skills that
receive solid but not exhaustive coverage. One good example, one clear definition,
and connection to the bigger picture.

**Outer ring — Worth being familiar with.** Topics that get a brief mention and a
signpost to further learning. One to two sentences plus an off-ramp. The reader
should recognize the term if they encounter it elsewhere.

The Pareto heuristic: roughly 20% of concepts in any domain generate 80% of
functional understanding. Identify that 20% and make it unmissable through emphasis,
repetition, and rich examples.

**The dinner party test.** After reading, could someone explain this concept
conversationally at a dinner party? They don't need to be experts — they need to be
conversant. They should be able to answer basic questions and know where to look for
more. This is the target for minimum viable teaching.

## Progressive disclosure as layout

Progressive disclosure — originally a UX principle — becomes a book layout strategy.
Show what most people need first; defer advanced or rare paths.

Three tiers of content in any section:

- **Mainline explanation**: minimal, essential for the stated outcome. This is the
  text every reader encounters. It should flow as a continuous narrative.

- **Optional deep dives**: boxed sections, sidebars, footnotes, or clearly labeled
  "If you're curious..." expansions. These let technical readers see that more depth
  exists without forcing everyone through it.

- **Tooling exits**: "If you want to compute or measure this, the tool/method is
  called [specific name]" — rather than teaching full proficiency. Gives the reader
  a search term without burdening the mainline text.

This achieves a critical balance: the narrative stays coherent while technical readers
get signals that the writer *could* go deeper, and they know exactly where to look.

## Retrieval practice

Research on the testing effect shows that being tested on material improves later
retention more than additional studying alone. This argues for short, frequent "check
yourself" prompts as part of the core text — not relegated to an appendix.

Good retrieval prompts:
- Require **recall** ("What does X do?"), not recognition ("Which of these is X?")
- Target the **core mental model** elements from the blueprint
- Are **answerable from the section alone** — they don't require outside knowledge
- Use **varied question types** — not all "What is...?" questions

Place retrieval prompts at the end of each major section, after the explanation and
examples. They serve double duty: testing the reader's understanding and signaling to
the reader what they should have retained (which helps focus re-reading if needed).

## Bloom's taxonomy for depth targets

Use Bloom's revised taxonomy to calibrate how deeply to teach each concept:

- **Remember** — recognize/recall facts. Target for outer-ring (niche) content.
- **Understand** — explain in own words. Target for ALL content at minimum.
- **Apply** — use in new situations. Target for inner-ring (threshold) concepts.
- **Analyze/Evaluate/Create** — higher-order thinking. Signpost as areas for
  further study; don't attempt to cover in the mainline text.

The minimum viable target is "Understand" for everything covered and "Apply" for
threshold concepts. If content doesn't bring readers to at least "Understand," either
deepen the treatment or cut the topic.

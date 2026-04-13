# Anti-Patterns

Common failure modes in AI-assisted educational writing and how to detect and fix them.
Read this when checking for AI artifacts, improving naturalness, or when content sounds
generic, formulaic, or machine-generated.

## Table of contents

1. [AI cliché taxonomy](#ai-cliché-taxonomy)
2. [Literal instruction interpretation](#literal-instruction-interpretation)
3. [Monotonous structure](#monotonous-structure)
4. [The repetition scan](#the-repetition-scan)
5. [Seductive detail traps](#seductive-detail-traps)
6. [The meta-commentary trap](#the-meta-commentary-trap)

---

## AI cliché taxonomy

These words and phrases appear at statistically disproportionate rates in AI-generated
text. They are not banned — any word can be the right word in context — but their
presence should trigger scrutiny. If a concrete, specific alternative exists, use it.

### Overused words

| Word | Problem | Preferred alternative |
|------|---------|----------------------|
| delve | Almost never used in natural speech | explore, examine, look at, dig into |
| robust | Vague intensifier | (state specifically what makes it strong) |
| pivotal | Overdramatic for most uses | important, key, central |
| comprehensive | Often meaningless filler | thorough, complete, (or just delete) |
| crucial | Overused intensifier | important, essential, necessary |
| landscape | Metaphor used as filler | field, area, domain, world |
| tapestry | Purple prose | (use literal description instead) |
| harness | Cliché verb | use, apply, take advantage of |
| leverage | Business jargon | use, build on, take advantage of |
| unlock | Cliché metaphor | enable, make possible, open up |
| unleash | Overdramatic | release, enable, allow |
| navigate | Overextended metaphor | handle, work through, deal with |
| realm | Grandiose for most contexts | area, field, domain |
| embark | Overdramatic | start, begin |
| foster | Vague | encourage, support, build |
| nuanced | Often empty filler | (state the specific nuance instead) |
| multifaceted | Abstract filler | complex, (list the specific facets) |
| streamline | Buzzword | simplify, make faster, reduce steps |
| elevate | Vague intensifier | improve, strengthen, raise |
| underscore | Rarely used in speech | emphasize, highlight, show |

### Overused phrases and patterns

| Pattern | Problem |
|---------|---------|
| "In today's fast-paced world..." | Content-free throat-clearing |
| "It's not about X, it's about Y" | Formulaic reversal structure |
| "X is the Swiss Army knife of Y" | Template analogy |
| "At its core..." | Filler preamble |
| "Let's dive in" / "Let's dive deeper" | Cliché opening/transition |
| "The key takeaway here is..." | Meta-commentary (just state the takeaway) |
| "Think of it this way..." | Announces the analogy instead of just using it |
| "This is where X comes in" | Formulaic introduction |
| "But here's the thing..." | Conversational cliché |
| "The beauty of X is..." | Filler intensifier |
| "When it comes to..." | Wordy preamble (delete, start with the actual point) |
| "It goes without saying..." | If it does, don't say it |
| "In a nutshell..." | Cliché summary opener |
| "The bottom line is..." | Cliché summary opener |
| "X plays a crucial role in Y" | Vague and formulaic |
| "At the end of the day..." | Cliché summary |
| "It's worth noting that..." | Just note it |
| "Needless to say..." | Then don't say it |

### The easy-phrase heuristic

From Zinsser: "If a phrase comes to you easily, look at it with deep suspicion."

Phrases that arrive effortlessly are almost always prefabricated — they exist as
pre-assembled units in the language model (or the human writer's) pattern library.
The good stuff requires effort. When a phrase feels too smooth, too ready, ask:
"Is this saying something specific, or is it filling space with familiar sounds?"

---

## Literal instruction interpretation

The most insidious AI failure mode in educational writing. The model follows the
letter of a writing guideline while violating its spirit.

### Examples

| Instruction | Literal (bad) | Craft (good) |
|-------------|---------------|--------------|
| "Start with why" | "Why should we care about electronics?" | "Every time you key up your radio, electronics turn your voice into a signal that can travel miles." |
| "Use analogies" | "Think of it like a highway for data." | "Data travels through a network the way cars travel on a highway — but unlike cars, data can be in multiple places at once." |
| "Be conversational" | "So, here's the thing about resistors..." | "A resistor does exactly what it sounds like — it resists the flow of current." |
| "Engage the reader" | "Ready to learn something cool?" | "Resistors are one of the simplest components in electronics, but they show up in nearly every circuit ever built." |
| "Provide motivation" | "Understanding this topic is essential for..." | (Open with a concrete scenario where the concept matters) |
| "Make it accessible" | "Don't worry, this isn't as hard as it sounds!" | (Just explain it clearly without commenting on difficulty) |

### The reverse-engineering test

After writing any section, ask: "Could a reader identify which writing guidelines I
was following?" If yes — if the instruction is visible through the output — the
execution is too literal. Rewrite until the technique is invisible and the content
feels like it was written by someone who simply knows how to explain things well.

---

## Monotonous structure

Single-pass long-form generation tends to produce structurally repetitive content.
The same opening pattern, the same paragraph rhythm, the same analogy format, the
same transition style — repeated across every section.

### Detection

Read the first sentence of every section in sequence. If they follow the same
pattern (all questions, all "X is..." definitions, all anecdotes), the structure is
monotonous.

Read the last sentence of every section in sequence. If they all end the same way
(all summaries, all bridges, all questions), same problem.

Check paragraph lengths. If every paragraph is 4–6 sentences with no variation, the
rhythm is flat.

### Prevention

- **Vary opening frameworks** across sections. If three consecutive sections open
  with ABT, switch to BLUF or SCQA for the next one.
- **Use the previous section as an anchor.** When generating section-by-section,
  include the previous section's final paragraph in context and explicitly instruct:
  "Vary the opening pattern, paragraph rhythm, and example style from the preceding
  section."
- **Alternate section lengths.** Some sections should be long and detailed (core
  concepts); others should be short and punchy (bridge sections, quick definitions).
- **Mix example types.** Don't use the same kind of example every time — alternate
  between scenarios, worked problems, visual descriptions, historical references,
  and thought experiments.
- **Vary paragraph lengths within sections.** Include at least one very short
  paragraph (1–2 sentences) per section for emphasis and rhythm.

---

## The repetition scan

A mechanical check for repeated patterns. Run this on every completed draft.

### What to scan for

1. **Repeated metaphors and analogy templates.** Search for metaphor keywords
   ("like a," "think of," "imagine," "Swiss Army knife," "double-edged sword,"
   "tip of the iceberg"). Count unique metaphors vs. repeated ones.

2. **Repeated sentence openers.** Extract the first 3–4 words of every sentence.
   Sort and count. Flag any opener that appears more than twice.

3. **Repeated transition patterns.** Search for "However," "Additionally,"
   "Furthermore," "Moreover," "In fact," "Interestingly," "Importantly." Count
   each. If any appears more than 3 times per chapter, reduce.

4. **Repeated structural patterns.** Check whether sections follow the same
   internal structure (e.g., all open with a question, all have exactly one analogy
   in the second paragraph, all end with a summary sentence).

5. **Repeated intensifiers.** Search for "very," "really," "incredibly,"
   "extremely," "absolutely," "remarkable," "fascinating." These are almost
   always deletable.

### Remediation

For each repeated element:
- **Repeated metaphor** → Replace with a literal, specific description or a fresh
  analogy unique to this concept.
- **Repeated opener** → Restructure the sentence to begin differently. Start with
  a dependent clause, a short declarative, or a concrete noun.
- **Repeated transition** → Delete transitions that don't change meaning. For
  necessary transitions, use content-based connections instead of transition words.
- **Repeated structure** → Reorganize the section's internal pattern. Swap the
  order of elements, vary paragraph count, or change example placement.

---

## Seductive detail traps

Seductive details are interesting but irrelevant tangents that harm learning by
crowding essential content out of working memory. They're especially problematic in
AI-generated content because language models are trained on text that values
engagement, leading them to insert "fun facts" that derail the learning path.

### Detection

For each anecdote, aside, or tangent, ask:
1. Does this directly support the outcome statement for this section?
2. If removed, would the reader's understanding of the core concept be diminished?
3. Is this more memorable than the core content? (If yes, it may be displacing it.)

If the answer to #1 and #2 is "no" and the answer to #3 is "yes" — it's a seductive
detail. Cut it or move it to an optional sidebar.

### Common seductive detail patterns

- Historical origin stories that are interesting but don't help understand the concept
- "Fun fact" tangents that are tenuously connected to the topic
- Extended analogies that become more interesting than the concept they're explaining
- Biographical details about inventors/discoverers that don't illuminate the concept
- Dramatic statistics that create emotional impact but don't support the learning goal

---

## The meta-commentary trap

Meta-commentary is text that talks about the text rather than delivering content.
It's a hallmark of AI-generated educational writing and a sign that the writer is
narrating their process rather than doing their job.

### Examples to eliminate

| Meta-commentary (cut) | Direct alternative |
|-----------------------|-------------------|
| "In this section, we'll explore..." | (Just start exploring) |
| "Let's take a moment to consider..." | (Just consider it) |
| "It's important to understand that..." | (Just explain it) |
| "As we discussed earlier..." | "The impedance matching we covered earlier..." |
| "You might be wondering..." | (Create the wondering through information gaps) |
| "Now that we've covered X, let's move on to Y" | (Use a thematic transition) |
| "Before we dive in, let's..." | (Just start) |
| "The key thing to remember here is..." | (Just state it clearly) |

### The exception

Signposting — briefly telling the reader what's coming or where they are — is not
meta-commentary when it's short and serves cognitive navigation. "This section covers
three types of oscillators" is useful signposting. "In this exciting section, we're
going to explore the fascinating world of oscillators and discover why they're so
important" is meta-commentary.

The test: does the sentence help the reader navigate, or does it fill space with
enthusiasm about the text's own existence? Navigation aids stay; self-congratulation
goes.

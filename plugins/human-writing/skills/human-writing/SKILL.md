---
name: human-writing
description: >-
  Draft or rewrite human-facing prose such as emails, team messages, meeting
  summaries, wiki pages, README files, docs, blog posts, articles, and reports.
  Use for English or Danish text that should sound natural, idiomatic, or less
  AI-like. Do not use for ordinary agent chat, internal reasoning, code-only
  tasks, command explanations, or routine answers without a prose deliverable.
license: BSD-3-Clause
---

# Human writing

Write human-facing prose that sounds like it was written by a competent person in the target language and situation. Use this skill for first drafts, rewrites, tone edits, and humanizing text that sounds generic or machine-made.

## Progressive disclosure

Before drafting, choose one language guide and one context guide. Use only the files needed for the task.

### Language guides

- English: `languages/english.md`
- Danish: `languages/danish.md`

If the requested language is not covered, use the shared principles in this file and ask only if the missing language rules would change the result materially.

### Context guides

- Emails, team messages, short updates, and lightweight meeting summaries: `contexts/conversational.md`
- Wiki pages, README files, runbooks, internal docs, and technical explanations: `contexts/docs.md`
- Blog posts, articles, reports, essays, and polished long-form summaries: `contexts/editorial.md`

If a task spans contexts, pick the dominant reader need. For example, a meeting summary for a project wiki should use the docs guide, not the conversational guide.

## Shared task

1. Identify the language, audience, format, and purpose.
2. Load the relevant language guide and context guide.
3. Draft or rewrite in plain, concrete language.
4. Preserve meaning, facts, constraints, and the user's intended stance.
5. Add texture where the context allows it.
6. Remove formulaic AI patterns.
7. Run the self-check before returning the text.

## Universal principles

Write specific facts before interpretation. Names, dates, numbers, examples, and observable effects beat inflated adjectives.

Match the relationship between writer and reader. A team message can be warm and brief. A README should be fuller, structured, and useful to a reader who arrives cold. A blog post can have voice and movement, but it still needs substance.

Use active voice most of the time. Prefer common words over abstract ones. Vary sentence and paragraph length. Let short sentences stay short.

Do not inflate ordinary facts. If something matters, show why with evidence or operational consequence. If you cannot show why, state the fact and move on.

Do not add vague authority. Name the source or remove the claim. Avoid unnamed experts, industry observers, and generic reports.

Do not write sycophantic or meta text in the deliverable. Skip phrases like "great question," "I hope this helps," AI disclaimers, knowledge-cutoff language, and apologies unless the user explicitly asks for them.

Do not force symmetry. Avoid manufactured groups of three, repeated section shapes, and generic closing summaries. End when the useful content ends.

## Operating modes

### First draft

Generate a clean draft, then self-edit it against the selected language and context guides before returning it.

### Rewrite or humanize

Preserve the original meaning and structure where useful, but replace weak phrasing, filler, inflated claims, and patterns that make the text sound machine-made.

### Adapt to a new context

When moving text from one context to another, change the density and structure. An email can become a wiki page only after adding purpose, prerequisites, examples, and reader navigation. A README can become a team message only after cutting background and surfacing the ask.

## Output format

Return the final text first. Add a brief note about major changes only when it helps the user review the edit.

## Quick self-check

Before delivering text, scan for these tells:

1. Does the text match the requested language and context?
2. Did I use the relevant language guide and context guide?
3. Did I preserve facts, constraints, and intended stance?
4. Are claims specific enough to be useful?
5. Did I add vague importance, generic praise, or unsourced authority?
6. Does every paragraph earn its place for this reader?
7. Are sentence lengths and paragraph lengths varied?
8. Did I use formulaic transitions, filler conclusions, or generic chatbot phrases?
9. For docs, did I add enough structure and operational detail for a cold reader?
10. For conversational writing, did I keep it direct and low-ceremony?


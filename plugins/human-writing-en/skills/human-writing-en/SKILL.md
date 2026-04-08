---
name: human-writing-en
description: >-
  English writing style that reads as human-authored, not AI-generated.
  ALWAYS use this skill when writing prose, documentation, explanations,
  blog posts, emails, articles, reports, or any English text that should
  sound natural and human. Also use it when editing or rewriting text to
  remove AI-sounding patterns. Apply this skill whenever the user mentions
  writing style, tone, voice, or asks text to sound less robotic, more
  natural, or less like AI output.
license: BSD-3-Clause
---

# Human-Sounding English Writing

This skill teaches you to write English that reads like a real person wrote it. AI-generated text has identifiable patterns. LLMs regress to the statistical mean of their training data, replacing specific facts with generic, inflated language. The result: text that sounds positive, vague, and formulaic. This skill helps you avoid those patterns.

## Your task

Use this skill for both first-draft generation and rewriting existing text.

1. Identify the writing context and target voice.
2. Draft or rewrite the text in plain, concrete language.
3. Remove AI-sounding patterns listed below.
4. Preserve meaning, constraints, and intended audience.
5. Add human texture where appropriate for the context.
6. Run the self-check before delivering output.

## Operating modes

### First-draft generation

Generate a clean first draft from scratch, then self-edit it to remove AI patterns before returning it.

### Rewrite and humanize

Preserve the original meaning and structure where possible, but replace AI artifacts and weak phrasing.

## Core Principles

Write sentences that average 10 to 20 words and focus on one idea. Use active voice about 90% of the time. Pick common, concrete words over abstractions. Mix short and medium sentences. Vary paragraph length. State facts directly.

Every sentence you produce should pass this test: could a competent human writer have written this sentence without an LLM? If the answer is no, rewrite it.

## High-risk vocabulary

LLMs overuse specific words. One or two may be fine, but clusters of these terms are a strong AI signal.

**Hard bans in user-facing prose:**

- great question, excellent point, i hope this helps, let me know if you'd like
- as of my last training update, based on my training data

**Words to watch (avoid unless context truly requires them):**

- additionally, moreover, furthermore, consequently, therefore, ultimately, notably
- delve, foster, leverage, utilize, underscore, garner, showcase, enhance
- pivotal, crucial, vital, intricate, vibrant, seamless, robust, dynamic, innovative, groundbreaking
- tapestry, landscape (as metaphor), testament, interplay, synergy, paradigm
- holistic, cutting-edge, game-changer, realm, journey (as metaphor)
- nestled, bustling, in the heart of, breathtaking, renowned
- it's important to note, it's worth mentioning, at the end of the day
- in today's [anything], in the world of, in the realm of, in a nutshell
- moving forward, going forward, with that being said, needless to say
- when it comes to, a significant number of, last but not least
- serves as, stands as, boasts (meaning "has"), aligns with
- exemplifies, epitomizes, embodies, encapsulates
- navigate/navigating (metaphorical), elevate, embark, unleash, uncover
- rich (figurative), profound, comprehensive, extensive (as filler adjectives)

**Replacements:** Use "is" instead of "serves as." Use "has" instead of "boasts." Use "shows" instead of "showcases." Use "important" sparingly, and only when something is actually important. Use "use" instead of "leverage" or "utilize." Use "try" instead of "endeavor." Use "start" instead of "embark." Use "look into" instead of "delve into."

## Banned Sentence Patterns

### Significance inflation

LLMs inflate the importance of ordinary facts. A train station becomes "a key hub that has played a vital role in the socio-economic development of the region." A town's founding becomes "a pivotal moment that marked a shift in regional governance."

Write the fact. Skip the commentary about its importance. If something is important, the fact itself will show that.

**Bad:** "The institute was established in 1989, marking a pivotal moment in the evolution of regional statistics."
**Good:** "The institute was established in 1989 to collect and publish regional statistics."

### Notability name-dropping

LLMs often list major outlets or follower counts to imply authority without substance.

**Bad:** "Her views were cited by NYT, BBC, FT, and others, and she has 500,000 followers."
**Good:** "In a 2024 New York Times interview, she argued for outcome-based AI regulation."

### Superficial -ing phrases

LLMs tack present participle phrases onto the end of sentences to add fake depth: "highlighting its importance," "underscoring the need for," "reflecting broader trends," "contributing to the ongoing dialogue."

Cut them. If the analysis matters, give it its own sentence with specific evidence.

**Bad:** "The color palette resonates with the region's natural beauty, symbolizing Texas bluebonnets and the Gulf coast, reflecting the community's deep connection to the land."
**Good:** "The architect chose blue, green, and gold to reference local bluebonnets and the Gulf coast."

### The "Despite challenges" formula

LLMs end articles with: "Despite [positive words], [subject] faces challenges including [list]. Despite these challenges, [subject] continues to thrive." This is a formula, not analysis.

If challenges exist, name them with specifics. If prospects exist, cite evidence.

**Bad:** "Despite its industrial prosperity, Korattur faces challenges typical of urban areas. Despite these challenges, it continues to thrive."
**Good:** "Traffic increased after three IT parks opened in 2015. The city began a drainage project in 2022 to address recurring floods."

### Negative parallelisms

LLMs overuse "not just X, but also Y" and "it's not about X, it's about Y" to sound thoughtful. Real writers use these constructions sparingly.

**Bad:** "It's not just about autocomplete; it's about unlocking creativity at scale."
**Good:** "These tools do more than autocomplete. They generate whole functions and test scaffolding."

### Rule of three

LLMs force ideas into groups of three: "adjective, adjective, and adjective" or "phrase, phrase, and phrase."

If you have two things to say, say two. If you have four, say four. Don't manufacture a third item to fill the pattern.

**Bad:** "The event features keynote sessions, panel discussions, and networking opportunities."
**Good:** "The event includes talks and panels. There's time for informal networking between sessions."

### Elegant variation (synonym cycling)

LLMs avoid repeating words by cycling through synonyms. A character becomes "the protagonist," then "the central figure," then "the hero." Just use the same word. Repetition is fine.

**Bad:** "The protagonist faces challenges. The main character must overcome obstacles. The central figure eventually triumphs."
**Good:** "The protagonist faces challenges but eventually triumphs and returns home."

### False ranges

LLMs use "from X to Y" constructions where X and Y are not a meaningful scale.

**Bad:** "The book covers topics from the Big Bang to dark matter."
**Good:** "The book covers the Big Bang, star formation, and dark matter theories."

### Copula avoidance

LLMs replace "is" and "are" with fancier constructions: "serves as," "stands as," "functions as," "represents." Use "is." Use "are." Use "has." These are good words.

**Bad:** "Gallery 825 serves as LAAA's exhibition space for contemporary art. The gallery features four separate spaces."
**Good:** "Gallery 825 is LAAA's exhibition space. The gallery has four rooms."

## Banned Punctuation and Formatting

### Semicolons

Avoid semicolons. Use a period and start a new sentence, or use a comma with a conjunction.

**Bad:** "We researched extensively; the results were clear."
**Good:** "We researched extensively, and the results were clear."

### Em dashes

Avoid em dashes. LLMs overuse them in places where humans would use commas, parentheses, or separate sentences. If you must use one, limit yourself to one per 500 words at most.

**Bad:** "The idea — though interesting — was rejected."
**Good:** "The idea was interesting but was rejected."

### Excessive boldface

Do not bold phrases for emphasis in a "key takeaways" style. Bold sparingly and only for structural purposes like defined terms.

**Bad:** "It blends **OKRs**, **KPIs**, and **BSC** frameworks."
**Good:** "It blends OKRs, KPIs, and BSC frameworks."

### Inline-header vertical lists

Avoid bullet lists where each item starts with a bold label and a colon unless the user explicitly asks for that format.

**Bad:** "- **Performance:** Load times improved. - **Security:** Encryption was added."
**Good:** "The update improved load times and added encryption."

### Emoji in prose

Do not use emoji unless the user asks for them.

**Bad:** "🚀 Launch phase starts in Q3."
**Good:** "Launch phase starts in Q3."

### Title case in headings

Use sentence case for headings: capitalize only the first word and proper nouns.

**Bad:** "Strategic Negotiations And Global Partnerships"
**Good:** "Strategic negotiations and global partnerships"

### Curly quotation marks

Use straight quotes ("like this") and straight apostrophes, not curly ones.

**Bad:** "He said “the project is on track.”"
**Good:** "He said \"the project is on track.\""

## Tone and Voice

### Preserve register and intent

Match the target context before adding personality:

- Technical docs: neutral, concrete, low emotion.
- Work emails: direct, polite, specific.
- Marketing copy: persuasive but still factual.
- Academic writing: careful claims and explicit evidence.

When the user provides a writing sample, mirror that tone unless they ask for a change.

### No promotional language

LLMs write like travel brochures and press releases. Strip out all puffery. Do not call things "groundbreaking," "stunning," "comprehensive," or "world-class." Just state what the thing does or is.

**Bad:** "Nestled within the breathtaking Gonder region, the town stands as a vibrant center with a rich cultural heritage and stunning natural beauty."
**Good:** "Alamata Raya Kobo is a town in the Gonder region, known for its weekly market and 18th-century church."

### No vague attributions

Do not attribute claims to unnamed experts, observers, or industry reports. Name the source or cut the claim.

**Bad:** "Experts believe it plays a crucial role in the regional ecosystem."
**Good:** "A 2019 Chinese Academy of Sciences survey found three endemic fish species in the river."

### No hedging

Do not stack qualifiers: "could potentially possibly be argued that it might have some effect." State the claim directly. If certainty is low, say so once and move on.

**Bad:** "It could potentially be argued that the policy might have some positive effect on outcomes."
**Good:** "The policy may affect outcomes. Early data is mixed."

### No filler phrases

Cut phrases that add no meaning:

- "In order to" becomes "to"
- "Due to the fact that" becomes "because"
- "At this point in time" becomes "now"
- "It is important to note that" becomes nothing (just state the thing)
- "Has the ability to" becomes "can"
- "In the event that" becomes "if"
- "At the end of the day" becomes nothing
- "The question of whether" becomes "whether"

### No sycophancy

Never write "Great question!" or "That's an excellent point!" or "I hope this helps!" These are chatbot artifacts. Start with the answer.

### No self-reference

Never mention being an AI, having limitations, training data, or knowledge cutoffs in the output text. Never apologize.

### No knowledge-cutoff disclaimers

Do not leave disclaimer phrasing in final prose.

**Bad:** "As of my last training update, details are limited."
**Good:** "Public filings from 2024 do not include that detail."

### No meta-conclusions

Do not end with "In summary," "In conclusion," or "The future looks bright." End when you run out of things to say. The last paragraph should contain new information, not a restatement.

## Sentence Construction

Keep most sentences to one verb phrase. Break complex sentences into shorter ones.

**Bad:** "Because the data were incomplete and the timeline was short, we postponed the launch, although we had secured funding."
**Good:** "The data were incomplete. We had little time. We postponed the launch even though funding was ready."

Avoid stacking subordinating conjunctions (because, although, since, if, unless, when, while). One per sentence is usually enough.

Avoid chains of prepositional phrases. "The analysis of the performance of the system in the context of the requirements of the project" should become "the system's performance analysis" or something similarly direct.

Use plain connectors: "and," "but," "so," "then." These do the job.

## Adding Human Texture

Avoiding AI patterns is half the job. Sterile, voiceless writing is also a giveaway. Good writing has a person behind it.

**Vary rhythm.** Short sentences. Then a longer one that takes its time. Mix it up. Do not make every sentence the same length.

**Be specific.** Numbers, dates, names, and measurable facts beat adjectives. "Revenue grew 12% in Q3" beats "revenue experienced significant growth."

**Acknowledge complexity when honest.** "This is impressive but also a bit unsettling" beats a long neutral list of pros and cons.

**Ask a genuine question occasionally.** Use this in conversational formats only. Skip it for formal docs, policy text, and academic writing.

**Let structure be imperfect sometimes.** Overly symmetrical outlines feel algorithmic. Not every section needs the same number of subsections or paragraphs.

**Use "is" and "are" freely.** LLMs avoid these. Humans don't.

## Process

1. Read the request and identify context, audience, and tone.
2. Draft or rewrite the text.
3. Scan for AI patterns in this file and fix them.
4. Verify factual claims stay intact.
5. Run the quick self-check.
6. Return final text, and optionally a short changelog if helpful.

## Output format

Provide:

1. The final rewritten or drafted text.
2. Optional brief summary of what changed and why.

## Quick Self-Check

Before delivering text, scan for these tells:

1. Did I use three or more high-risk vocabulary words? Rewrite them.
2. Do multiple sentences end with -ing phrases? Cut them.
3. Is every sentence between 15 and 25 words? Vary the length.
4. Did I use "serves as" or "stands as" anywhere? Replace with "is."
5. Does any paragraph inflate significance without evidence? Cut the inflation.
6. Did I end with a vague positive conclusion? End with a fact instead.
7. Are there em dashes? Replace with commas or periods.
8. Did I use semicolons? Replace with periods.
9. Are there more than two items in a parallel list? Check if the third is filler.
10. Did I bold multiple phrases for emphasis? Remove the bold.
11. Did I add vague notability claims instead of concrete facts?
12. Did I use a false "from X to Y" range?
13. Did I keep the right tone for the target context?

## Full example

**Bad:** "The new update serves as a testament to our innovative vision. Moreover, it delivers a seamless, intuitive, and powerful experience, ensuring users can maximize productivity."

**Good:** "The update adds batch export, keyboard shortcuts, and offline mode. In beta testing, most users completed tasks faster."

Changes made: removed inflated language, removed rule-of-three filler, replaced abstract claims with specific features and evidence.

## Reference

Pattern foundations are aligned with the Wikipedia guide on signs of AI writing.

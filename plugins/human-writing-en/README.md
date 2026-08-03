# Human Writing

Writing style plugin that helps agents draft and rewrite human-facing prose that
sounds natural for its language, reader, and format.

## What it does

LLM-generated text often drifts toward inflated vocabulary, vague hedging,
formulaic structure, and tone that does not fit the situation. This plugin gives
agents a shared writing process, language-specific rules, and context-specific
guidance for denser documentation versus lighter messages.

| Area | Examples |
|------|----------|
| Languages | English and Danish guidance |
| Contexts | Emails, team messages, wiki pages, README files, documentation, blog posts, reports |
| Vocabulary | High-risk AI-sounding words and phrases in each language |
| Structure | Different expectations for conversational, documentation, and editorial prose |
| Tone | Direct, specific writing that preserves register and audience fit |

## Skills

### `human-writing`

Activated when drafting, editing, or rewriting prose meant for human readers:
emails, team messages, meeting summaries, wiki pages, README files,
documentation, blog posts, articles, and reports. Also activated when the user
asks to make text more natural, idiomatic, human-sounding, less robotic, or less
AI-like.

The skill should not activate for ordinary agent conversation, internal
reasoning, code-only tasks, command explanations, or routine answers unless the
user is asking for a human-facing prose deliverable.

## Structure

```text
skills/human-writing/
	SKILL.md                    # Shared process and routing guidance
	languages/
		english.md                # English-specific vocabulary, patterns, and examples
		danish.md                 # Danish-specific vocabulary, patterns, and examples
	contexts/
		conversational.md         # Emails, team messages, short updates
		docs.md                   # Wiki pages, README files, runbooks, technical docs
		editorial.md              # Blog posts, articles, reports, polished summaries
```

# JOSS Review

Review plugin that guides AI agents through the Journal of Open Source Software
(JOSS) submission review process.

## What it does

JOSS reviews are checklist-driven. This plugin condenses the official review
criteria and checklist into an actionable workflow that agents can follow
step by step.

| Area | Examples |
|------|----------|
| Screening | Repository age, license, commit history |
| Installation | Clone, install, verify core functionality |
| Paper review | Required sections, claims, references |
| Documentation | README quality, examples, API docs |
| Feedback | Grading (Accept / Minor / Major Revisions), constructive comments |

## Skills

### `joss-review`

Activated when reviewing a JOSS paper, preparing review comments for a JOSS
submission, evaluating research software against JOSS criteria, or when the user
mentions "openjournals/joss-reviews" or a JOSS review issue. Walks through the
review in a specific order: screen first, install and test, read the paper,
evaluate documentation, then write feedback.

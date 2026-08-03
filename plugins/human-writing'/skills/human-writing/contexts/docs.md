# Documentation context

Use this guide for wiki pages, README files, runbooks, setup guides, internal documentation, technical explanations, and other reference material.

## Goal

Write for a reader who arrives without the meeting context. Documentation should be fuller than an email, but still plain. It should help the reader decide what the page is for, whether it applies to them, and what to do next.

## Add enough structure

Include the sections the reader needs. Do not use every section every time.

- Purpose: what this page helps with.
- Audience: who should read it.
- Scope: what it covers and what it does not cover.
- Prerequisites: access, tools, permissions, setup, assumptions.
- Steps: numbered actions when order matters.
- Examples: concrete commands, inputs, outputs, or scenarios.
- Decisions: what was decided and why.
- Troubleshooting: symptoms, causes, fixes, and where to look next.
- Maintenance: owner, update cadence, or source of truth.

## Make it useful, not bare

Do not reduce docs to terse statements. Add the connective tissue a real reader needs: why a step exists, what success looks like, what can go wrong, and how to recover.

Prefer concrete examples over abstract descriptions. A README that says "configure the environment" is weaker than one that names the required variables and shows a minimal command.

Use links or cross-references instead of "as mentioned earlier" when the medium supports it.

## Keep the tone neutral

Documentation should be calm and direct. Avoid marketing language, jokes that age badly, and chatty asides that slow down scanning.

Use headings that match reader questions:

- "What this does"
- "Before you start"
- "Run locally"
- "Deploy"
- "Troubleshooting"

## Patterns

Bad: "This README gives a comprehensive overview of the project and explains how to get started quickly and efficiently."

Good: "This README shows how to install dependencies, run the API locally, and execute the integration tests."

Bad: "Make sure your environment is configured correctly."

Good: "Set `API_BASE_URL` and `CLIENT_ID` before starting the app. Without them, login fails with `missing_client_id`."

Bad: "The system supports robust error handling across various scenarios."

Good: "If the import job fails, it writes the failed row numbers to `import-errors.csv` and exits with code 2."

## Documentation self-check

1. Can a cold reader tell whether this page applies to them?
2. Are prerequisites explicit?
3. Are steps ordered and testable?
4. Does the page include at least one concrete example when the topic is procedural?
5. Are error cases or limits named where they matter?
6. Does the final section give a useful next action or source of truth?

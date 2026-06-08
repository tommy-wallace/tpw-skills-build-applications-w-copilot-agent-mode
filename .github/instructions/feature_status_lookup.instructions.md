---
applyTo: "feature-status-assistant/**"
---
# Feature Status Assistant Guidelines

Build a Slack/Teams "Where's my feature?" assistant that accepts `/feature-status <query>` and returns customer-safe output.

## Required behavior

- Search across:
  - GitHub issues
  - GitHub pull requests
  - GitHub projects (items/fields)
  - Changelog content (for example `CHANGELOG.md` or GitHub releases)
- Normalize natural-language feature queries (for example `stacked prs`, `stacked pull requests`, `stacked PR`).
- Classify results into one of:
  - `shipped`
  - `in progress`
  - `not planned`
- Return a concise customer-safe summary plus supporting public links.

## Customer-safe output rules

- Never include private repository data.
- Never include internal-only notes, security details, or confidential implementation details.
- Avoid sharing roadmap commitments unless they are publicly documented.
- If evidence is mixed or incomplete, state uncertainty clearly without exposing internal context.

## Output template

Return these sections in this order:

1. `Status:` shipped / in progress / not planned
2. `Customer-safe summary:` 2-4 sentences suitable for email
3. `Public references:` bullet list of public issues/PRs/releases/changelog links
4. `Last updated:` UTC timestamp

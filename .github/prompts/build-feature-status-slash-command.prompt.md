---
mode: 'agent'
model: GPT-5.5
description: 'Build a customer-safe /feature-status Slack/Teams command'
---

Build a production-ready "Where's my feature?" lookup tool in `feature-status-assistant`.

Requirements:

1. Implement a Node.js + TypeScript service with an HTTP endpoint that can be used by Slack slash commands and Microsoft Teams command handlers.
2. Support command input in the form `/feature-status <query>` where `<query>` can be natural language (for example `stacked prs`).
3. Query GitHub for relevant public issues, PRs, and project metadata using GitHub APIs.
4. Query public changelog evidence from `CHANGELOG.md` and/or GitHub releases.
5. Rank and combine evidence by relevance and recency.
6. Compute a final status: `shipped`, `in progress`, or `not planned`.
7. Generate a "SAFE TO SHARE WITH CUSTOMER" summary that excludes private/confidential/internal details.
8. Return structured JSON that includes:
   - `query`
   - `status`
   - `summary`
   - `references` (public URLs only)
   - `generatedAt`
9. Add clear setup instructions in `feature-status-assistant/README.md` for environment variables and local testing.
10. Add focused tests for status classification and customer-safe redaction behavior.

Implementation constraints:

- Keep logic modular (search, ranking, classification, safety filtering, formatter).
- If confidence is low, use cautious wording in the summary instead of making commitments.
- Never include internal/private URLs in output.

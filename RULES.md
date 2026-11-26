# Scenario A rules

This project intentionally has no data access and no domain context.

## Required behavior

1. Do not call databases, Cube, MCPs, skills, or external data tools.
2. Do not invent factual or numerical results.
3. If a question requires unavailable data, say the answer cannot be verified from the available context.
4. Do not claim a query, connection, or source was used.
5. Preserve the user's requested language and response format.

## Isolation rule

Do not add `databases`, `agent/mcps`, schema/business documentation, semantic mappings, examples containing answers, or skills to this repository. Any such addition changes the A baseline and requires protocol review.

## First-turn response requirement
Always answer the user's question in the current response and provide every requested field; if data is unavailable, state that explicitly without inventing values or deferring the answer to a follow-up.

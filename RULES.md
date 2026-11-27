# Scenario A rules

This project intentionally has no data access and no domain context.

## Required behavior

1. Do not call databases, Cube, MCPs, skills, or external data tools.
2. Do not invent factual or numerical results.
3. If a question requires unavailable data, say the answer cannot be verified from the available context.
4. Do not claim a query, connection, or source was used.
5. Preserve the user's requested language and response format.

## Isolation rule

Do not add `databases`, `agent/mcps`, schema/business documentation, semantic mappings, examples containing answers, or skills to this repository. The shared temporal reference below is the only benchmark-wide evaluation metadata intentionally provided to all scenarios; it grants no data access or BookSQL domain context. Any other context addition changes the A baseline and requires protocol review.

## Shared BookSQL benchmark temporal reference

For BookSQL benchmark questions, use `2022-06-01` as the fixed `as_of_date`, matching the date used by the official evaluator for its supported temporal replacements. This does not mean every date/time SQL expression is normalized. The anchor overrides the actual system/database clock only for interpreting temporal expressions in this benchmark.

Use this date only to interpret relative time wording or query predicates. It is not a data cutoff: do not add a blanket `transaction_date <= '2022-06-01'`, do not suppress later transactions, and do not add a date filter when the question has no temporal condition. Preserve the original questions, Gold SQL, and source data.

When forming a query for a relative period, resolve it to explicit absolute ISO dates from this anchor. Preserve the question's intended period and the Gold predicate's boundary semantics; distinguish a full calendar period (for example, “this month”) from a period-to-date (for example, “month to date”). For Cube, use absolute date-range endpoints rather than runtime-relative ranges. For SQL, do not rely on `CURRENT_DATE` or `now` at query time. If an evaluator must normalize unchanged Gold SQL, normalize a separate execution copy and use the same anchor for Gold and predictions. Temporal normalization must not alter text literals or other query semantics.

This is a date-only reference; it does not define a time of day or timezone for `CURRENT_TIMESTAMP`/`now`. Do not invent those values unless the benchmark protocol separately specifies them.

### Fiscal-year interpretation

For this BookSQL benchmark, the fiscal year runs from April 1 through March 31. With `as_of_date = 2022-06-01`, interpret “this fiscal year” and “this fiscal year to date” as 2022-04-01 through 2022-06-01, inclusive. “Last fiscal year” means 2021-04-01 through 2022-03-31, inclusive. Only an explicit request for the full FY 2022–23 uses 2022-04-01 through 2023-03-31.

In the validation split, 150 Gold queries worded “this fiscal year to date” instead cover the full FY through 2023-03-31. Preserve those questions and Gold SQL unchanged, but flag/report them separately as Gold/wording inconsistencies. Do not reproduce that full-year range when answering a genuine “to date” question or silently rewrite Gold.

## First-turn response requirement
Always answer the user's question in the current response and provide every requested field; if data is unavailable, state that explicitly without inventing values or deferring the answer to a follow-up.

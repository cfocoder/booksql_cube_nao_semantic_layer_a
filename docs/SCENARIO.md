# Scenario A deployment contract

## Required Nao project

```text
Project: booksql-condition-a
Repository: https://github.com/cfocoder/booksql_cube_nao_semantic_layer_a.git
Branch: main
```

## Allowed capabilities

```text
LLM: yes
SQLite MCP: no
Cube BookSQL MCP: no
Business skill: no
Technical schema context: no
```

A deployment should expose no database or MCP tools in this project. Model credentials may be supplied by the runtime, but do not declare or include data access.

## Fiscal-year convention

BookSQL fiscal years run from April 1 through March 31, as implied by the authors' [DIN-SQL example](https://github.com/Exploration-Lab/BookSQL/blob/main/GPT/DIN-SQL.py#L1584). With the benchmark reference date 2022-06-01, “this fiscal year” and “this fiscal year to date” mean 2022-04-01 through 2022-06-01; “last fiscal year” means 2021-04-01 through 2022-03-31. A full FY 2022–23, when explicitly requested, means 2022-04-01 through 2023-03-31.

The validation split has 150 Gold queries worded “this fiscal year to date” whose SQL instead covers the full FY through 2023-03-31. Keep questions and official Gold unchanged; flag these cases separately as Gold/wording inconsistencies.

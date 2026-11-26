# Scenario A — LLM baseline without data access

This repository is the Nao Multi-project context for BookSQL scenario **A**.

## Boundary

- No physical database connection, MCP, schema, semantic model, benchmark mapping, or business skill.
- The agent answers only from the user's prompt and conversation state.
- It must not invent factual or numerical answers or claim that it queried a source.
- Use the same model/provider, prompt, question, language, and response format as B/C/D; only available capabilities differ.

## Project mapping

- Nao project: `booksql-condition-a`
- Repository: `cfocoder/booksql_cube_nao_semantic_layer_a`
- Expected route: LLM without tools

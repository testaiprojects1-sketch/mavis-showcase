# ADR 002: SOUL.md Design — Personality + Guardrails

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Need to encode: identity, values, behavioral rules, tool schemas, guardrails, preferences — in a format that's version-controllable, hot-reloadable, and non-technical editable.

## Decision
Use Markdown with YAML frontmatter (SOUL.md) as the single source of truth for personality and guardrails.

## Rationale
- Markdown: human-readable, diffable, editable by non-engineers
- YAML frontmatter: structured config (model params, tool schemas, guardrail rules)
- Hot-reload: Hermes watches file changes; no restart needed
- Version control: full history of personality evolution
- Eval harness: can test guardrail adherence against SOUL.md rules

## Consequences
- Parsing complexity (YAML + Markdown sections)
- Schema validation needed for frontmatter
- Guardrail enforcement at runtime requires Hermes integration
- Migration path needed for schema changes
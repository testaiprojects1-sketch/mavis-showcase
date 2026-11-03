# ADR 004: Tool Registry — Explicit Schemas in SOUL.md

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
15+ tools need: type-safe invocation, self-documentation, eval harness compatibility, guardrail enforcement.

## Decision
Define tool schemas in SOUL.md frontmatter (YAML); implement as Python functions with matching signatures. Hermes validates at runtime.

## Rationale
- Single source of truth: schema + implementation coupled
- Type-safe: Hermes validates args against schema before invocation
- Self-documenting: SOUL.md serves as tool catalog
- Eval harness: can generate test cases from schemas
- Guardrails: schema can encode constraints (e.g., `confirm_required: true`)

## Consequences
- Boilerplate per tool (schema + implementation)
- Schema changes require SOUL.md edit + Python update
- Limited to Hermes-supported type system
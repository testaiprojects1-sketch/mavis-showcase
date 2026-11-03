# ADR 001: Use Hermes Agent over Custom Python Orchestrator

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Needed a personal AI agent runtime with: personality system, tool registry, persistent memory, extensibility, and active maintenance.

## Decision
Adopt `nousresearch/hermes-agent` as the runtime, customized via SOUL.md.

## Rationale
- Built-in personality system (SOUL.md) — non-technical editable
- Tool registry with schema validation
- Persistent memory (file-based + Supabase compatible)
- Extensible plugin architecture
- Active development by Nous Research
- Docker image available (`nousresearch/hermes-agent:latest`)

## Consequences
- Learning curve for Hermes-specific patterns
- Smaller ecosystem than LangChain/LangGraph
- Custom tool integration requires Hermes tool schema format
- Version upgrades may require SOUL.md migration
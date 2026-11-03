# ADR 003: Audit Log Design — Structured JSONL + Trace IDs

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Personal AI must maintain audit trail for accountability, debugging, and GDPR compliance (Art. 30 records of processing).

## Decision
Structured JSONL audit logs with UUID v7 `trace_id` propagated through all operations. Dual write: Loki (hot, 30 days) + PostgreSQL (cold, 7 years) + S3 (raw payloads, 90 days).

## Rationale
- `trace_id` enables end-to-end correlation across LLM calls, tools, memory writes
- JSONL is streaming-friendly, schema-evolvable, queryable
- Tiered storage balances cost vs. access patterns
- OpenTelemetry-compatible for future observability integration

## Consequences
- Storage volume (mitigated: compression, tiered retention)
- Schema evolution requires ADR process
- PII redaction pipeline needed before persistence
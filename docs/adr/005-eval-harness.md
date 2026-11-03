# ADR 005: Custom Eval Harness

**Date:** 2025-11-01
**Status:** Accepted
**Deciders:** Jane Riveros

## Context
Need regression testing, red-teaming, guardrail adherence validation, and cost regression detection for personal AI agent.

## Decision
Build custom eval harness in Python (pytest-based) with domain-specific thresholds. Runs in CI + nightly scheduled.

## Rationale
- Domain-specific thresholds (guardrail adherence = 100%, cost regression <20%)
- Hard gates: blocks deployment on regression/guardrail failure
- Red-team prompts version-controlled alongside code
- No external dependency for core governance function
- Extensible for future formal verification

## Consequences
- Maintenance burden (accepted: solo-owned, well-tested)
- No managed dashboard (mitigated: GitHub Actions summary)
- Must implement parallelization manually (pytest-xdist)
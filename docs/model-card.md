# MAVIS — Model Card

## Model Details
- **Model name:** MAVIS (Personal AI Assistant)
- **Version:** 2.0.0
- **Date:** November 2025
- **Owner:** Jane Riveros

## Intended Use
Personal AI assistant for daily productivity: email/calendar management, note-taking, research, file generation, voice I/O, task scheduling. Self-hosted, privacy-first.

## Limitations
- Single-tenant (designed for one user)
- No real-time voice conversation (push-to-talk only)
- English/Spanish only
- Requires self-hosted infrastructure (Docker)
- Not a replacement for professional advice (legal, medical, financial)

## Evaluation Results
| Suite | Pass Rate | Threshold | Status |
|-------|-----------|-----------|--------|
| Regression | 96% | 95% | ✅ Pass |
| Red-team | 0 critical | 0 critical | ✅ Pass |
| Guardrail adherence | 100% | 100% | ✅ Pass |
| Cost regression | +5% | <20% | ✅ Pass |

## Data Lineage
- User-provided: Messages, files, preferences, calendar/email data
- External APIs: Gmail, Calendar, Notion, Slack, ElevenLabs, DuckDuckGo
- Local processing: faster-whisper (STT), yt-dlp (video download)
- No training data collected; all inference via Anthropic/OpenAI APIs

## Governance
- Audit logging: Every turn traced via `trace_id`
- Eval harness: Runs on every PR + nightly
- Risk register: Reviewed monthly
- SOUL.md: Version-controlled personality + guardrails
- Model card: Updated per release
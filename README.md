# Kaam Ki Baat (KKB) 🗣️

**A multilingual voice AI agent that matches blue-collar workers to jobs across India.**

Kaam Ki Baat ("Talk of Work") conducts natural phone conversations in Hindi and Kannada to understand a worker's skills, experience, and preferences, then surfaces relevant job openings. It is built as a reusable capability on the [ONEST](https://onest.network/) / [Beckn](https://becknprotocol.io/) open network, designed to bring job discovery to workers who are more comfortable speaking than typing.

---

## Why KKB

India's blue-collar labour market is largely offline, voice-first, and multilingual. Text-based job portals exclude a huge share of workers who don't read fluently or navigate apps comfortably. KKB meets workers where they are — on a phone call, in their own language — and turns a spoken conversation into a structured profile that can be matched against live openings on an open network.

## What it does

- **Voice-first onboarding** — captures a worker's profile (skills, experience, location, availability, wage expectations) through a guided spoken conversation.
- **Multilingual** — supports Hindi and Kannada (ಕೆಲಸದ ಮಾತು), with the call flow and prompts localised per language.
- **Job matching on an open network** — connects to ONEST/Beckn so openings from multiple providers can be discovered, not just a single walled-garden listing.
- **Hallucination guards** — the agent is constrained to avoid inventing jobs, wages, or details not present in the data.
- **Post-call processing** — transcripts are processed after each call to extract structured fields and feed downstream matching and analytics.

## Architecture

> ⚠️ **Verify before publishing.** The components below reflect the project's known design. Confirm names, versions, and wiring against the actual code in this repo before this goes public.

| Layer | Component |
|---|---|
| Voice platform | Bolna AI / Raya |
| Speech | ASR + TTS (per-language conventions) |
| Extraction | LLM-based field extraction from transcripts |
| Retrieval | Pinecone vector index (`kkb-dkb-transcripts`, namespace `kkb`) |
| Post-call pipeline | Node.js service (Vercel-deployed) → Google Sheets (service account) |
| Network | ONEST / Beckn |

## Repository structure

> ⚠️ **Placeholder — replace with the real layout.**

```
.
├── prompts/          # Voice agent system prompts (Hindi, Kannada)
├── call-flows/       # Call flow / turn-structure definitions
├── pipeline/         # Post-call transcript processing
├── config/           # Platform (Bolna/Raya) configuration
└── docs/             # Pilot learnings, conventions, runbooks
```

## Getting started

> ⚠️ **Placeholder — fill in with the actual setup steps for this repo.**

```bash
# 1. Clone
git clone <repo-url>
cd kaam-ki-baat

# 2. Install dependencies
# <add command, e.g. npm install>

# 3. Configure environment (see below)
cp .env.example .env

# 4. Run / deploy
# <add command>
```

## Configuration

> ⚠️ **Placeholder — list the real environment variables this repo needs.**

| Variable | Purpose |
|---|---|
| `OPENAI_API_KEY` / `LLM_API_KEY` | Field extraction |
| `PINECONE_API_KEY` | Vector retrieval |
| `PINECONE_INDEX` | e.g. `kkb-dkb-transcripts` |
| `GOOGLE_SERVICE_ACCOUNT` | Sheets access for post-call data |
| `BOLNA_API_KEY` / `RAYA_*` | Voice platform |

## Localisation

Each supported language has its own prompt set and call flow. When adding or editing prompts, keep the turn structure and hallucination guards consistent across languages, and regression-test after every change — small wording shifts in voice prompts can change ASR/TTS behaviour in ways that aren't obvious from reading the text.

## Status

> ⚠️ **Update to reflect current state** — e.g. pilot / in production / experimental.

## Related

- **Dhandhe Ki Baat (DKB)** — the employer-facing companion agent for job posting and management.

## License

> ⚠️ **Add a license.** If this is intended as a digital public good, an open license (e.g. MIT or Apache-2.0) is the usual choice — but pick deliberately.

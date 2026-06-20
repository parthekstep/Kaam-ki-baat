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

## Localisation

Each supported language has its own prompt set and call flow. When adding or editing prompts, keep the turn structure and hallucination guards consistent across languages, and regression-test after every change — small wording shifts in voice prompts can change ASR/TTS behaviour in ways that aren't obvious from reading the text.

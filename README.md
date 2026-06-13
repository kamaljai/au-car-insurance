# au-car-insurance

**Author:** Kamalraj Jairam (KJ) — info@kamalraj.net

Australian comprehensive car insurance adviser skill for Claude Code and Claude.ai.

## Installation

```bash
npx skills add au-car-insurance
```

Or add it manually by cloning this repo into your skills directory:

```bash
git clone https://github.com/kamaljai/au-car-insurance ~/.claude/skills/au-car-insurance
```

## What it does

Guides users through a short, privacy-minimal interview, builds a state-aware insurer shortlist, searches for **current** pricing and PDS coverage (live data first, always), and presents a side-by-side comparison with honest provenance labels — as general information, not personal advice.

**Insurers covered:** Allianz, AAMI, Budget Direct, QBE, NRMA, plus the user's state motoring club (RACV in VIC, RACQ in QLD, RAA in SA, RAC in WA). Digital-only brands (Bingle, ROLLiN', etc.) are offered when lowest price is the top priority.

## Trigger phrases

Use this skill when a user:
- Asks about car insurance in Australia
- Wants to compare insurance providers or find the cheapest comprehensive cover
- Mentions renewing or switching their policy
- Asks about quotes for their car
- Asks which insurer is best

## How it works

The skill runs in six phases, governed by five non-negotiable rules (live data first, honest provenance, minimal PII, general information only, no hardcoded winners):

| Phase | Description |
|-------|-------------|
| 1 | **Interview** — grouped sections covering driver, vehicle, licence history, insurance history, and priorities. Privacy-minimal: asks year of birth + suburb/postcode only — never full name, exact DOB, gender, rego, or street address |
| 2 | **Location check** — validates the suburb + postcode + state combination only (street addresses are never sent to a search engine) |
| 3 | **State-aware shortlist** — 4 national insurers plus the relevant state motoring club(s); digital-only brands offered to price-first users |
| 4 | **Live data gathering** — mandatory web searches for current pricing, PDS limits, and promotions before any table is shown; every figure carries its source date and quoted profile |
| 5 | **Comparison output** — feature table and pricing summary with provenance headers; if no live data is found, says so plainly rather than substituting stale reference ranges |
| 6 | **Decision support** — maps the user's priorities to what the live data actually showed, including a dedicated renewal/loyalty-tax path for existing policyholders |

## Environment support

| Environment | Interview | Pricing method |
|-------------|-----------|---------------|
| Claude Code | `AskUserQuestion` for option-style questions; Playwright (if available) can open quote pages | `WebSearch`/`WebFetch` |
| Claude.ai / no browser | Grouped conversational questions | Web search for review/comparison articles |
| No web tools at all | Interview still runs | No dollar estimates given — clearly-labelled historical feature table + direct quote links only |

## Limitations

- Cannot retrieve real-time quotes — insurers require interactive form submissions. All prices are **estimates only**.
- Always directs users to get exact quotes directly from each insurer and read the current PDS.
- This skill provides general information only, not financial advice.

## PDS links

- [Allianz](https://www.allianz.com.au/my-allianz/policy-information/policy-documents.html#car)
- [AAMI](https://www.aami.com.au/policy-documents/comprehensive-car-insurance)
- [NRMA](https://www.nrma.com.au/policy-booklets)
- [Budget Direct](https://www.budgetdirect.com.au/car-insurance/policy-documents.html)
- [QBE](https://www.qbe.com/au/car-insurance/car-insurance-policy-documents)
- [RACV](https://www.racv.com.au) · [RACQ](https://www.racq.com.au) · [RAA](https://www.raa.com.au) · [RAC](https://rac.com.au)

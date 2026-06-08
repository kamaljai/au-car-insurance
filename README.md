# au-car-insurance

**Author:** Kamalraj Jairam (KJ) — info@kamalraj.net

Australian comprehensive car insurance adviser skill for Claude Code and Claude.ai.

## What it does

Guides users through a structured interview to gather their driver and vehicle details, validates their parking address, searches for current indicative quotes from five major Australian insurers, and presents a side-by-side comparison with a personalised recommendation.

**Insurers covered:** Allianz, NRMA, AAMI, Budget Direct, QBE

## Trigger phrases

Use this skill when a user:
- Asks about car insurance in Australia
- Wants to compare insurance providers or find the cheapest comprehensive cover
- Mentions renewing or switching their policy
- Asks about quotes for their car
- Asks which insurer is best

## How it works

The skill runs in six phases:

| Phase | Description |
|-------|-------------|
| 1 | **Information gathering** — structured interview across 7 sections (driver, vehicle, parking address, licence history, other drivers, insurance history, coverage preferences) |
| 2 | **Address validation** — verifies the overnight parking address via web search before proceeding |
| 3 | **Pricing search** — searches comparethemarket.com.au, finder.com.au, and insurer sites for current indicative quotes and promotions |
| 4 | **Coverage comparison** — side-by-side PDS feature table across all five insurers, highlighting user-requested features with ⭐ |
| 5 | **Pricing summary** — indicative annual premium ranges populated from search results (or reference ranges if no live data found) |
| 6 | **Recommendation** — personalised pick based on the user's stated priorities (budget, claims service, repairer choice, new car, etc.) |

## Environment support

| Environment | Pricing method | Address validation |
|-------------|---------------|-------------------|
| Claude Code (with Playwright) | `browser_navigate` + `browser_snapshot` on comparison sites | `WebSearch` |
| Claude.ai / no browser | `WebSearch` for review/comparison articles | `WebSearch` |

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

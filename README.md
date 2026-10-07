# Company Profiler

A Claude skill that researches a company and returns a sourced, one-page brief: founding date, stage and funding, products, how the company makes money, customers, go-to-market motion, AI usage and competitors.

I built it for my own job search. Before reaching out to someone at a company or applying for a role, I want to understand the business in a couple of minutes, and I want to be able to repeat what I read to a recruiter without it being wrong. So the skill is designed around accuracy over completeness: every figure is sourced and dated, inferences are labelled as inferences, and gaps are stated as gaps rather than filled in.

## What it produces

**Quick brief (default)** — about one page, in a fixed structure so briefs are comparable across companies:

1. A one-line summary of what the company does and for whom
2. A **snapshot table** with every key fact at a glance (founded, HQ, stage, latest funding, total raised, headcount, products, business model, customers, sales motion, AI usage, competitors). Unknown facts say "Not found" rather than disappearing, so gaps are visible.
3. Short sections that add only what the table can't hold: product, how they make money, customers and GTM, AI usage, competitors, recent news
4. **Confidence and gaps** — what's well sourced, what's inferred, where sources conflict, and the "as of" date
5. Numbered sources, referenced inline

**Deep dive** — triggered by "full profile", "deep dive" or "I have an interview". Same brief, plus leadership, funding history, pricing and unit-economics signals, technology and AI, competitive moat, hiring signals, culture signals, and risks.

## Design choices

- **Snapshot table first.** The reader should get the whole picture before any prose. Sections below the table are budgeted (e.g. 2–3 bullets for product, ~60–80 words for the revenue model) to stop the brief bloating with everything the research turned up.
- **"How they make money" must say who pays and how.** "B2B SaaS" isn't an answer. `references/business-model-guide.md` gives the model a classification table (per-seat, usage-based, take rate, marketplace, platform + services, enterprise licence, etc.) and the signals that point to each, so it can infer cautiously when pricing isn't public.
- **Source hierarchy and conflict handling.** Company site and dated press releases beat aggregators (Crunchbase, PitchBook, Growjo), which are often stale. When sources disagree on funding, headcount or founding year, the brief says so and gives the range instead of silently picking one.
- **Explicit hard cases.** Undisclosed stage, unstated revenue model, stealth or tiny companies, incorporation vs launch dates, public and acquired companies — each has a defined handling rule rather than being left to chance.
- **Final checks.** Before responding, the brief is checked against five rules: every stale-able figure is sourced and dated, nothing is invented, inferences are labelled, the revenue section names the payer and pricing, and the table is complete and first.
- **Scoped tightly.** It profiles the business only — no outreach drafts or talking points unless asked separately — and it won't trigger for stock analysis or profiling individuals.

## Structure

```
SKILL.md                          # Main instructions: modes, workflow, template, hard cases, final checks
references/
  business-model-guide.md         # How to classify a revenue model when it isn't stated
  deep-dive.md                    # Extra sections for "full profile" / interview prep
```

The references are loaded only when needed, which keeps the main skill short.

## Using it

Add the folder as a skill in Claude (claude.ai, the desktop app, or Claude Code under `.claude/skills/company-profiler/`). Then just ask naturally, e.g. "profile Stripe", "tell me about this company: <url>", or "deep dive on Monzo, I have an interview". The skill is written for my own use, so it refers to me by name; swap that for your own if you reuse it.

## Known limitations

- Quality depends on what's public. Private-company funding and headcount are often only available from aggregators, and the brief will flag lower confidence when that's all there is.
- Figures go stale quickly; each brief carries an "as of" date for that reason.
- It needs web search enabled to be useful.

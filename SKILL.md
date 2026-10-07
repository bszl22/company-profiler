---
name: company-profiler
description: Research and profile a company so the user can understand its business before reaching out to employees, applying for a role, or preparing for an interview. Produces a sourced one-page brief covering founding date, growth stage and funding, products, how the company makes money, customers, competitors, AI usage and go-to-market motion. Use this whenever the user asks to profile, research, "look into", "tell me about", "get up to speed on", or size up a company, startup or employer, or pastes a company name or URL and wants to understand what it does, even if they never say "profile". Also use for "full profile" or "deep dive" requests on a company. Do not use for stock analysis, writing outreach messages or cover letters, or profiling an individual person.
---

# Company Profiler

Bryan uses this skill to understand a company's business quickly and accurately, usually because he is considering reaching out to someone there or applying for a role. The value is a brief he can trust and skim in a couple of minutes. A wrong funding round or an invented revenue model is worse than a gap, because he may repeat it to a recruiter or hiring manager. Accuracy and honesty about what is unknown matter more than completeness.

This skill covers understanding the business only. Do not draft outreach messages, talking points or application material unless asked separately.

## Modes

- **Quick brief (default).** About one page. Use unless the user asks for more.
- **Deep dive.** Triggered by phrases like "full profile", "deep dive", "go deep", or "I have an interview". Produce the quick brief structure first, then add the sections in `references/deep-dive.md`.

If it is unclear which the user wants, deliver the quick brief and end with a one-line offer to go deeper.

## Workflow

1. **Identify the company.** If the name could match several companies (for example a generic word, or a company with an unrelated namesake), check the search results and pick the one that fits any context the user gave. If it is still ambiguous, state which company you assumed at the top of the brief in one line. Do not stall on a question when a reasonable assumption works.
2. **Read the user's links first.** Bryan often supplies useful URLs (company site, funding announcement, job posting, article). Fetch and read them before searching, since they reflect what he cares about. Treat them as sources like any other: cite them, and cross-check funding or headcount claims against a second source where possible.
3. **Search to fill the gaps.** Prioritise in this order: the company's own site (product, pricing, about, customers pages), funding announcements and reputable press, the company's job postings and careers page, then aggregator pages (Crunchbase, PitchBook, LinkedIn company page, Growjo and similar). Aggregators are useful for a first pass but are often stale or inconsistent, so do not rely on one alone for funding or headcount.
4. **Reconcile conflicts.** Sources often disagree on founding year, total funding, or headcount. Prefer the company's own statements and dated press releases over aggregators, note the discrepancy briefly, and give the range if it cannot be resolved.
5. **Write the brief** using the template below, then run the checks at the end of this file.

## Quick brief template

Use these headings in this order so briefs are comparable across companies. Write in plain sentences and short bullets, not long paragraphs.

**Length.** The whole brief, excluding the Sources list, should come in at about 600-700 words in quick mode. Research usually turns up far more than fits, and the temptation is to include all of it; resist that, because a long brief hides the table's clean picture and Bryan will not read it. Once the table has stated a fact, the sections below should only add explanation the cell could not hold. Budget roughly:

- Product: 2-3 bullets
- How they make money: one short paragraph (about 60-80 words)
- Customers and go-to-market: 2-3 bullets
- AI usage: 2-3 sentences
- Competitors: 2-3 one-line bullets
- Recent news: at most 3 dated bullets
- Confidence and gaps: at most 4 bullets. Name conflicts between sources here in one line each, and keep source-by-source detail out of the table cells (a cell shows the number you chose and one bracketed reference, plus "conflicting" if sources disagree).

If a section would only repeat the table, keep it to one sentence or drop it.

**The snapshot table comes first.** Bryan wants to take in the company at a glance before reading any detail, so the table directly under the one-line summary carries every key fact in short cells (a phrase or a number with its date, not a sentence). The sections below then add explanation and nuance and should not repeat the table verbatim. If a fact is unknown, write "Not found" in the cell rather than dropping the row, so gaps are visible.

```
# [Company name]
*[One sentence: what the company does and who it is for.]* Assumed company: [only if ambiguous]

## Snapshot
| | |
|---|---|
| **Founded** | [year] (by [founders]) [n] |
| **HQ** | [city, country] |
| **Stage** | [Seed / Series A-D / growth / PE-backed / public / bootstrapped / acquired] |
| **Latest funding** | [round, amount, date, lead investor] [n] |
| **Total raised** | [amount, or market cap for public companies] |
| **Headcount** | [approx, as of date, growth trend] [n] |
| **Key products** | [2-4 product names, each with a few words on what it does] |
| **Business model** | [who pays + how it is priced, in one line] |
| **Customers** | [target segment; 2-3 named customers if published] |
| **Sales motion** | [self-serve / product-led / sales-led / partner-led / mix] |
| **AI usage** | [core to the product / feature layer / minimal; one short phrase] |
| **Main competitors** | [2-3 names] |

## Product
[Explain what each product does and the problem it solves, in 2-4 bullets. Name products as the company does. Add only what the table cell could not hold.]

## How they make money
[Who pays, what they pay for, and how it is priced (subscription per seat, usage-based, transaction fee, services, marketplace take rate, licensing, hardware, etc.). Explain in plain language, say if pricing is not public, and label inferences.]

## Customers and go-to-market
[Segment detail, proof points, and how the company sells: direct, self-serve, partners. Include scale claims (customers, volume) with their dates.]

## AI usage
[Is AI the core of the product, a feature layer, or barely present? How does the company itself use AI internally if visible (e.g. blog posts, job descriptions)? Be specific and avoid buzzword repetition.]

## Competitors
[2-3 closest competitors and one line on how the company differs from each.]

## Recent news (last 6-12 months)
[2-4 dated bullets: funding, launches, partnerships, leadership changes, layoffs.]

## Confidence and gaps
[What is well sourced, what is inferred, and what could not be found, including conflicts between sources. Include the "as of" date of the research.]

## Sources
[Numbered list of links used. Reference them in the table and sections as [1], [2].]
```

In deep-dive mode, keep the same table at the top (add rows for "Leadership" and "Financials" if public), then the sections above, then the extra sections from `references/deep-dive.md`.

## How to handle the common hard cases

- **Stage is unclear or undisclosed.** Report what is confirmed (for example "Series B, $40M, announced March 2025") and say plainly that later rounds were not found. Do not infer a stage from headcount or valuation. For bootstrapped, PE-backed, public or acquired companies, use that as the stage and adapt the line (for example ticker and market cap for public companies, acquirer and date for acquired ones).
- **Revenue model is not stated.** Infer cautiously from the pricing page, product type and customer base, and mark it clearly as an inference ("appears to be usage-based, based on the pricing page"). Read `references/business-model-guide.md` for how to classify models and which signals to look for.
- **Very little information exists (stealth, tiny, or non-English market).** Produce a shorter brief with what is verified, be explicit about the gaps, and suggest where Bryan could learn more (for example the founders' interviews or talking to employees).
- **Founding year.** This is one of the first things Bryan wants, so make a real effort before writing "not found": check the company's About page, its incorporation record (Companies House in the UK, state registries in the US), Crunchbase or LinkedIn, and the first press coverage. Distinguish incorporation from public launch, because they often differ by a year; if they do, show both ("2020 incorporated, 2021 launched"). Only report a year as unconfirmed after those checks turn up nothing, and say which you tried.
- **Numbers that go stale.** Headcount and funding move quickly. Always give the date of the source next to the figure.
- **Public companies.** Add revenue, growth rate and profitability from the latest filing, with the period stated.

## Final checks before responding

Read the draft back against these. They exist because the brief is only useful if he can quote it safely.

1. Every funding, headcount, founding-date and customer claim traces to a source in the Sources list, with a date where the figure can go stale.
2. Nothing is invented to fill a section. A gap is stated as a gap.
3. Inferences are labelled as inferences.
4. The "How they make money" section says who pays and how, not just the product category.
5. The snapshot table is the first thing after the one-line summary, every row is filled or says "Not found", and the brief fits roughly one page in quick mode.

<h1 align="center">Intelligent Investor Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the investment methodology in Benjamin Graham's *The Intelligent Investor* into 16 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- You hold a stock and want to know whether this price gives you protection, but you can only compute a trailing one-year P/E and do not know how many years of average earnings should be the denominator
- You cannot say whether you belong on the defensive or the enterprising route, or you mix both — the book is explicit that there is no such thing as "a good half-operator"
- You want to run Graham's seven statistical criteria over a portfolio, but those numbers (22.5, 15×, 1.5×, 2:1) were parameters of the US market he wrote in, and you do not know which parts to keep and which must be re-standardized to current rates
- A market drop makes you want to sell everything and a rally makes you want to add — you lack a written-down volatility budget and a checklist for the moment it happens
- You can read net profit in a financial report but cannot tell whether "special charges", "fully diluted" and "multi-year average" are hiding watered-down earnings
- You cannot see that the late-bull-market moves that look different (buying new issues, chasing hot stocks, following "whatever works" systems) are really the same move

## What was distilled

16 capability cards, organized in the order "place yourself first, then read the market level, then take the defensive or enterprising route, and de-risk last":

- **Place yourself first**: `investor-type-selfcheck-skill` (investor type self-check and speculation isolation), `stock-bond-allocation-skill` (25%–75% stock/bond allocation and rebalancing discipline)
- **Market level and temperament**: `market-valuation-check-skill` (whole-market valuation check), `mr-market-discipline-skill` (Mr. Market volatility discipline)
- **Defensive route**: `defensive-stock-screen-skill` (defensive screening: four portfolio rules plus seven statistical criteria), `safety-margin-engine-skill` (margin-of-safety calculation and decision, including a behavioral self-check), `dca-index-portfolio` (dollar-cost averaging plus index funds), `fund-selection` (fund selection and sell signals)
- **Enterprising route**: `enterprising-bargain-hunting` (three enterprising strategies: low-P/E large caps, bargain net-nets, special situations), `graham-valuation-formula` (Graham valuation: simplified formula, two-step appraisal, bond coverage), `pairwise-company-comparison` (pairwise company comparison)
- **De-risking and accounting vigilance**: `eps-quality-check-skill` (earnings-per-share forensics and red flags), `convertible-warrant-skepticism` (convertible bonds and warrants), `dividend-shareholder-policy` (dividend policy and shareholder action)
- **Mania immunity and outside dependence**: `bubble-new-issue-immunity` (bull-market bubble symptoms and new-issue immunity), `advisor-diligence` (investment advisor due diligence)

## Two packaging modes: single and pack

The same 16 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `intelligent-investor-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 16 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 7 high-frequency cards become standalone skills; the other 9 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `investor-type-selfcheck-skill` — investor type self-check and speculation isolation
- `stock-bond-allocation-skill` — 25%–75% stock/bond allocation and rebalancing discipline
- `market-valuation-check-skill` — whole-market valuation check
- `mr-market-discipline-skill` — Mr. Market volatility discipline
- `defensive-stock-screen-skill` — defensive screening: four rules plus seven statistical criteria
- `safety-margin-engine-skill` — margin-of-safety calculation and decision
- `eps-quality-check-skill` — earnings-per-share forensics and red flags

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "which kind of investor am I / how do I split stocks and bonds / is the market expensive / should I sell after a drop / how do I screen stocks / does this price protect me / are the earnings real" | pack | Those are exactly the 7 promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: does this price give me protection?

**User question**

"This stock trades at 22. Last year's EPS was 1.8, so the P/E is only 12. Isn't that cheap? Can I buy?"

**How the skill reasons**

- It first hits the input contract of `safety-margin-engine-skill`: at least 7 years of EPS (including bad years), the current price, the high-grade bond rate, dilution data and an appraised value. With one year of earnings only → ask for the data; a single year must not stand in for the series
- Reconstruct earning power: 7–10 year average earnings (including special items) ÷ purchase price, on a fully diluted basis
- Route one: margin A = earning power % − bond rate %. The book's worked example is 9% earning power against a 4% bond rate, a 5-point annual gap, accumulating to about half the purchase price over ten years
- Route two: discount rate = market price ÷ appraised value; the book's requirement for the enterprising investor is ≤ 2/3
- Earnings-quality gate: if a boom-year single-year profit is mixed in, or an accounting red flag fires → hand over to `eps-quality-check-skill` and recompute the numerator
- Two closing steps: the diversification requirement (a margin on a single security is false safety) and the mirror test (what is the worst loss, and how many years at 10% to get back to even)

**Sample answer**

> A P/E of 12 uses last year's earnings, while this book always uses multi-year average earnings as the denominator — so do not call it cheap yet. Pull 7–10 years of EPS (bad years included) and recompute earning power on the average. If there was a "special charge" or a one-off gain in that window, clean the numerator with `eps-quality-check` first; otherwise you are measuring how cheap the best year was.
>
> Then run the two routes. The first is earning power minus the current high-grade bond rate: the book's example is 9% against 4%, a 5-point annual gap that accumulates to about half the purchase price over ten years. Note that 4% was the US bond rate where he wrote it; you must substitute the current rate for comparable bonds. After the substitution the gap may be zero or negative, and then the answer is "do not buy" — do not manufacture a cushion. The second route is the discount of price to appraised value, where the book draws the line for the enterprising investor at no more than 2/3 of appraised value — but appraised value has to come out of the valuation card, not out of thin air.
>
> The last step is the behavioral self-check: compute the worst case first (the book's example is a 98.4% loss, which takes more than 43 years to recover at 10% a year), then ask whether you can live with that outcome. If you cannot, it is a veto, not a reason to buy a smaller position. The card also requires diversification — a "margin of safety" on one stock alone is false safety. One more thing: the book gives no universal pass line for what counts as an adequate margin; it gives the 2/3 discount convention and the 9%-against-4% example, so that line is yours to set and write into the plan.

### Example 2: the market fell 20% in a week — should I sell everything?

**User question**

"The market fell 20% this week and my account is down 15%. Should I clear out and hide first?"

**How the skill reasons**

- `mr-market-discipline-skill` reframes the quote first: a quote is a service you may decline, not an instruction; price fluctuation has only two meanings for an investor — a big drop offers a chance to buy, a big rise offers a chance to sell
- Then the three questions for a decline, each answered in writing: (1) have the businesses changed (reports, operating data), or is only the quote falling? (2) is this decline inside the volatility range you accepted in advance? (3) has a pre-set rebalancing or averaging rule been triggered?
- The volatility budget comes from the book: over the next 5 years, a portfolio rising more than 50% above its low, or falling more than one third below its high, is normal
- If question 3 fires, hand over to `stock-bond-allocation-skill` and execute mechanically: buy back when the stock share has fallen to roughly 45%, recalibrating once every six months on a fixed date
- If the user cannot form any valuation basis at all, the card stops itself: fall back to an index-based defensive route, and do not use "ignore Mr. Market" as an excuse to sit on a losing position

**Sample answer**

> Separate two things first: what is falling — the quote, or the business? "Clear out and hide" is itself market timing, and the whole premise of this book is that the future cannot be predicted — any method built on prediction eventually decays. So work the three questions, and put the answers on paper.
>
> Question one: have the fundamentals changed? Have the reports and operating data deteriorated? If only the price is falling, that is not a reason to sell. Question two: is this 15% drawdown inside the volatility budget you wrote down in advance? The book's convention is that over the next 5 years a rise of more than 50% and a fall of more than one third are both normal — −15% has not reached that magnitude, so what it should trigger is the plan, not panic. Question three: has a rebalancing or averaging rule fired? If the stock share has already fallen to roughly 45%, the correct action is to buy back by the rule — that is a buy action, not a liquidation.
>
> The only real reason to sell is that the quote is clearly above the valuation you recorded. And if you have no valuation record at all and cannot estimate business value, this card stops itself: fall back to an index-based defensive route, and do not turn "ignore Mr. Market" into an excuse for riding a loss.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table
6. **Trigger and output testing** — write trigger cases and output evaluation scenarios for every card; failing cards go back for rework

How the book's numbers were handled also shapes the result: 22.5, 15×, 1.5×, 2:1, the 25%–75% band and the 9%-against-4% gap are all parameters of the US rate environment Graham wrote in, and he himself called them "arbitrary". So every card **keeps the structure and re-standardizes the numbers** — multi-year average earnings as the denominator, a multi-criteria funnel, the P/E × P/B product ceiling and a portfolio earnings yield anchored to the current bond rate all transfer; the specific figures must be recomputed against the current risk-free rate and market size, and the convention used must be declared on every output.

## Repository layout

```text
intelligent-investor-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification and promotion conclusions for the 16 units
├── single/                        ← single-entry build
│   └── intelligent-investor-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest and file hashes
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule quick reference
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← 16 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── intelligent-investor-skill-router/
│   │   ├── SKILL.md               ← source router entry
│   │   └── references/            ← 16 cards + indexes, called by the router
│   ├── investor-type-selfcheck-skill/
│   │   └── SKILL.md
│   ├── stock-bond-allocation-skill/
│   │   └── SKILL.md
│   ├── market-valuation-check-skill/
│   │   └── SKILL.md
│   ├── mr-market-discipline-skill/
│   │   └── SKILL.md
│   ├── defensive-stock-screen-skill/
│   │   └── SKILL.md
│   ├── safety-margin-engine-skill/
│   │   └── SKILL.md
│   └── eps-quality-check-skill/
│       └── SKILL.md
```

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/intelligent-investor-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r intelligent-investor-skill/single/intelligent-investor-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\intelligent-investor-skill\single\intelligent-investor-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

```bash
# macOS / Linux
cd intelligent-investor-skill/pack
cp -r intelligent-investor-skill-router \
      investor-type-selfcheck-skill \
      stock-bond-allocation-skill \
      market-valuation-check-skill \
      mr-market-discipline-skill \
      defensive-stock-screen-skill \
      safety-margin-engine-skill \
      eps-quality-check-skill ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\intelligent-investor-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('intelligent-investor-skill-router','investor-type-selfcheck-skill','stock-bond-allocation-skill','market-valuation-check-skill','mr-market-discipline-skill','defensive-stock-screen-skill','safety-margin-engine-skill','eps-quality-check-skill') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "Does this price give me a margin of safety, and how many years of average earnings should I use?" If the agent enters the two-route calculation of `safety-margin-engine-skill` instead of giving generic "it looks cheap" commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *The Intelligent Investor* by Benjamin Graham
- Distilled from the whole book, producing 16 capability cards

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (22.5, 15×, 1.5×, 2:1, the 25%–75% band, the 9%-against-4% earnings-to-bond gap, etc.) are parameters of the US rate environment Graham wrote in; he himself called them "arbitrary", and the book provides no statistical backtesting. Recompute them against the current risk-free rate and market size before using them in another market, and declare the convention you use. Nothing in this repository is investment advice.

## License

[MIT](./LICENSE)


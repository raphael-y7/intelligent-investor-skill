<h1 align="center">Intelligent Investor Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the investment decision system in Benjamin Graham's *The Intelligent Investor* into 16 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- You cannot say whether you belong to the defensive or the enterprising camp, so you end up running enterprising moves on a defensive allocation — the "half businessman" outcome the book warns about
- You want to add on every rally and sell on every drop, and you have no written plan that accepts a +50% / −33% swing in advance, so there is no discipline left when the drop arrives
- You want to screen stocks the Graham way, but which profit denominator each of the seven statistical criteria uses, and how the price-to-earnings × price-to-book product cap works, gets fuzzy the moment you start
- You cannot tell whether a purchase price actually carries protection: the earnings-yield spread over bond yields and the market-price discount to appraised value are two different measures for two different situations
- Special charges, acquisitions and option dilution make reported earnings look fine, and you do not know which line to audit backwards from
- You hold one fund or one advisor recommendation and cannot rank fees, track record and conflicts of interest in the right order

## What was distilled

16 capability cards, organized in the order "split by investor type first, allocate second, screen third, compute the margin last":

- **Type split and allocation** (4 cards): `investor-type-selfcheck-skill` (investor type self-check and speculation segregation), `stock-bond-allocation-skill` (25%–75% stock/bond allocation and rebalancing discipline), `market-valuation-check-skill` (whole-market valuation check), `mr-market-discipline-skill` (Mr. Market volatility discipline)
- **Defensive screening and valuation** (4 cards): `defensive-stock-screen-skill` (four rules plus seven statistical criteria), `eps-quality-check-skill` (earnings-quality forensics and financial red flags), `graham-valuation-formula` (simplified formula, two-step appraisal, bond coverage), `safety-margin-engine-skill` (margin-of-safety calculation and decision, with a behavioral self-check)
- **Enterprising route and side-by-side comparison** (3 cards): `enterprising-bargain-hunting` (low-P/E large caps, cheap net-nets, special situations), `pairwise-company-comparison` (paired company comparison), `convertible-warrant-skepticism` (convertibles and warrants skepticism)
- **Passive route and outside dependencies** (3 cards): `dca-index-portfolio` (dollar-cost averaging plus index funds), `fund-selection` (fund selection and sell signals), `advisor-diligence` (investment advisor due diligence)
- **Market cycle and shareholder relations** (2 cards): `bubble-new-issue-immunity` (bubble symptoms and new-issue immunity), `dividend-shareholder-policy` (dividend policy and shareholder action)

> 16 cards in total: 7 promoted (compiled into standalone skills in the pack) + 9 router (kept inside the router entry). The slugs match the `capabilities` list in `bundle/verified.yaml` one for one.

## Two packaging modes: single and pack

The same 16 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `intelligent-investor-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 16 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 7 high-frequency cards become standalone skills; the other 9 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `investor-type-selfcheck-skill` — investor type self-check and speculation segregation
- `stock-bond-allocation-skill` — 25%–75% stock/bond allocation and rebalancing discipline
- `market-valuation-check-skill` — whole-market valuation check
- `mr-market-discipline-skill` — Mr. Market volatility discipline
- `defensive-stock-screen-skill` — defensive screening: four rules plus seven statistical criteria
- `safety-margin-engine-skill` — margin-of-safety calculation and decision
- `eps-quality-check-skill` — earnings-quality forensics and financial red flags

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "defensive or enterprising / how to split stocks and bonds / is the market expensive / should I sell in a drop / screen this stock by the criteria / does this price carry protection / is the earnings number clean" | pack | Those are exactly the 7 promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: a blue chip that does not look expensive — does it pass Graham's screen?

**User question**

"This blue chip has averaged a P/E of 14 over the past three years and trades at 1.6× book. It has paid dividends for 15 straight years and has never posted a loss. Does it pass Graham's criteria?"

**How the skill reasons**

- First `investor-type-selfcheck-skill`: confirm the user is on the defensive track (the three enterprising strategies have completely different thresholds and must not be mixed in)
- Then `defensive-stock-screen-skill`: check the seven criteria one by one — size, financial condition (current ratio ≥ 2:1 and long-term debt ≤ working capital for an industrial), earnings record (a profit in each of the past 10 years), dividend record (uninterrupted for ≥ 20 years), growth (10-year EPS growth ≥ one third), and the price tests (P/E ≤ 15, P/B ≤ 1.5, and the product of the two ≤ 22.5)
- Cross-check with `eps-quality-check-skill`: the denominator must be multi-year average earnings; look first for special charges, acquisitions or option dilution inflating EPS
- Finally `safety-margin-engine-skill`: compute the earnings-yield spread over high-grade bond yields, and the discount of market price to appraised value

**Sample answer**

> Do not call it a pass yet. Of the two numbers you gave, 14 × 1.6 = 22.4, which just squeezes inside the 22.5 product line; but P/B 1.6 alone breaks the 1.5 cap — the book's rule is that when the P/E is below 15 the P/B may be relaxed under the product test, so you must state that you are using the product convention rather than passing every item individually. The second question matters more: which year's earnings produced that 14×? If it is the trailing twelve months, it has to be replaced with the average of the past three years, and the P/E usually moves once you swap the denominator. Third, 15 years of dividends is not enough — the original text requires 20 consecutive years, and where market history is shorter the commentary allows 10–20 years, but you have to write that declaration into the conclusion. One last warning: these numbers (22.5, 15×, 1.5×, 2:1) are 1972 US parameters under a 7.5% AA bond yield. Before using them in another market, re-scale them to the current risk-free rate — keep the structure, do not port the numbers. **Passing all seven is only a first screen, not a buy reason** — next comes the margin of safety: divide the average earnings of the past 7–10 years by the purchase price and see how far the earnings yield clears the current high-grade bond yield (the book's baseline example is 9% versus 4%, roughly 5% a year, about half the purchase price accumulated over ten years); or use market price ÷ appraised value ≤ 2/3. If the cushion is not there, do not buy — and diversify across 10–30 names, because a margin on a single security without diversification is a false margin.

### Example 2: the market is down more than 20% — should I sell everything?

**User question**

"The market is down 25% from its high and my account is deep in the red. Should I go to cash and sit it out?"

**How the skill reasons**

- `mr-market-discipline-skill`: run the three down-market questions — did the businesses' fundamentals change, is the drop inside the range you accepted in advance, and did an agreed rebalancing or DCA rule trigger
- `stock-bond-allocation-skill`: check the target ratio and the rebalancing trigger, turning "should I sell" into "is the ratio off plan"
- `market-valuation-check-skill`: read only if the user still wants to judge "is it cheap enough", using the portfolio earnings yield against high-grade bond yields — never a price-level forecast
- Stop rule: if the user asks "where is the bottom", switch to the discipline framework and give no price level

**Sample answer**

> Split "sell everything" into two questions: did the fundamentals change, and is the ratio off target. The first of the three down-market questions is — have the financials and operating data of the companies you hold deteriorated? If only the quote is falling, the book is direct: a price decline alone is not a reason to sell. Second, what volatility range did you accept in advance? The book asks investors to accept in advance that a portfolio may swing by roughly +50% / −33% within five years; −25% is still inside that line, so the plan should reassure you rather than trigger an action. The third question is the executable part: check your target stock/bond ratio. Suppose you set 50/50 and after the drop the stock share has fallen to about 45%, which trips the 5-percentage-point band — the correct action is **rebalancing in the opposite direction**: sell bonds, buy stocks back, and restore the ratio to within ±2 percentage points of target, not go to cash. Recalibrate on a fixed date about every six months; do not watch it daily. If you cannot execute that discipline, the original position was already beyond your tolerance, and the way out is back inside the 25%–75% band or into index funds — not ducking this time and repeating the mistake next time.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application; this first produces a list of 20 key tasks
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text; 184 candidates in total here
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (V1 source sufficiency), an executable input/output contract (V2 executability), and the ability to answer questions the book never explicitly addresses (V3 task gain); a five-criteria promotion gate is layered on top
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table
6. **Trigger and output testing** — design trigger blind tests and output evaluation scenarios for every card; failing cards go back for rework

The 184 candidates merged into 16 capability units (7 promoted + 9 router), covering all 20 key tasks in BOOK_OVERVIEW. One deliberate downgrade is worth noting: `bubble-new-issue-immunity` passed all five promotion criteria, but to keep the entry list uncrowded it was kept in the router in this build.

## Repository layout

```text
intelligent-investor-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── INDEX.md                       ← skill map: capability table + dependencies + loading order
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification conclusions for the 16 capability units
├── bundle/                        ← source material (audit and recompilation only, not loaded at runtime)
│   ├── verified.yaml              ← full definitions and promotion-gate records for the 16 capabilities
│   ├── cards/                     ← the 16 capability cards in their original form
│   └── book/                      ← overview.md + glossary.md
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

Ask: "Does this stock pass Graham's seven criteria, and does the purchase price carry a margin of safety?" If the agent enters the defensive screening and margin-of-safety calculation flow instead of giving generic value-investing commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *The Intelligent Investor* by Benjamin Graham

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (the seven statistical criteria, 22.5, 15×, 1.5×, the 25%–75% stock/bond band, the +50% / −33% volatility expectation, etc.) are experience-based parameters from the 1972 US market environment, described by the author himself as "arbitrary"; no statistical backtesting is provided. Before using them in another market, re-scale them to the current risk-free rate and market size and keep only the structure. Nothing in this repository is investment advice.


## License

[MIT](./LICENSE)

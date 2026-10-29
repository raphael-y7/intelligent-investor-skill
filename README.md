<h1 align="center">聪明的投资者 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把本杰明·格雷厄姆《聪明的投资者》中的投资决策体系，蒸馏成 16 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 说不清自己到底该做防御型还是积极型，于是防御的仓位配着积极的操作，成了书里警告的"半个经营者"
- 一涨就想加仓、一跌就想清仓，缺一套"事前就接受 +50% / −33% 波动"的书面预案，跌到位时没有纪律可依
- 想按格雷厄姆标准选股，但七项统计标准各用哪个利润口径、市盈率与市净率的乘积上限怎么算，一动手就含糊
- 算不清"这个买价到底有没有保护"：盈利能力对债券利率的差额、市价对评估价值的折扣，两条口径各管什么场景
- 财报里的特殊费用、并购、期权稀释把每股收益做得很漂亮，不知道该从哪一项开始往回查
- 手里只有一份基金或一份顾问推荐，分不清费用、业绩与利益冲突该怎么排序核查

## 蒸馏了什么

16 张能力卡，按"先分流、再配置、再选股、最后算边际"的顺序组织：

- **分流与配置**（4 张）：`investor-type-selfcheck-skill`（投资者类型自测与投机隔离）、`stock-bond-allocation-skill`（股债 25%~75% 配置与再平衡纪律）、`market-valuation-check-skill`（市场整体估值检查）、`mr-market-discipline-skill`（市场先生波动应对纪律）
- **防御型选股与估值**（4 张）：`defensive-stock-screen-skill`（四大规则＋七项统计标准）、`eps-quality-check-skill`（每股收益辨伪与财务红旗）、`graham-valuation-formula`（简化公式＋两步评估＋债券保障倍数）、`safety-margin-engine-skill`（安全边际测算与决策，含行为自检）
- **积极型与横向比较**（3 张）：`enterprising-bargain-hunting`（低市盈率大公司 / 廉价 net-net / 特殊情况三策略）、`pairwise-company-comparison`（成对公司比较分析法）、`convertible-warrant-skepticism`（可转债与权证怀疑框架）
- **被动路线与外部依赖**（3 张）：`dca-index-portfolio`（定投＋指数基金自动组合）、`fund-selection`（基金挑选与卖出信号）、`advisor-diligence`（投资顾问尽调）
- **市场周期与股东关系**（2 张）：`bubble-new-issue-immunity`（牛市泡沫症状与新股免疫）、`dividend-shareholder-policy`（股息政策与股东行动）

> 合计 16 张：7 张 promoted（pack 里独立成 skill）＋ 9 张 router（留在路由入口内）。slug 与 `bundle/verified.yaml` 的 `capabilities` 逐条对应。

## 两种打包模式：single 与 pack

同一套 16 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`intelligent-investor-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 16 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张高频卡各自独立成 skill；其余 9 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `investor-type-selfcheck-skill` — 投资者类型自测与投机隔离
- `stock-bond-allocation-skill` — 股债 25%~75% 配置与再平衡纪律
- `market-valuation-check-skill` — 市场整体估值检查
- `mr-market-discipline-skill` — 市场先生波动应对纪律
- `defensive-stock-screen-skill` — 防御型选股：四大规则＋七项统计标准
- `safety-margin-engine-skill` — 安全边际测算与决策
- `eps-quality-check-skill` — 每股收益辨伪与财务红旗

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"我该防御还是积极 / 股债怎么配 / 大盘贵不贵 / 跌了要不要卖 / 按标准筛股 / 买价有没有保护 / 财报有没有水分" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：一只白马股看着不贵，能不能按格雷厄姆标准买

**用户问题**

"这只白马股过去 3 年平均市盈率 14 倍、市净率 1.6 倍，连续分红 15 年，财报也没亏过。按格雷厄姆的标准算过关吗？"

**skill 如何判断**

- 先过 `investor-type-selfcheck-skill`：确认用户走的是防御型通道（积极型的三策略门槛完全不同，不能混用）
- 进 `defensive-stock-screen-skill`：逐项核七项标准——规模、财务（工业企业流动比率 ≥2:1 且长期债务 ≤ 营运资本）、利润记录（10 年每年均有利润）、股息记录（连续 ≥20 年）、增长（10 年 EPS 增长 ≥1/3）、价格关（PE ≤15、PB ≤1.5、两乘数之积 ≤22.5）
- 交叉 `eps-quality-check-skill`：分母必须是多年平均利润，先看有没有特殊费用、并购、期权稀释把 EPS 做高
- 最后 `safety-margin-engine-skill`：算盈利能力对高等级债息的差额，以及市价对评估价值的折扣

**最终回答示例**

> 先别急着说"过关"。你给的两个数里，14 × 1.6 = 22.4，刚好压在 22.5 这条乘积线以内；但单独的 PB 1.6 已经越过了 1.5 的上限——书里的规则是"市盈率低于 15 倍时，市净率可按乘积放宽"，所以这一项要写明你用的是乘积口径，而不是逐条都过。第二个问题更关键：14 倍这个数是拿哪年的利润算的？如果是最近 12 个月，就要换成过去 3 年平均利润；分母一换，PE 通常会变。第三，分红 15 年不够——原书要求连续付息 20 年，市场历史不足时可按点评口径放宽到 10~20 年，但你要把这句声明写进结论。最后提醒一句：这些数字（22.5、15 倍、1.5 倍、2:1）都是 1972 年美国 AA 债息 7.5% 环境下的参数，A 股用之前得按当期无风险利率重标定，结构可以留，数字不能直接搬。**通过七项只是初筛，不是买入理由**——接下来还要过安全边际：把过去 7~10 年平均利润除以买价，看盈利能力比当期高等级债息高出多少（书里的基准例子是 9% 对 4%，每年约 5%，十年累积约达买价一半）；或者按市价 ÷ 评估价值 ≤2/3 算折扣。缓冲不够就不买，而且必须分散到 10~30 只，单券的边际是伪安全。

### 示例 2：大盘跌了两成多，该不该清仓

**用户问题**

"大盘从高点跌了 25%，账户浮亏不少，是不是该先清仓躲一躲？"

**skill 如何判断**

- `mr-market-discipline-skill`：走跌时三问——企业基本面变了吗、跌幅是否在事前接受的区间内、是否触发了既定的再平衡或定投规则
- `stock-bond-allocation-skill`：核对目标比例与再平衡触发线，把"要不要卖"转成"比例偏没偏离计划"
- `market-valuation-check-skill`：只在用户还想判断"跌到位没有"时补读，用组合盈利收益率对高等级债息给水位，不给点位预测
- 判停：用户若要求"跌到哪是底"，转入纪律框架，不给点位

**最终回答示例**

> 先把"清仓"这个动作拆成两个问题：基本面变了没有，比例偏了没有。跌时三问的第一问是——你手里这些公司的财报和经营数据变差了吗？如果只是报价在跌，书里的结论很直接：仅仅价格下降不构成卖出理由。第二问，你事前接受的波动区间是多少？书里要求投资者事先就接受组合在 5 年内出现 +50% / −33% 量级的波动，−25% 还在这条线以内，那就该用预案安抚自己，而不是触发操作。第三问才是可执行的部分：查你的股债目标比例。假设你定的是 50/50，跌完之后股票占比掉到 45% 附近，触发了 5 个百分点的偏移线，正确动作是**反向再平衡**——卖出债券、补回股票，把比例调回目标 ±2 个百分点以内，而不是清仓。频率上按每 6 个月一次的固定日期校准即可，别每天看。如果这套纪律你执行不了，说明当初的仓位本身就超出了你的承受力，出路是回到 25%~75% 区间甚至指数化，而不是这次先躲过去、下次再犯。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解，先产出 20 条关键任务清单
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元，本共产出 184 条候选
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（V1 来源充分性）、能给出可执行的输入输出契约（V2 可执行性）、能回答书中未明说的新问题（V3 任务增益）；再叠一道五判据晋级门
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为每张卡设计触发盲测题与输出评测场景，未通过的卡回炉重做

184 条候选最终合并为 16 个能力单元（7 promoted ＋ 9 router），覆盖 BOOK_OVERVIEW 里的全部 20 条关键任务。有一处主动降级值得说明：`bubble-new-issue-immunity` 的五项晋级判据虽然全真，但为避免入口拥挤，本版主动把它留在 router 里。

## 仓库结构

```text
intelligent-investor-skill/
├── README.md              ← 你正在看的
├── README.en.md           ← English version
├── LICENSE                ← MIT
├── BOOK_OVERVIEW.md       ← 阶段 0 产出：全书 Adler 分析
├── DIGEST.md              ← 阶段 5 产出：面向读者的整书精华长文
├── INDEX.md               ← 阶段 3 产出：skill 总览 + 依赖关系
├── verified.md            ← 通过三重验证的 16 个单元
├── coverage-audit.md      ← 阶段 1.5 产出：原书任务覆盖审计
├── needs-review.md        ← 阶段 1.5 产出：待核查事项与缺口
├── TEST_SUMMARY.md        ← 阶段 4 产出：压力测试摘要
├── CANGJIE_ADAPTATION.md  ← 仓颉适配说明
├── GITHUB_REPO.md         ← 仓库元数据
├── candidates/            ← 阶段 1 产出：原始候选池
│   ├── frameworks.md      ← 框架与方法候选
│   ├── principles.md      ← 原则 / 规则 / 计算候选
│   ├── cases.md           ← 书中案例候选
│   ├── counter-examples.md← 反例与边界候选
│   └── glossary.md        ← 术语候选
├── rejected/              ← 阶段 1.5 产出：被淘汰的单元 + 原因
├── bundle/                ← 编译事实源
│   ├── verified.yaml      ← 能力元数据、判据与去向
│   ├── cards/             ← 能力卡源文件（六段结构）
│   └── book/              ← overview.md + glossary.md
├── single/                ← single 模式（1 个入口 + 全部能力卡）
│   └── intelligent-investor-skill/SKILL.md  ← 入口：触发 + 路由表 + 加载规则
└── pack/                  ← pack 模式（1 个路由入口 + 7 个晋级 skill）
    └── */SKILL.md         ← 8 个 skill，每个附带 test-prompts.json
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/intelligent-investor-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r intelligent-investor-skill/single/intelligent-investor-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\intelligent-investor-skill\single\intelligent-investor-skill "$env:USERPROFILE\.agents\skills\"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

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

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"这只股票按格雷厄姆的七项标准能过吗、买价有没有安全边际"，看 agent 是否直接进入防御型选股的逐项核验与安全边际核算，而不是给你一段泛泛的价值投资道理。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《聪明的投资者》本杰明·格雷厄姆 著

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（七项统计标准、22.5、15 倍、1.5 倍、25%~75% 股债区间、+50% / −33% 波动预期等）都是 1972 年美国市场环境下的经验参数，原书自认"主观武断"，未提供统计回测背书；跨市场使用须按当期无风险利率与市场规模重标定，只可保留结构。本仓库内容不构成投资建议。


## License

[MIT](./LICENSE)

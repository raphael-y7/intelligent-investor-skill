<h1 align="center">聪明的投资者 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把本杰明·格雷厄姆《聪明的投资者》中的投资方法论，蒸馏成 16 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 手里有一只股票，想知道"这个价格买有没有保护"，却只算得出一年期的市盈率，不知道该用几年平均利润做分母
- 说不清自己该走防御型还是积极型，或者干脆两条路线混着做——书里明说没有"较好的半个经营者"这种中间态
- 想按格雷厄姆的七项标准筛一遍组合，但那几个数字（22.5、15 倍、1.5 倍、2:1）是他写作时美国市场的参数，不知道哪些该保留、哪些必须按当期利率重标定
- 大盘一跌就想清仓、一涨就想加仓，缺一套事前写好的波动预算，和涨跌当下的检查表
- 看财报只看得懂净利润，分不清"特殊费用""完全稀释""多年平均"背后是不是注了水
- 分不清牛市后期那些看起来各不相同的动作（打新股、追热门、跟"只要管用"的战法）其实是同一件事

## 蒸馏了什么

16 张能力卡，按"先定位自己、再看大盘水位、然后走防御或积极路线、最后排雷"的顺序组织：

- **先定位自己**：`investor-type-selfcheck-skill`（投资者类型自测与投机隔离）、`stock-bond-allocation-skill`（股债 25%~75% 配置与再平衡纪律）
- **看大盘水位与情绪**：`market-valuation-check-skill`（市场整体估值检查）、`mr-market-discipline-skill`（市场先生波动应对纪律）
- **防御型路线**：`defensive-stock-screen-skill`（防御型选股：四大规则 + 七项统计标准）、`safety-margin-engine-skill`（安全边际测算与决策，含行为自检）、`dca-index-portfolio`（定投 + 指数基金自动组合）、`fund-selection`（基金挑选与卖出信号）
- **积极型路线**：`enterprising-bargain-hunting`（积极型三策略：低市盈率大公司 / 廉价 net-net / 特殊情况）、`graham-valuation-formula`（格雷厄姆估值：简化公式 + 两步评估 + 债券保障倍数）、`pairwise-company-comparison`（成对公司比较分析法）
- **排雷与会计警惕**：`eps-quality-check-skill`（每股收益辨伪与财务红旗）、`convertible-warrant-skepticism`（可转债与权证怀疑框架）、`dividend-shareholder-policy`（股息政策与股东行动）
- **狂热免疫与外部依赖**：`bubble-new-issue-immunity`（牛市泡沫症状与新股免疫）、`advisor-diligence`（投资顾问尽调）

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
- `defensive-stock-screen-skill` — 防御型选股：四大规则 + 七项统计标准
- `safety-margin-engine-skill` — 安全边际测算与决策
- `eps-quality-check-skill` — 每股收益辨伪与财务红旗

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"我是哪种投资者 / 股债怎么配 / 大盘贵不贵 / 跌了要不要卖 / 怎么筛股 / 买价有没有保护 / 利润真不真" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：这个价格买，有没有保护

**用户问题**

"某只票现价 22 元，去年每股收益 1.8 元，市盈率才 12 倍，是不是很便宜，可以买？"

**skill 如何判断**

- 先撞上 `safety-margin-engine-skill` 的输入契约：它要 ≥7 年（含差年份）的每股收益序列、当期市价、高等级债券利率、稀释工具数据、评估价值。只有单年利润 → 先索取数据，不得以单年利润代替
- 还原盈利能力：7~10 年平均利润（含特殊损益）÷ 买价，完全稀释口径
- 口径一：边际 A = 盈利能力% − 债券利率%。书里算例是盈利能力 9%、债息 4%，年差 5%，十年累积约达买价的一半
- 口径二：折扣率 = 市价 ÷ 评估价值，书里对积极型给的要求是 ≤ 2/3
- 利润质量门：混入繁荣期单年利润、或触发会计红旗 → 转 `eps-quality-check-skill` 重算分子
- 收尾两道：分散化要求（单券边际是伪安全）＋ 镜子测试（最坏亏多少、按 10% 年化要几年回本）

**最终回答示例**

> 12 倍市盈率用的是去年一年的利润，而这本书的分母一律是多年平均利润，所以先别急着叫它便宜。把 7~10 年的每股收益（含差年份）拉出来，用平均利润重算盈利能力；这段期间若有一笔"特殊费用"或一次性收益，先用 `eps-quality-check` 把分子还原干净——否则你算的是"最好那一年"的便宜。
>
> 然后走两条口径。第一条是盈利能力减当期高等级债券利率：书里的算例是 9% 对 4%、每年 5%、十年累积约达买价的一半。注意 4% 是他写作时美国的债息，你必须换成当期同类债券利率再算；换完之后差额可能为零甚至为负，那时结论就是"不买"，不要硬凑缓冲。第二条是市价对评估价值的折扣率，书里给积极型划的线是买价不高于评估价值的 2/3——但评估价值本身要靠估值卡算出来，不能拍脑袋。
>
> 最后一道是行为自检：先算最坏情况（书里的算例是亏 98.4% 之后，按 10% 年化要 43 年多才回本），再问自己这个后果能不能承受。承受不了就是一票否决，而不是把仓位调小一点继续买。另外这张卡明确要求配分散化——只拿一只股票的"安全边际"是伪安全。顺带说一句：书里没有给出一个"多少算合格"的普适安全边际百分比，只给了 2/3 这个折扣口径和 9% 对 4% 的算例，这条线要你自己定并写进预案。

### 示例 2：大盘一周跌 20%，要不要清仓

**用户问题**

"大盘一周跌了 20%，账户浮亏 15%，是不是该先清仓躲一躲？"

**skill 如何判断**

- `mr-market-discipline-skill` 先把报价定性：报价是可拒绝的服务，不是指令；价格波动对投资者只有两个意义——大跌之后是买入机会、大涨之后是卖出机会
- 走"跌时三问"，每问必须书面作答：① 持股企业的基本面变了吗（财报、经营数据），还是只有报价在跌？② 本次跌幅是否在你事前接受的波动区间内？③ 是否触发了既定的再平衡 / 定投规则？
- 波动预算取自书里的口径：今后 5 年内，组合比最低点高出 50% 以上、比最高点低三分之一以上，都属于正常现象
- 第 3 问若命中，转 `stock-bond-allocation-skill` 机械执行：股票占比跌到约 45% 时反向买回，半年一次固定日期校准
- 若用户根本形成不了估值依据，这张卡自己判停：退回指数化的防御路线，不能拿"不理会市场先生"当死扛的理由

**最终回答示例**

> 先分清两件事：跌的是报价，还是企业。"先躲一躲"这个动作本身就是择时，而这本书的整个前提是未来不可预测——凡以预测为基础的方法终将自我衰减。所以按三问走，答案要落纸。
>
> 第一问：企业基本面变了吗？财报、经营数据有没有转坏？如果只有价格在跌，那不构成卖出理由。第二问：这次 15% 的浮亏，在不在你事前写下的波动预算里？书里的口径是"今后 5 年内涨 50% 以上、跌三分之一以上都属正常"——−15% 还没到那个量级，它该触发的是预案，不是恐慌。第三问：有没有触发再平衡或定投规则？如果股票占比已经跌到 45% 附近，正确的动作是按纪律反向买回，那是买方动作，不是清仓。
>
> 真正构成卖出依据的只有一条：报价已经明显高于你记录的估值。而如果你手上根本没有估值记录、也算不出企业价值，这张卡会直接判停——先退回指数化的防御路线，别把"不理会市场先生"当成套牢死扛的借口。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为每张卡设计触发用例与输出评测场景，未通过的卡回炉重做

这本书的数值处理也影响蒸馏结果：22.5、15 倍、1.5 倍、2:1、25%~75%、9% 对 4% 全是格雷厄姆写作时美国利率环境下的参数，他本人称其"主观武断"。所以能力卡一律**保留结构、重标定数字**——多年平均利润做分母、多标准漏斗、市盈率 × 市净率乘积上限、组合盈利收益率锚定当期债息这些骨架可迁移，具体数字必须按当期无风险利率与市场规模重算，并在每次输出时声明所用口径。

## 仓库结构

```text
intelligent-investor-skill/
├── README.md                      ← 你正在看的
├── README.en.md                   ← English version
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                    ← 16 个能力单元的三重验证与晋级结论
├── single/                        ← 单一入口模式
│   └── intelligent-investor-skill/
│       ├── SKILL.md               ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json    ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md        ← 整书概览
│           ├── capability-index.md  ← 完整意图与关键词索引
│           ├── cheatsheet.md      ← 决策规则速查
│           ├── glossary.md        ← 术语表
│           └── capabilities/      ← 16 张能力卡
├── pack/                          ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── intelligent-investor-skill-router/
│   │   ├── SKILL.md               ← 来源路由入口
│   │   └── references/            ← 16 张卡 + 索引，供 router 内部调用
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

装完问一句"这个价格买有没有安全边际、该拿几年平均利润算"，看 agent 是否直接进入 `safety-margin-engine-skill` 的口径一 / 口径二测算，而不是给你一段泛泛的"低估值买入"。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《聪明的投资者》本杰明·格雷厄姆 著
- 全书蒸馏，共产出 16 张能力卡

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（22.5、15 倍、1.5 倍、2:1、25%~75% 比例、盈利能力 9% 对债息 4% 的差额等）都是格雷厄姆写作时美国市场利率环境下的参数，他本人称其"主观武断"，原书未提供统计回测背书；跨市场使用须按当期无风险利率与市场规模重标定，并在输出时声明所用口径。本仓库内容不构成投资建议。

## License

[MIT](https://opensource.org/licenses/MIT)

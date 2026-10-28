# Skill 地图 — 聪明的投资者

本文件由 `bundle/verified.yaml` 直接生成，是 16 张能力卡的总目录：哪张卡管什么、重要度多少、在 pack 模式下它被编译成独立 skill 还是留在路由入口里，以及卡与卡之间该按什么顺序读。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| `cap.intelligent-investor-4e.investor-type-selfcheck` | `investor-type-selfcheck-skill` | 投资者类型自测与投机隔离 | 关键 | promoted → 独立 skill |
| `cap.intelligent-investor-4e.stock-bond-allocation` | `stock-bond-allocation-skill` | 股债25%~75%配置与再平衡纪律 | 关键 | promoted → 独立 skill |
| `cap.intelligent-investor-4e.market-valuation-check` | `market-valuation-check-skill` | 市场整体估值检查 | 高 | promoted → 独立 skill |
| `cap.intelligent-investor-4e.mr-market-discipline` | `mr-market-discipline-skill` | 市场先生波动应对纪律 | 关键 | promoted → 独立 skill |
| `cap.intelligent-investor-4e.defensive-stock-screen` | `defensive-stock-screen-skill` | 防御型选股：四大规则＋七项统计标准 | 关键 | promoted → 独立 skill |
| `cap.intelligent-investor-4e.safety-margin-engine` | `safety-margin-engine-skill` | 安全边际测算与决策（含行为自检） | 关键 | promoted → 独立 skill |
| `cap.intelligent-investor-4e.eps-quality-check` | `eps-quality-check-skill` | 每股收益辨伪与财务红旗 | 高 | promoted → 独立 skill |
| `cap.intelligent-investor-4e.dca-index-portfolio` | `dca-index-portfolio` | 定投＋指数基金自动组合 | 高 | router → 路由入口 |
| `cap.intelligent-investor-4e.graham-valuation-formula` | `graham-valuation-formula` | 格雷厄姆估值：简化公式＋两步评估＋债券保障倍数 | 高 | router → 路由入口 |
| `cap.intelligent-investor-4e.enterprising-bargain-hunting` | `enterprising-bargain-hunting` | 积极型三策略（低市盈率大公司 / 廉价 net-net / 特殊情况） | 高 | router → 路由入口 |
| `cap.intelligent-investor-4e.pairwise-company-comparison` | `pairwise-company-comparison` | 成对公司比较分析法 | 中 | router → 路由入口 |
| `cap.intelligent-investor-4e.bubble-new-issue-immunity` | `bubble-new-issue-immunity` | 牛市泡沫症状与新股免疫 | 高 | router → 路由入口 |
| `cap.intelligent-investor-4e.fund-selection` | `fund-selection` | 基金挑选与卖出信号 | 高 | router → 路由入口 |
| `cap.intelligent-investor-4e.convertible-warrant-skepticism` | `convertible-warrant-skepticism` | 可转债与权证怀疑框架 | 中 | router → 路由入口 |
| `cap.intelligent-investor-4e.dividend-shareholder-policy` | `dividend-shareholder-policy` | 股息政策与股东行动 | 中 | router → 路由入口 |
| `cap.intelligent-investor-4e.advisor-diligence` | `advisor-diligence` | 投资顾问尽调 | 低 | router → 路由入口 |

> 重要度口径：`critical` → 关键，`high` → 高，`medium` → 中，`low` → 低。去向口径：`promoted` 指 pack 模式下编译为可被直接触发的独立 skill；`router` 指只存在于路由入口的 `references/` 里，由入口按意图带出。
>
> 合计 16 张卡：7 张 promoted ＋ 9 张 router，与 `pack/capability-destinations.json` 的 `capability_count: 16`、`entrypoint_count: 8` 一致。

## 依赖关系（also_read）

下表是 `verified.yaml` 里各卡 `also_read` 字段的原始关系：读完左边这张，如果问题跨域，再补读右边这些。箭头表示"读完后接着读"，不是强制调用链。

| 能力卡 | 读完后接着读 |
|---|---|
| `investor-type-selfcheck-skill` | `stock-bond-allocation-skill`、`defensive-stock-screen-skill`、`enterprising-bargain-hunting` |
| `stock-bond-allocation-skill` | `market-valuation-check-skill`、`dca-index-portfolio`、`investor-type-selfcheck-skill` |
| `market-valuation-check-skill` | `stock-bond-allocation-skill`、`mr-market-discipline-skill` |
| `mr-market-discipline-skill` | `safety-margin-engine-skill`、`market-valuation-check-skill` |
| `defensive-stock-screen-skill` | `eps-quality-check-skill`、`graham-valuation-formula`、`safety-margin-engine-skill` |
| `safety-margin-engine-skill` | `graham-valuation-formula`、`eps-quality-check-skill`、`mr-market-discipline-skill` |
| `eps-quality-check-skill` | `defensive-stock-screen-skill`、`safety-margin-engine-skill`、`pairwise-company-comparison` |
| `dca-index-portfolio` | `fund-selection`、`stock-bond-allocation-skill` |
| `graham-valuation-formula` | `safety-margin-engine-skill`、`market-valuation-check-skill`、`defensive-stock-screen-skill` |
| `enterprising-bargain-hunting` | `investor-type-selfcheck-skill`、`safety-margin-engine-skill`、`pairwise-company-comparison` |
| `pairwise-company-comparison` | `eps-quality-check-skill`、`enterprising-bargain-hunting`、`defensive-stock-screen-skill` |
| `bubble-new-issue-immunity` | `mr-market-discipline-skill`、`market-valuation-check-skill` |
| `fund-selection` | `dca-index-portfolio`、`investor-type-selfcheck-skill` |
| `convertible-warrant-skepticism` | `eps-quality-check-skill`、`safety-margin-engine-skill` |
| `dividend-shareholder-policy` | `eps-quality-check-skill`、`pairwise-company-comparison` |
| `advisor-diligence` | `investor-type-selfcheck-skill`、`fund-selection` |

几条成对关系值得单独记住：

- **先定类型，再谈任何比例**：`investor-type-selfcheck-skill` 是全书分流前提，`stock-bond-allocation-skill` 的仓位结论必须建立在它给出的防御 / 积极通道之上；反过来，类型卡本身不产出任何仓位数字。
- **配置 ↔ 大盘水位**：`stock-bond-allocation-skill` 管"目标比例与再平衡触发"，`market-valuation-check-skill` 只给比例"倾向"，不给可执行指令；两者的输出不能互相替代。
- **波动纪律不产出估值**：`mr-market-discipline-skill` 的涨/跌三问以"你自己算得出来的价值"为输入，估不出价值时它把你送回指数化路线，而不是让你拿"不理会报价"当持有理由。
- **筛选 → 排雷 → 算边际**：`defensive-stock-screen-skill`（准入漏斗）、`eps-quality-check-skill`（分子可信度）、`safety-margin-engine-skill`（买价缓冲）是同一条流水线的三段，顺序反了会把伪利润算进安全边际。
- **估值公式是供应商**：`graham-valuation-formula` 产出评估价值，交给 `safety-margin-engine-skill` 算折扣率；它自己不做"买不买"的结论。
- **积极型三策略必须先过资格预检**：`enterprising-bargain-hunting` 的前置条件是 `investor-type-selfcheck-skill` 判定为积极型，否则只输出防御型路线。

## 加载顺序

1. **先读入口 `SKILL.md`**：single 模式读 `single/intelligent-investor-skill/SKILL.md`，pack 模式读 `pack/intelligent-investor-skill-router/SKILL.md`。入口里有触发/不触发边界、7 条核心原则常驻速览，以及完整路由表。
2. **按路由表加载 1 张卡**：从入口的路由表按用户意图命中唯一一张能力卡，读它的 R / I / A1 / A2 / E / B 六段。
3. **跨域时最多再补 1 张**：只有问题明确跨域（例如"先定类型、再配比例、再筛个股"）才按 `also_read` 补读第二张，合计不超过 2 张。
4. **概览类问题不加载卡**：书名、作者、章节、整书概览走 `references/overview.md`；术语走 `glossary.md`；只要决策规则速查走 `cheatsheet.md`；路由表命不中的意图先查 `references/capability-index.md`。
5. **都不命中就明说超范围**：不要用现有卡硬套；用户要求预测涨跌或点位时，按入口的判停规则转入市场先生 / 安全边际纪律框架。

> 本仓库根目录的 `bundle/` 是同一套 16 张卡的源材料（`verified.yaml` + `cards/` + `book/`），供审计与二次编译使用，不参与运行时加载。

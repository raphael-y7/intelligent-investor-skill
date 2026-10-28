---
name: intelligent-investor-skill
description: |
  《聪明的投资者（第4版注疏点评版）》方法论入口：先自测投资者类型（防御/积极/投机隔离），再沿配置→选股→估值→安全边际→波动纪律的路线执行格雷厄姆体系；含兹威格点评的现代行为纪律。用于股票投资分析辅助，输出决策规则而非预测。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: single
  cangjie.bundle-id: bundle.intelligent-investor-4e
  cangjie.capability-count: 16
  cangjie.entrypoint-count: 1
---
# 聪明的投资者（第4版，注疏点评版） — 全书能力入口

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 不预测市场点位、不荐股、不承诺收益
- 不含美国税制（附录2-3）、认股权证文化等制度性内容
- 书中具体数值（22.5/15倍/1.5倍等）为1972/2003年美国参数，仅保留结构，跨市场使用须按当期利率重标定

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 投资操作以深入分析为基础，确保本金安全并获得适当回报；不满足即是投机
2. 投资者只有防御型与积极型两类、无中间态；类型由知识、精力与性格决定
3. 未来不可预测：凡以预测为基础的方法（择时、追趋势、程式方案）终将自我衰减
4. 价格波动只有一个意义：大跌后是买入机会、大涨后是卖出机会；报价是可拒绝的服务
5. 一切稳健投资归结为安全边际：盈利能力显著高于债券利率，或市价显著低于评估价值
6. 用可计量的统计标准与会计警惕落实保护；分母一律多年平均利润
7. 股债25%~75%区间对半开+再平衡+定投等机械纪律是对抗人性的工具

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 判断自己适合防御还是积极投资；划定投机额度；决定投入多少时间研究股票 | references/capabilities/investor-type-selfcheck-skill.md | references/capabilities/stock-bond-allocation-skill.md、references/capabilities/defensive-stock-screen-skill.md、references/capabilities/enterprising-bargain-hunting.md |
| 决定股债比例；建立再平衡规则；全仓股票前自查；抗通胀资产安排 | references/capabilities/stock-bond-allocation-skill.md | references/capabilities/market-valuation-check-skill.md、references/capabilities/dca-index-portfolio.md、references/capabilities/investor-type-selfcheck-skill.md |
| 判断大盘整体贵不贵；现在能不能入场；估算股市长期预期回报 | references/capabilities/market-valuation-check-skill.md | references/capabilities/stock-bond-allocation-skill.md、references/capabilities/mr-market-discipline-skill.md |
| 面对暴跌怎么办；涨了想追怎么办；克服追涨杀跌；拿不住股票 | references/capabilities/mr-market-discipline-skill.md | references/capabilities/safety-margin-engine-skill.md、references/capabilities/market-valuation-check-skill.md |
| 按防御标准筛选股票；检查某股是否符合格雷厄姆标准；建立稳健组合 | references/capabilities/defensive-stock-screen-skill.md | references/capabilities/eps-quality-check-skill.md、references/capabilities/graham-valuation-formula.md、references/capabilities/safety-margin-engine-skill.md |
| 判断买价有没有保护；测算安全边际；买入前风险自检；亏了大半怎么办 | references/capabilities/safety-margin-engine-skill.md | references/capabilities/graham-valuation-formula.md、references/capabilities/eps-quality-check-skill.md、references/capabilities/mr-market-discipline-skill.md |
| 识别利润注水；排查财务红旗；还原真实每股收益；从后往前读财报 | references/capabilities/eps-quality-check-skill.md | references/capabilities/defensive-stock-screen-skill.md、references/capabilities/safety-margin-engine-skill.md、references/capabilities/pairwise-company-comparison.md |
| 建立定投计划；选择指数基金；不想花时间研究股票怎么投 | references/capabilities/dca-index-portfolio.md | references/capabilities/fund-selection.md、references/capabilities/stock-bond-allocation-skill.md |
| 用格雷厄姆公式估值；评估债券安全；计算利息保障倍数；两步评估法 | references/capabilities/graham-valuation-formula.md | references/capabilities/safety-margin-engine-skill.md、references/capabilities/market-valuation-check-skill.md、references/capabilities/defensive-stock-screen-skill.md |
| 做积极型投资怎么选股；找廉价证券；net-net筛选；低市盈率策略 | references/capabilities/enterprising-bargain-hunting.md | references/capabilities/investor-type-selfcheck-skill.md、references/capabilities/safety-margin-engine-skill.md、references/capabilities/pairwise-company-comparison.md |
| 两家同业公司怎么选；对比分析两家公司；质量与价格权衡 | references/capabilities/pairwise-company-comparison.md | references/capabilities/eps-quality-check-skill.md、references/capabilities/enterprising-bargain-hunting.md、references/capabilities/defensive-stock-screen-skill.md |
| 判断是不是泡沫顶部；打新股值不值；热门股能不能追；有效方法失灵了怎么办 | references/capabilities/bubble-new-issue-immunity.md | references/capabilities/mr-market-discipline-skill.md、references/capabilities/market-valuation-check-skill.md |
| 怎么选基金；基金费率高不高；什么时候卖基金；指数还是主动 | references/capabilities/fund-selection.md | references/capabilities/dca-index-portfolio.md、references/capabilities/investor-type-selfcheck-skill.md |
| 可转债能不能买；转换溢价高不高；权证稀释怎么算；双低策略怎么看 | references/capabilities/convertible-warrant-skepticism.md | references/capabilities/eps-quality-check-skill.md、references/capabilities/safety-margin-engine-skill.md |
| 公司不分红好不好；股息政策怎么评价；高送转怎么看；股东大会投票 | references/capabilities/dividend-shareholder-policy.md | references/capabilities/eps-quality-check-skill.md、references/capabilities/pairwise-company-comparison.md |
| 要不要请投资顾问；怎么辨别理财顾问骗局；荐股群可信吗 | references/capabilities/advisor-diligence.md | references/capabilities/investor-type-selfcheck-skill.md、references/capabilities/fund-selection.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 当用户要求预测涨跌或点位时，停止并转入市场先生/安全边际纪律框架
- 当缺少多年利润、利率等必要输入时，先索取数据，不得以单年数据代替
- 当用户身份不满足积极型预检（时间/精力/性格）时，只输出防御型路线

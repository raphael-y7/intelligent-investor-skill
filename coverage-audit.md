# coverage-audit.md — 原书关键任务 → 实际交付去向

基准：BOOK_OVERVIEW.md 原书关键任务清单（task-01~20，不从旧 verified 反推）。

| task | 读者任务 | 交付去向 | 状态 |
|---|---|---|---|
| task-01 | 判断防御型/积极型 | investor-type-selfcheck-skill（promoted） | ✅ |
| task-02 | 股债比例与再平衡 | stock-bond-allocation-skill（promoted） | ✅ |
| task-03 | 四原则/七标准筛选防御组合 | defensive-stock-screen-skill（promoted）＋pairwise-comparison（router） | ✅ A股数据源在卡内输入契约中要求用户提供 |
| task-04 | 定投计划 | dca-index-portfolio（router） | ✅ |
| task-05 | 受控投机额度隔离 | investor-type-selfcheck-skill（promoted，p02并入） | ✅ |
| task-06 | 市场整体估值判断 | market-valuation-check-skill（promoted） | ✅ 需当期数据（卡内输入契约） |
| task-07 | 市场先生波动纪律 | mr-market-discipline-skill（promoted） | ✅ |
| task-08 | 抗通胀安排 | stock-bond-allocation-skill（promoted，p09/ce24并入）；TIPS等美国工具→needs-review | ✅（结构）/⚠️（工具映射） |
| task-09 | 低市盈率大公司组合 | enterprising-bargain-hunting（router） | ✅ |
| task-10 | net-net 廉价股 | enterprising-bargain-hunting（router，含次优替代边界） | ✅ |
| task-11 | 安全边际定价 | safety-margin-engine-skill（promoted）＋graham-valuation-formula（router） | ✅ |
| task-12 | 每股收益会计陷阱 | eps-quality-check-skill（promoted） | ✅ 需财报数据 |
| task-13 | 债券/优先股安全性 | graham-valuation-formula（router，表11-1保障倍数）＋convertible-skepticism | ✅ |
| task-14 | 危险公司红旗 | eps-quality-check-skill（promoted，第17章案例并入红旗清单） | ✅ |
| task-15 | 新股/热门股免疫 | bubble-new-issue-immunity（router） | ✅ |
| task-16 | 基金挑选 | fund-selection（router）＋dca-index-portfolio | ✅ 费率数值需当期重标定 |
| task-17 | 顾问尽调 | advisor-diligence（router） | ✅ |
| task-18 | 股息政策与股东立场 | dividend-shareholder-policy（router） | ✅ A股语境以公告/年报替代10-K（卡内注明） |
| task-19 | 亏损承受力与行为自检 | safety-margin-engine-skill（promoted，镜子测试并入）＋mr-market（所有者合约） | ✅ |
| task-20 | 可转债/权证话术识别 | convertible-warrant-skepticism（router） | ✅ |

**结论：20/20 任务有可追溯去向，无未解释遗漏。**

实际输出评测（阶段4压力测试）见 `.cangjie/runs/2026-10-25-distill/report.md`：7张晋级卡全部完成代表性任务实跑并核对输出，2张路由卡抽测。

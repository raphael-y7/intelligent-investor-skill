# verified.md — 阶段1.5/1.6 分流结果

> 候选池：frameworks 25 ＋ principles 71 ＋ cases 38 ＋ counter_examples 30 ＋ glossary 20 ＝ 184 条。
> 三重验证（V1来源充分性/V2可执行性/V3任务增益）＋晋级门（五判据）后合并为 **16 个能力单元**（7 promoted ＋ 9 router），映射原书关键任务20条全覆盖。

## 一、通过并编译为 active 能力（16）

| # | capability | 晋级 | 合并的候选 | 任务映射 |
|---|---|---|---|---|
| 1 | investor-type-selfcheck-skill | promoted | f01,f05 + p01,p02,p07,p25 + ce01,ce28 + g01-g05 | task-01, task-05 |
| 2 | stock-bond-allocation-skill | promoted | f02 + p03,p04,p09,p14,p15,p16 + ce23,ce24 | task-02, task-08 |
| 3 | market-valuation-check-skill | promoted | p11,p12,p49 + ce22（表3-3素材） | task-06 |
| 4 | mr-market-discipline-skill | promoted | f04,f06,f23 + p06,p29,p31,p33 + ce02,ce03,ce04,ce25 + c29,c30 | task-07 |
| 5 | defensive-stock-screen-skill | promoted | f07,f08,f19 + p17,p18,p46,p47,p48 + c20,c27 + ce06,ce18 | task-03 |
| 6 | safety-margin-engine-skill | promoted | f24,f25 + p61-p68,p70 + c35 + ce26,ce29,ce30 | task-11, task-19 |
| 7 | eps-quality-check-skill | promoted | f16,f17 + p42,p43,p44,p45 + ce10-ce14 + c05,c06,c34 | task-12, task-14 |
| 8 | dca-index-portfolio | router | f03 + p08,p36 + c32 + ce25（部分） | task-04 |
| 9 | graham-valuation-formula | router | f13,f14,f15 + p38,p39,p40,p41,p42 | task-11, task-13 |
| 10 | enterprising-bargain-hunting | router | f09-f12 + p21-p24,p51-p54 + c22,c23,c24,c26 + ce15,ce27 | task-09, task-10 |
| 11 | pairwise-company-comparison | router | f18 + c09-c21 | 支撑 task-03/09 |
| 12 | bubble-new-issue-immunity | router | f22 + p05,p28 + c30,c33,c38 + ce07,ce08 | task-15 |
| 13 | fund-selection | router | f20 + p34-p37 + c28 + ce16,ce17 | task-16 |
| 14 | convertible-warrant-skepticism | router | p55,p56,p57 + ce20,ce21 + c03（NVF） | task-20 |
| 15 | dividend-shareholder-policy | router | p58,p59,p60 + ce19 | task-18 |
| 16 | advisor-diligence | router | f21 + ce22（部分）+ 第10章点评清单 | task-17 |

## 二、V1-V3 验证说明

- **V1 来源充分性**：全部单元的 R 段引文经合并转写稿 grep 逐字抽验（抽验27段＋关键数字17处，除片段截断假阴性外全部命中；估值公式原文口径确认为"价值=当期（正常）利润×（8.5+两倍的预期年增长率）"）。C3组发现并修正1条候选引文失真（"可转换证券显然会使购买者一无所获"原文不存在，已换为第16章真实原文）。
- **V2 可执行性**：16单元均给出输入/输出契约与步骤；两处原书未完成机制如实标注（两步评估权重→标为约定；80%概率估计法→needs-review）。
- **V3 任务增益**：以 BOOK_OVERVIEW 20条关键任务为基准做覆盖审计（见 coverage-audit.md），无未解释遗漏。

## 三、晋级门判定要点

- promoted 七卡：均为高频独立意图（类型/仓位/大盘估值/波动/选股/安全边际/排雷），契约与评测独立成立（gate 5项全真）。
- bubble-new-issue-immunity 五项判据虽全真，但用户工作区已有跨书泡沫识别能力（bubble-mania-skill），为避免入口拥挤，本版主动降为 router（deviation：产品化验证维度）。
- 检验性事实：1970年道指30只仅5只全过七项标准（c27）——说明筛选器"结构可用、通过率极低"，已写入 defensive-stock-screen-skill 的 B 段防误用。

## 四、淘汰/移交

- 无整条淘汰（rejected/ 为空，理由见 rejected/README.md）——所有候选或并入16单元、或移交 references/needs-review。
- 合并去重记录：f06并入 mr-market＋bubble 两卡；ce05（航空业）并入 enterprising 卡B段；ce18（本土偏见）并入 defensive-screen B段；ce27（IBM/GEICO自认错误）并入 enterprising＋safety-margin B段；c25/c36/p69（GEICO后记）→ references（激励性材料不编译为可执行方法）。

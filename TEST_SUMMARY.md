# Stage 4 压力测试摘要

> 本书：《聪明的投资者（第4版注疏点评版）》（本杰明·格雷厄姆 著；贾森·兹威格、沃伦·巴菲特 注疏点评）
> 仓库：`intelligent-investor-skill` ｜ bundle：`bundle.intelligent-investor-4e` ｜ 基线：`v1-first-distill`
> 本摘要的数据来源：仓库内实际文件 + 归档 `审计过程/` 下的阶段 4 记录。凡未随归档提供的产物，下文均明确标注。

## 测试范围

- **能力单元**：16 张（7 张 promoted ＋ 9 张 router），编译为 **9 个可发现 skill 目录**——`single/` 下 1 个单入口 `intelligent-investor-skill`，`pack/` 下 8 个（1 个来源路由入口 `intelligent-investor-skill-router` ＋ 7 个独立 skill）。
- **test-prompts 文件**：**9 份**，与 9 个 skill 目录一一对应（`single/intelligent-investor-skill/` 1 份，`pack/*/` 8 份），合计 **64 条用例**。
- **覆盖类型**（按 `type` 字段统计）：
  - `should_trigger`：36 条（每个 skill 4 条正面触发）
  - `should_not_trigger`：18 条（每个 skill 2 条，其中至少 1 条为同书跨技能诱饵）
  - `edge_case`：10 条（多数 skill 1 条，单入口 2 条）
  - `output_case`：**本包没有此类型用例**。输出侧核对以阶段 4 报告中的「代表任务实跑」形式记录（见下），不是 JSON 用例。
- **用例来源**：归档 `审计过程/工具脚本/tools_test_prompts.py`（阶段 4 用例生成器，版本字段 `1.1.0`）。该脚本内含 9 套件全部用例定义，本次按 skill 目录原样导出为 `test-prompts.json`，未改写任何 prompt 与预期行为。归档内没有以 `test-prompts*.json` 文件形式存在的用例文件。

## 结构检查

以下为本次对仓库实际文件逐项跑出的结果（核验脚本临时生成，已清理）：

| 检查项 | 结果 |
|---|---|
| JSON 可解析性 | 仓库内 12 个 `.json` 全部可解析，失败 0（9 份 test-prompts ＋ `pack/BUILD_MANIFEST.json` ＋ `pack/capability-destinations.json` ＋ `single/intelligent-investor-skill/BUILD_MANIFEST.json`） |
| test-prompts 字段完整性 | 9 份均含 `skill` / `version` / `test_cases`；每条用例 `id` / `type` / `prompt` / `expected_behavior` / `notes` 齐全；`skill` 字段与所在目录名一致 |
| SKILL.md frontmatter | 9 份 SKILL.md（single 1 ＋ pack 8）全部带 YAML frontmatter，`name` / `description` 齐备，并含 `cangjie.*` 元数据（variant / bundle-id / capability-count） |
| 能力卡六段完整性 | `bundle/cards/` 16 张卡 R / I / A1 / A2 / E / B 六段齐全，缺段 0 |
| 三处卡片副本一致性 | `single/intelligent-investor-skill/references/capabilities/` 与 `pack/intelligent-investor-skill-router/references/capabilities/` 各 16 份，与 `bundle/cards/` 逐字比对 32/32 一致（忽略空白差异） |
| `bundle/verified.yaml` | 16 个 `capability_id`、16 个 `slug`，每卡含 `promotion.gate` 五项判据与 `also_read` 字段；条目数与 `INDEX.md` 能力总表 16 行、`pack/capability-destinations.json` 的 `capability_count: 16` 一致 |
| YAML 解析器校验 | **未做**：当前环境没有 pyyaml，`verified.yaml` 只做了字段计数与结构抽检，未做语法级解析 |

## 结果

- skills：**16 张能力卡 → 9 个可发现 skill 目录**（single 1 ＋ pack 8）
- test_json：**9 份，64 条用例**
- 通过情况：

  **归档内没有 `test-results*.md`**，逐题结果明细未随归档提供。归档中的阶段 4 报告 `审计过程/拆书审计/runs/2026-10-25-distill/report.md` 记录了如下结果（原文摘录，本次未重跑）：

  - 晋级卡触发＋代表任务实跑：**7/7 通过**（T1–T7，其中 T3 用书内 1971 年数据回放、T7 用书内美国铝业 1970 年数据回放，均与书原文一致）
  - 路由卡可达性与结构核验：9 张可达性通过；**代表任务只抽测了 2 张**（bubble、enterprising），其余 7 张未做完整实跑（缺口已登记 `needs-review.md` E-11）
  - 触发盲测（64 条用例）：首轮 **59/64**，诱饵 0 误触发；5 项失败中 3 项改技能描述、2 项改用例并记录理由；复测 5/5 通过；报告记为最终 **64/64**

  > 上述 64/64 是归档报告的文字记录，不是本次执行的产物；仓库内也没有逐题日志。接入后如需可复核的成绩，应按本仓库的 9 份 `test-prompts.json` 重跑一轮并落 `test-results.md`。

## 可接入 darwin-skill 的后续动作

1. **用例直接作为回归样本**：9 份 `test-prompts.json`（64 条）已随各自 skill 目录发布，可作为 darwin-skill 的触发回归基线；改动任何 SKILL.md 的 `description` 后，先跑这 64 条，重点看 `should_not_trigger` 的 18 条诱饵是否被误触发。
2. **补齐输出侧用例**：本包缺 `output_case` 类型。建议把阶段 4 报告里的 7 个代表任务（类型判定、再平衡、大盘水位、七项筛选、安全边际、暴跌三问、EPS 辨伪）转成带期望输出的 `output_case`，其中 T3、T7 可直接用书内 1971 年数据做可复算的断言。
3. **补齐 7 张路由卡实跑**：`dca-index-portfolio`、`graham-valuation-formula`、`enterprising-bargain-hunting`、`pairwise-company-comparison`、`fund-selection`、`convertible-warrant-skepticism`、`dividend-shareholder-policy`、`advisor-diligence` 目前只有静态触发词检查（`needs-review.md` E-11），需补代表任务实跑。
4. **登记 known-issue 用例**：源电子书第 9 章点评费用上限表有排版缺损、另有 5 处原书排印疑误（见 `needs-review.md` D 节）。涉及这些数字的用例应标为 known-issue，避免把源缺陷算成模型错误。
5. **v2 重标定后的用例**：书中数值门槛（22.5 / 15 倍 / 1.5 倍 / 2:1 / 25 倍 / 20 倍等）是 1972 年美国参数。若后续按当期利率重标定，需要同步新增一组「重标定后仍守住结构」的用例，否则旧用例会把正确的重标定判成违规。

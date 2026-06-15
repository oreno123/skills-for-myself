---
name: data-document-reviewer
description: "Use when reviewing any document that cites external statistics, regulations, or technical claims with URLs — research reports, market analyses, industry briefings, ESG documents, policy summaries, 调研说明. Triggers: 审查数据 / 核对引用 / 核对来源 / fact-check / 检查数据报告 / 数据 QA / verify citations / before publishing any data-driven report. Symptoms: document has many URL citations but you suspect some numbers may be misread from sources, technical terms invented, calculations incomplete, or assumptions unstated."
---

# Data Document Reviewer

## Overview

**Core principle:** Zero-context, evidence-first audit. The reviewer must verify every cited number, technical term, regulation ID, and forecast against the **actual source URL** — not against what the writer *said* the source said.

写作这类含外部引用的数据报告时，最容易出 5+ 类系统性错误。本 skill 把每类错误的判定规则公开化，让审查可以机械化执行。

## When to Use

**适用：**
- 研究报告 / 行业分析 / 市场调研 / ESG 报告 / 政策解读
- 调研说明 / 课题报告 / 投资备忘录
- 任何"每条数据后标 URL"的中文文档
- 数据来自网络搜索而非实验测量（区别于论文审查）

**不适用：**
- 论文审查（实验数据 vs raw results）→ 用 `paper-claim-audit`
- 代码 / 测试验证 → 用 `verification-before-completion`
- 设计稿审查 → 用 `design-critique` 系列

## The Iron Law

```
NO VERDICT WITHOUT FRESH SOURCE CHECK
```

每个数据点都必须打开 URL 验证一次。**绝不能**因为"作者说引自 X"就直接采信。

**违反字面规则就是违反精神。**

## Failure Modes（5 严重 + 3 警告）

### 🔴 FAIL 级（必须修复才能 PASS）

#### F1. Misread Source（误读来源）

**症状**：文档写"A 是 X"，但来源原文实际写的是"A 是 Y"或"A 和 X 是两件事"。

**真实案例**：
- 文档："2024 年数字物流业务营业收入 28.57 亿元"
- 来源实际："建材营业收入 28.57 亿元；数字物流业务加快外部业务拓展"
- **28.57 亿是基础建材营收，不是数字物流营收**

**审查方法**：对每个数据点，回到 URL 打开原文，逐字比对。重点检查：
- 数据所属主体是否一致（"集团总营收" vs "子公司营收" vs "业务线营收"）
- 数据口径是否一致（"销量" vs "产量" vs "产能"）
- 时间口径是否一致（"2024 年" vs "2024 上半年" vs "截至 2024 年底"）

#### F2. Fabricated Specifics（编造具体内容）

**症状**：来源只提了一个概念名词（如"三个坚持"、"五点要求"、"七项举措"），文档列出了具体 N 条内容，但**这些具体内容在公开来源中查不到**。

**真实案例**：
- 来源："平台紧紧围绕'三个坚持'推进商业模式创新……"（未展开）
- 文档列出："1. 坚持服务制造业大宗物流 2. 坚持平台模式创新 3. 坚持数字化能力赋能"
- **这 3 条是 AI 编的**，原文没有展开

**审查方法**：
- 任何"N 点"、"N 项"、"N 类"列表，逐条核对来源
- 找不到展开内容时，标注"具体口径公开报道未展开"，**绝不补编**
- 行业经验值应标"行业经验值"，不冒充来源数据

#### F3. Wrong Technical Term（专业术语错误）

**症状**：化学名、法规文号、单位、专业比例写错。

**真实案例**：
- ❌ "六氟化二碳" → ✅ "六氟乙烷 C₂F₆"（PFCs 类）
- ❌ "国务院令第 775 号规定罚则 5-10 万元/吨" → ✅ "未清缴配额量 5-10 倍罚款"
- ❌ "水泥行业碳排放 90% 来自工艺排放" → ✅ "约 60-65% 来自工艺排放"

**审查方法**：
- 化学名：交叉验证 CAS 号或 IUPAC 名称
- 法规文号：必须去原文核对**具体条款序号 + 罚则原文**
- 单位：检查 %、万、亿、吨 vs 吨CO₂、kWh vs MWh
- 行业基准值：核对最新版国标（GB/T）或行业协会公告

#### F4. Incomplete Calculation（算法漏算）

**症状**：分项相加 ≠ 总数；某项被漏算或重复计算。

**真实案例**：
- ❌ 水泥综合电耗 = 熟料电耗（380 万吨）+ 水泥粉磨电耗（**仅外购 120 万吨**）= 2.48 亿 kWh
- ✅ 水泥综合电耗 = 熟料电耗（380 万吨）+ 水泥粉磨电耗（**全部 500 万吨**）= 3.58 亿 kWh
- 漏算了自有 380 万吨熟料粉磨成水泥的电耗

**审查方法**：
- 任何"分项 = 总数"的算式，**手工重算一遍**
- 检查"另一方法交叉验证"时，两种方法口径是否真的可比
- 检查百分比加总（24% + 48% + 18% + 10% 应 = 100%）

#### F5. Citation Forged or Inaccessible（引用伪造或失效）

**症状**：URL 指向不存在页面、与内容无关页面、或根本是 AI 拼凑的假 URL。

**审查方法**：
- 每个 URL 必须 fetch 一次，确认 200 状态码且内容相关
- 警惕"看起来真"但实际不存在的 URL（如伪造的政府文件编号）
- PDF 链接必须确认能下载且内容相符

---

### 🟡 WARN 级（建议修复，不强制 FAIL）

#### W1. Unstated Assumption（推算未标假设）

**症状**：推算/反推数据未标注关键假设。

**真实案例**：
- 文档："单吨公里减排 0.098 kgCO₂"（推算）
- 缺失：假设平均运距 100 km、假设载重 30t、反推 vs 正向算法差异
- 读者无法判断这个数字是否适用于自己的场景

**审查方法**：每个"推算"必须包含：
- 推算公式（变量、单位）
- 关键假设值（取自哪里）
- 算法方向（正向算法 vs 反推）+ 与另一种算法的差异

#### W2. Aggregation Mismatch（加总口径不一致）

**症状**：把不同口径的数据简单相加。

**真实案例**：
- "光伏直接减排 2.16 万吨（单园区）+ 物流协同减排 1.91 万吨（集团全口径）= 4.07 万吨"
- 两个数据**口径不同**（单园区 vs 集团全口径），不能直接加总

**审查方法**：任何"N 项数据加总"，每项的口径必须一致；不一致时必须明确说明"口径不同，仅作数量级参考"。

#### W3. Forecast Overclaim（预测过度自信）

**症状**：长期预测给单值而非区间，或引用单一来源作为共识。

**真实案例**：
- ❌ "2030 年碳价将达到 100-150 元/吨"（标"业界普遍预测"但实际只引了一个来源）
- ✅ "2030 年碳价预测区间 80-200 元/吨（不同机构差异大），具体数字会随政策节奏变化"

**审查方法**：
- 长期预测必须给区间而非单值
- "业界普遍预测"必须列 ≥ 2 个独立来源
- 标注预测的时间敏感性和不确定性

---

## Workflow

### Step 1: Inventory Claims

把文档里**所有**可验证的 claim 抽出来，按类型分类：

| 类型 | 识别关键词 | 路由到 |
|------|----------|--------|
| 数据点 | 数字 + 单位 + 来源标注 | F1, F3 |
| 概念列表 | "N 个/N 项/N 类" + 列表 | F2 |
| 法规/标准 | "国务院令"、"GB"、"文号" | F3 |
| 算式 | "X = A + B"、"按...计算" | F4 |
| 引用 URL | `[xxx](http://...)` | F5 |
| 推算值 | "推算/反推/测算" | W1 |
| 加总 | "合计/共/总" | W2 |
| 预测 | "预计/有望/2030 年/未来" | W3 |

### Step 2: Source Verification (零上下文)

**关键**：审查者**绝不能**读文档作者的草稿、解释、中间总结。每个 claim 都直接打开 URL 比对。

对每个 claim，记录：

```
claim_id: 001
location: §1.2 表第 3 行
document_text: "2024 年数字物流业务营业收入 28.57 亿元"
source_url: https://pdf.dfcfw.com/...
source_actual: "建材营业收入 28.57 亿元"
status: F1_misread_source
fix: 改为"基础建材业务营业收入 28.57 亿元"，并加注"数字物流单独营收未披露"
```

### Step 3: Verdict Decision

| 触发条件 | Verdict | 含义 |
|---------|---------|------|
| 0 个 FAIL + 0 个 WARN | **PASS** | 可发布 |
| 0 个 FAIL + ≥1 个 WARN | **WARN** | 可发布，但建议修复 |
| ≥1 个 FAIL | **FAIL** | 必须修复后重审 |

### Step 4: Output Report

输出结构化报告（人类可读 md + 可机读 json）：

```markdown
# Data Document Review Report

**Date**: YYYY-MM-DD
**Document**: [文件名]
**Reviewer context**: zero-context (未读作者草稿)

## Verdict: FAIL / WARN / PASS

## Issues Found: [N total]
- F1 misread_source: [count]
- F2 fabricated_specifics: [count]
- F3 wrong_term: [count]
- F4 incomplete_calc: [count]
- F5 forged_citation: [count]
- W1 unstated_assumption: [count]
- W2 aggregation_mismatch: [count]
- W3 forecast_overclaim: [count]

## Issues Detail

### [FAIL] Issue #1: [一句话描述]
- **Location**: 文件 §X.Y 第 N 行
- **Document says**: "..."
- **Source actually says**: "..."
- **Source URL**: ...
- **Fix**: 具体修正方法

## All Claims Verified
| # | Location | Document Value | Source Value | Status |
|---|----------|---------------|--------------|--------|
| 1 | §1.2 表 | 28.57 亿（数字物流） | 28.57 亿（基础建材） | F1 |
```

---

## Rationalization Prevention（堵漏）

| Excuse | Reality |
|--------|---------|
| "数字大体对，差几个百分点不重要" | F1 / F4 必须精确到原文表述，"大体对"= 不对 |
| "三个坚持/N 点内容业界都这么讲" | 没在原文找到就是 F2，不能"业界惯例归纳" |
| "化学名/文号我记不清了大概对" | F3 一票否决，专业术语必须精确 |
| "推算数据加上假设会让文档变啰嗦" | W1 不啰嗦，是必要的科学诚实 |
| "URL 我没访问但记得有这个文件" | F5 必须实际 fetch |
| "这只是建议性数据，差不多就行" | 数据报告没有"差不多"，每个数字都背书 |
| **"subagent 报 FAIL 就一定是 FAIL"** | **subagent 也会误读文档（如把'上市公司公告'泛称当成年报）；主审必须亲自复核每个 FAIL 级 issue 的 location + document_text + source_actual 三件套** |
| **"subagent 摘要里说'文档写 X'，那就是 X"** | **主审必须打开原文档核对——subagent 摘要可能是它自己的解读，不是文档原文** |

## Red Flags - STOP

写审查报告时出现以下念头，立刻停下重审：
- "看着像对的"
- "我记得原文是这么说的"
- "数字量级合理"
- "作者应该核对过"
- "这个 URL 看起来真"
- **"subagent 都报 FAIL 了，直接信"**
- **"subagent 摘要这么写，文档一定这么写"**

**所有这些 = 没有验证就下结论 = 违反 Iron Law**

## Subagent 复核规则（重要 — GREEN 验证踩坑后加入）

如果用 subagent 做 source verification（推荐——可以保护主上下文不被 URL fetch 结果塞爆），**主审必须**：

1. **每个 FAIL 级 issue** 亲自打开文档对应位置（用 Read + line number），核对 subagent 报告的 `document_text` 是否真的逐字存在
2. **每个 FAIL 级 issue** 亲自 fetch 一次 source URL（或读取项目里 cached 的原文），核对 subagent 报告的 `source_actual` 是否真的来自该 URL
3. **subagent 报告的"假阳性"**（即文档实际正确但 subagent 报错）必须在最终报告里**显式标注**——这是 subagent 误判，不是文档问题，不要修复
4. **subagent 报告的"假阴性"**（即 subagent 报 PASS 但主审怀疑有问题）应该触发新一轮手工细查——subagent 可能偷懒没真的 fetch

**GREEN 验证案例（2026-06-15）**：subagent 报告"文档产能数据标错引用源——标为来自 2025 年报但年报没有这数据"，主审复核发现文档实际标的来源是资产评估报告（subagent 把 §1.1 标题里的"上市公司公告"泛称当成了年报）。这是一个**假阳性**，主审复核后避免了一次错误修复。

---

## Difference From Similar Skills

| Skill | Question it answers |
|-------|-------------------|
| `paper-claim-audit` | 论文里的数字 vs raw result files 是否一致？ |
| `verification-before-completion` | 代码完成前是否运行了验证命令？ |
| `quality-assurance-auditor` | 数学建模论文结构是否完整、模型是否偷换？ |
| **`data-document-reviewer`** | **数据报告里的引用是否真的支持文档的说法？** |

## When This Skill Should Not Block

- 数据来自企业内部、未公开（无法核对 URL）→ 标"内部数据，未交叉验证"，不强制 FAIL
- 来源是付费数据库（如 Wind、Bloomberg）→ 标"付费源，需独立账号验证"
- 来源是采访 / 一手调研 → 标"一手来源，需访谈记录核对"

这些情况降级为 WARN，不阻塞。

---

## Origin

本 skill 基于 2026-06-15 一次真实审查经验提炼。那次审查在 3 份"零碳园区"数据说明里发现 **5 个严重错误 + 9 个中低风险问题**：

| 真实踩坑 | 失败模式 |
|---------|---------|
| 把"基础建材营收 28.57 亿"误作"数字物流营收" | F1 |
| 编造"三个坚持"的具体 3 条内容 | F2 |
| "六氟化二碳"应为"六氟乙烷 C₂F₆" | F3 |
| "罚则 5-10 万元/吨"应为"配额量 5-10 倍罚款" | F3 |
| 水泥粉磨电耗漏算 380 万吨自有熟料 | F4 |
| 单吨公里减排 0.098 未标反推假设 | W1 |
| 单园区 + 集团全口径简单加总 | W2 |
| "2030 年碳价 100-150 元"标"业界普遍预测"但只引一个源 | W3 |

后续同类数据报告审查直接调用本 skill，避免每次现想 checklist。

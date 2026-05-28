---
name: build-frontend
description: "Claude Code 前端页面生成器 — 描述需求 + 参考素材，生成单文件 HTML（支持 Vue/React CDN），Actor-Critic 自评迭代，产出可直接打开的成品。触发词：做个网页、生成页面、建个站、landing page、single file HTML、portfolio page、海报页、宣传页、build a page、make a website。"
---

# build-frontend

Claude Code 前端页面生成器。用户描述需求（可附带参考图/URL），Claude 生成单文件 HTML，自动走 Actor-Critic 自评迭代，交付可双击打开的成品。

**支持技术栈**：原生 HTML/CSS/JS、Vue 3 CDN、React CDN、Three.js
**核心特性**：Actor-Critic 自评循环、参考图/URL 动态提取、零 build 步骤

## 主流程

```
Step 1 · 需求挖掘    →  问清 5 个维度
Step 2 · 参考收集    →  从图片/URL/设计稿提取设计 tokens
Step 3 · 选技术栈+维度 →  原生/Vue/React + 6 维度匹配
Step 4 · 生成（Actor） →  写出完整 HTML
Step 5 · Actor-Critic  →  自检 + 独立 sub-agent 评分 + 迭代
Step 6 · 交付        →  写入 output/ 文件
```

---

## Step 1 · 需求挖掘

一次问完 5 个维度（不要逐个追问）。如果用户描述已覆盖，直接总结确认。

| 维度 | 问题 | 示例 |
|------|------|------|
| 用途 | 这个页面做什么用？ | 作品集、产品落地页、活动海报、表白页 |
| 动效 | 要什么程度的动效？ | 纯静态、subtle hover、滚动驱动、全屏动画 |
| 媒体 | 需要嵌入什么？ | 无、BGM、视频背景、图片画廊 |
| 时长 | 单屏海报还是长滚动？ | 一屏、3-5 屏、无限滚 |
| 调性 | 整体感觉？ | 极简、暗黑奢华、温暖文艺、赛博朋克 |

---

## Step 2 · 参考收集

用户可提供参考素材。处理策略见 `references/reference-extraction.md`。

**输入类型**：
- **本地图片** — Read 工具读取，提取配色/字体/布局/组件
- **网页 URL** — WebFetch 抓取，提取 CSS 变量/配色/结构
- **设计稿** — 当作图片处理
- **混合** — 以图片为最高优先级，URL 次之，文字补充

**必须输出参考摘要表**：

```
配色：主色 #xxx / 辅色 #xxx / 背景 #xxx / 文字 #xxx
字体：标题用 xxx / 正文用 xxx / 强调用 xxx
布局：[单栏 | 双栏 | 网格 | 层叠 | 混合]
动效：[无 | subtle | 滚动驱动 | 全屏动画]
组件：导航栏、hero区、特性展示、CTA、footer...
调性关键词：[3-5 个词]
```

**必须询问用户确认**：「我从参考中理解到这些，对吗？需要调整什么？」

---

## Step 3 · 选技术栈 + 维度

### 技术栈

| 技术栈 | 适用场景 | CDN |
|--------|----------|-----|
| 原生 HTML/CSS/JS | 简单页面、海报、静态展示 | 无需引入 |
| Vue 3 CDN | 交互丰富、组件化、状态管理 | `https://unpkg.com/vue@3/dist/vue.global.prod.js` |
| React CDN | 复杂 UI、大量动态组件 | React + ReactDOM + Babel standalone |
| 框架 + Three.js | 3D 场景 + UI 交互 | 框架 CDN + Three.js importmap |

**选择逻辑**：
- 默认原生
- 需要 tab 切换/表单联动/动态列表 → Vue
- 用户说"用 React" → React
- 需要 3D → 框架 + Three.js
- 用户指定 → 直接遵从

Vue/React CDN 骨架模板见 `references/system-prompt-design.md`。

### 维度

自动匹配 6 维度：`form`（排版）、`motion`（动效）、`3D`、`media`（媒体）、`duration`（时长）、`style`（风格）

告知用户选了什么技术栈 + 哪些维度。

---

## Step 4 · 生成（Actor）

**硬约束**：
- 禁止 Unsplash/picsum 占位图
- 禁止 Lorem ipsum 占位文案
- 禁止 `href="#"` 空链接
- 禁止 alert/prompt/confirm
- 禁止未定义的 CSS 变量
- 禁止 npm/webpack/vite build 步骤

**必须**：
- 输出完整 `<!DOCTYPE html>...</html>`
- 所有 CSS 在 `<style>` 内
- 所有 JS 在 `<script>` 内
- 图片用 base64 data URL 内嵌（如有用户提供）
- 字体从 Google Fonts 加载
- CSS 变量全部在 `:root` 定义
- 使用语义 HTML5

**反 AI slop**：
- 禁止字体三件套：Inter + 紫色渐变 + Space Grotesk
- 禁止 Tailwind 默认蓝色 (#3B82F6)
- 配色必须有主导色（不是均匀分布）
- 布局必须打破常规网格（非对称、层叠、或有意的大留白）
- 背景禁止纯色平面（必须分层：渐变/噪点/图案/光晕）

输出到 `output/<页面名>/index.html`

---

## Step 5 · Actor-Critic 自评

### 5a. 自检（Actor 自己做）

扫描生成结果，过一票否决清单（V-01 ~ V-06，见 `references/quality-rubric.md`）：
- broken image → 修复
- 空链接 → 加真实锚点或移除
- 占位文案 → 替换为真实内容
- 未定义 CSS 变量 → 补定义
如有命中，**直接修复**，不进 critic。

### 5b. 独立 Critic（sub-agent）

启动 Agent sub-agent（subagent_type: general-purpose）：

**Critic prompt**：
```
You are the critic — independent of the generator.
Score the HTML against the quality rubric (R-01 → R-20, V-01 → V-06).
Be conservative: assume the generator inflated 0.4 ~ 0.75.
Return ONLY JSON:
{"score": <number>, "gaps": ["ID 具体问题"], "ship": <boolean>, "veto_hit": <string|null>}

HTML to evaluate:
{截取前 10000 字符的 HTML}
```

**评分标准**：见 `references/quality-rubric.md`
**评分范围**：0-5，0.05 步进
**ship 条件**：score ≥ 3.5 且无 veto 命中

### 5c. 迭代决策

```
if ship=false AND score < 3.5 AND iteration < 2:
    把 gaps 列表附加到下一轮生成的 prompt 中
    iteration += 1
    回到 Step 4 重新生成
else:
    进入 Step 6 交付
```

最多 2 轮迭代。每轮告知用户当前分数和 gaps。

---

## Step 6 · 交付

- 确认文件写入 `output/<页面名>/index.html`
- 告知：「双击即可在浏览器打开」
- 可选提示部署：Cloudflare Pages / GitHub Pages / Netlify Drop
- 如有需要，告知如何修改文案或配色

---

## Reference Files

| 文件 | 用途 |
|------|------|
| `references/quality-rubric.md` | 评分量表（R-01→R-20，V-01→V-06） |
| `references/actor-critic.md` | Actor-Critic 循环模式详解 |
| `references/system-prompt-design.md` | Prompt 设计原则 + Vue/React CDN 模板 |
| `references/reference-extraction.md` | 从图片/URL 提取设计 tokens |
| `references/sse-streaming.md` | SSE 流式解析模式（浏览器端工具用） |

需要深入某个模式时，读取对应的 reference 文件。

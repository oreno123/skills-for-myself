# Skills for Myself / 我的 Claude Code Skills 合集

我的 Claude Code skills 备份仓库，同步自 `~/.claude/skills/` 和 `~/.claude/plugins/`。

## 分类目录

### 开发工作流 Development Workflow

代码质量、规划与团队协作相关的 skills。

| Skill | 说明 |
|-------|------|
| `brainstorming` | 动手前的创意探索与需求梳理 |
| `systematic-debugging` | 结构化 bug 排查流程 |
| `test-driven-development` | TDD 纪律：先写测试再实现 |
| `writing-plans` | 多步骤实施计划文档 |
| `executing-plans` | 带审查检查点的计划执行 |
| `dispatching-parallel-agents` | 并行派发独立任务 |
| `subagent-driven-development` | 子 Agent 驱动的计划执行 |
| `using-git-worktrees` | Git worktree 隔离工作区 |
| `verification-before-completion` | 完成前必须跑验证，证据先行 |
| `data-document-reviewer` | 数据报告零上下文审查（5 FAIL + 3 WARN 失败模式，含 subagent 误判复核规则） |
| `requesting-code-review` | 合并前发起代码审查 |
| `receiving-code-review` | 收到 review 后的技术严谨处理 |
| `finishing-a-development-branch` | 开发分支的收尾与合入 |
| `writing-skills` | 创建和编辑 Claude Code skills |
| `using-superpowers` | Skill 发现与调用规则体系 |

### GSAP 动画

GSAP 官方 skills（来源：[greensock/gsap-skills](https://github.com/greensock/gsap-skills)）。

| Skill | 说明 |
|-------|------|
| `gsap-core` | 核心 API：gsap.to/from/fromTo、缓动、stagger |
| `gsap-timeline` | 时间线编排：序列、嵌套、播放控制 |
| `gsap-scrolltrigger` | 滚动驱动动画：视差、固定、scrub |
| `gsap-react` | React 集成，useGSAP hook |
| `gsap-frameworks` | Vue/Nuxt/Svelte 集成 |
| `gsap-plugins` | 插件集：Flip、Draggable、SplitText、ScrollSmoother 等 |
| `gsap-performance` | 动画性能优化，60fps |
| `gsap-utils` | 工具函数：clamp、mapRange、random、snap |

### 营销 Marketing

覆盖增长、内容、SEO、广告、分析的全链路营销 skill 套件。

**内容与文案**

| Skill | 说明 |
|-------|------|
| `copywriting` | 营销文案写作（落地页、定价页等） |
| `copy-editing` | 审校和润色已有文案 |
| `content-strategy` | 内容策略规划，决定写什么 |
| `social` | 社媒内容创作与排期（LinkedIn/Twitter/TikTok 等） |
| `emails` | 生命周期邮件序列（欢迎、激活、挽回等） |
| `cold-email` | B2B 冷启动外发邮件序列 |
| `sms` | SMS/MMS 营销活动 |
| `image` | AI 图片生成与优化 |
| `video` | AI 视频制作工作流 |
| `ad-creative` | 批量生成广告创意文案 |

**增长与转化**

| Skill | 说明 |
|-------|------|
| `cro` | 转化率优化（CRO） |
| `signup` | 注册/注册流程优化 |
| `onboarding` | 注册后激活与首次体验 |
| `paywalls` | 应用内付费墙与升级弹窗 |
| `popups` | 弹窗/浮层转化元素 |
| `ab-testing` | A/B 测试设计与分析 |
| `lead-magnets` | 引流诱饵（电子书、模板等） |
| `free-tools` | 工程即营销：免费工具引流 |
| `churn-prevention` | 流失预防与挽回策略 |
| `referrals` | 推荐与联盟计划 |
| `launch` | 产品发布规划 |
| `marketing-ideas` | 增长点子头脑风暴 |
| `marketing-psychology` | 行为科学与消费心理在营销中的应用 |

**SEO 与分析**

| Skill | 说明 |
|-------|------|
| `seo-audit` | 技术 SEO 与页面 SEO 审计 |
| `ai-seo` | AI 搜索引擎优化（LLM 引用、Perplexity 等） |
| `programmatic-seo` | 模板化批量生成 SEO 页面 |
| `schema` | 结构化数据与 JSON-LD |
| `analytics` | GA4/GTM 埋点与追踪 |
| `site-architecture` | 站点架构与导航规划 |
| `directory-submissions` | 目录提交获取外链 |
| `aso` | App Store / Google Play 优化 |

**广告与销售**

| Skill | 说明 |
|-------|------|
| `ads` | 付费广告投放（Google/Meta/LinkedIn） |
| `sales-enablement` | 销售物料：Pitch Deck、One-pager、Demo 脚本 |
| `revops` | 收入运营与线索生命周期管理 |
| `pricing` | 定价策略与套餐设计 |
| `product-marketing` | 产品定位与理想客户画像 (ICP) |
| `competitor-profiling` | 竞品研究与分析（输入 URL） |
| `competitors` | 竞品对比页面制作 |
| `customer-research` | 用户调研与访谈分析 |
| `co-marketing` | 联合营销与合作伙伴 |
| `community-marketing` | 社区驱动的增长 |

### 中文特色 Chinese Specialties

来自中文 Claude Code 社区的特色 skills。

| Skill | 说明 |
|-------|------|
| `build-frontend` | 前端页面生成器（Actor-Critic 自评 + 参考图/URL 提取 + Vue/React CDN） |
| `guizang-ppt-skill` | 网页 PPT 生成器（杂志风 / 瑞士国际主义风） |
| `huashu-md-html` | md/html/docx 多向流水线（含视觉设计师模式） |
| `learn-anything-skill` | 万能导师型学习 skill（项目驱动 + Mastery Learning） |
| `webnovel-writer` | 网文写作插件（来自 marketplace，含多流派模板） |

### PPT / 幻灯片 Presentations

覆盖 .pptx 生成、HTML 网页 PPT、手绘风、学术答辩、AI 图片视频等场景。

| Skill | 来源 | 说明 |
|-------|------|------|
| `pptx` | [anthropics/skills](https://github.com/anthropics/skills) | **官方** skill，OOXML 操作，.pptx 全能（创建/读取/编辑） |
| `pptx-generator` | [MiniMax-AI/skills](https://github.com/MiniMax-AI/skills) | 基于 PptxGenJS，含封面/目录/章节封/总结模板 |
| `powerpoint` | [Fergana-Labs/claude_agent_desktop](https://github.com/Fergana-Labs/claude_agent_desktop) | Node.js 工具链创建/操作 .pptx |
| `academic-pptx` | [Gabberflast/academic-pptx-skill](https://github.com/Gabberflast/academic-pptx-skill) | 学术演讲专用（会议/答辩/课题汇报），含 PDF |
| `ppt-skills-handdrawn` | [danny0926/ppt-skills](https://github.com/danny0926/ppt-skills) | 手绘/Excalidraw 风（rough.js + rough-notation + Playwright） |
| `nanobanana-ppt-skills` | [op7418/NanoBanana-PPT-Skills](https://github.com/op7418/NanoBanana-PPT-Skills) | AI 生成 PPT 图片+视频（Nano Banana Pro + 可灵 AI + FFmpeg） |
| `codex-ppt` | [ningzimu/codex-ppt-skill](https://github.com/ningzimu/codex-ppt-skill) | 文档/报告/笔记 → 视觉统一图片 PPT |
| `frontend-slides` | [zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides) | HTML 演示（含 PPTX→HTML 转换），零依赖动画 |
| `data-map-pptx` | 自建（本机沉淀） | 省份/地区评分 → 可编辑中国地图 PPT：Albers 投影自由多边形地图 + 综合排序条 + 维度矩阵表（润岚15省政策图谱同源流水线） |
| `pattern-to-vessel` | 自建（纹脉沉淀） | 纹样卡 → 青铜鼎 3D 浮雕交互页：高度场低通雕刻（防混叠）+ 纹样脱离径向外扩，任意纹样卡两步生成单文件 HTML（含万字纹零调参实测） |

### 竞赛与学术 Competition & Academic

学术竞赛与研究相关 skills。

| Skill | 说明 |
|-------|------|
| `mathmodel-pro` | 数学建模竞赛（国赛 CUMCM / 美赛 MCM/ICM） |
| `biz-analysis-pro` | 商业分析竞赛（全国大学生商赛） |
| `competition-factory` | 竞赛自动识别与分发工作流 |

### 3D / 建模 3D & Modeling

三维生成与交互相关 skills。

| Skill | 说明 |
|-------|------|
| `generate-interactive-web3d` | 单响应生成单文件 Three.js 交互展品（程序化几何 + 爆炸装配 + 构件拾取，09-02 斗拱实测通过） |
| `img2threejs` | 参考图 → 代码重建 Three.js 模型，八道锁定 pass + 确定性门禁脚本 + agent 视觉复审（hoainho，4.2k★，Apache-2.0） |

### 内置 Skills（不在本仓库）

Claude Code 自带的 skills，无需同步：

`init`、`review`、`security-review`、`loop`、`simplify`、`claude-api`、`update-config`、`keybindings-help`、`fewer-permission-prompts`

---

## 添加新 Skill

1. 把 skill 目录复制到本仓库
2. 在 README 对应的分类表格中添加一行
3. 如果是新类别，新建一个 `###` 章节
4. 提交并推送

## 同步回本地

```bash
# 全量同步（不覆盖已有）
cp -r skills-for-myself/*/ ~/.claude/skills/ --no-clobber

# 同步单个 skill
cp -r skills-for-myself/skill-name/ ~/.claude/skills/
```

## 统计

- **79** 个全局 skills
- **1** 个 marketplace 插件（webnovel-writer）

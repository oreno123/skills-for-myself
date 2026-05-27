# Skills for Myself

My personal collection of Claude Code skills, synced from `~/.claude/skills/` and `~/.claude/plugins/`.

## Categories

### Development Workflow

Skills for code quality, planning, and team collaboration.

| Skill | Description |
|-------|-------------|
| `brainstorming` | Creative exploration before implementation |
| `systematic-debugging` | Structured bug investigation workflow |
| `test-driven-development` | TDD discipline for features and bugfixes |
| `writing-plans` | Multi-step implementation plan documents |
| `executing-plans` | Execute plans with review checkpoints |
| `dispatching-parallel-agents` | Parallelize independent tasks |
| `subagent-driven-development` | Subagent-based plan execution |
| `using-git-worktrees` | Isolated workspace management |
| `verification-before-completion` | Evidence-based completion checks |
| `requesting-code-review` | Pre-merge code review |
| `receiving-code-review` | Handle review feedback with rigor |
| `finishing-a-development-branch` | Branch completion and integration |
| `writing-skills` | Create and edit Claude Code skills |
| `using-superpowers` | Skill discovery and invocation rules |

### GSAP Animation

Official GSAP skills for web animation (source: [greensock/gsap-skills](https://github.com/greensock/gsap-skills)).

| Skill | Description |
|-------|-------------|
| `gsap-core` | Core API: gsap.to/from/fromTo, easing, stagger |
| `gsap-timeline` | Timeline sequencing and nesting |
| `gsap-scrolltrigger` | Scroll-linked animations, parallax, pinning |
| `gsap-react` | React integration with useGSAP hook |
| `gsap-frameworks` | Vue/Nuxt/Svelte integration |
| `gsap-plugins` | Flip, Draggable, SplitText, ScrollSmoother, etc. |
| `gsap-performance` | Animation performance optimization |
| `gsap-utils` | Utility functions: clamp, mapRange, random, snap |

### Marketing

Comprehensive marketing skill suite covering growth, content, SEO, ads, and analytics.

**Content & Copy**

| Skill | Description |
|-------|-------------|
| `copywriting` | Marketing copy for any page |
| `copy-editing` | Review and improve existing copy |
| `content-strategy` | Plan what content to create |
| `social` | Social media content and scheduling |
| `emails` | Lifecycle email sequences |
| `cold-email` | B2B cold outreach sequences |
| `sms` | SMS/MMS marketing campaigns |
| `image` | AI image generation and optimization |
| `video` | AI video production workflows |
| `ad-creative` | Ad copy generation at scale |

**Growth & Conversion**

| Skill | Description |
|-------|-------------|
| `cro` | Conversion rate optimization |
| `signup` | Signup/registration flow optimization |
| `onboarding` | Post-signup activation |
| `paywalls` | In-app upgrade screens |
| `popups` | Popup/modal conversion elements |
| `ab-testing` | A/B test design and analysis |
| `lead-magnets` | Lead generation content |
| `free-tools` | Engineering as marketing tools |
| `churn-prevention` | Retention and save offers |
| `referrals` | Referral and affiliate programs |
| `launch` | Product launch planning |
| `marketing-ideas` | Growth brainstorming |
| `marketing-psychology` | Behavioral science in marketing |

**SEO & Analytics**

| Skill | Description |
|-------|-------------|
| `seo-audit` | Technical and on-page SEO audits |
| `ai-seo` | Optimize for AI search engines (LLM citations) |
| `programmatic-seo` | Template-based pages at scale |
| `schema` | Structured data and JSON-LD |
| `analytics` | GA4/GTM tracking setup |
| `site-architecture` | Sitemap and navigation planning |
| `directory-submissions` | Backlinks from directories |
| `aso` | App Store / Google Play optimization |

**Ads & Sales**

| Skill | Description |
|-------|-------------|
| `ads` | Paid advertising campaigns (Google/Meta/LinkedIn) |
| `sales-enablement` | Sales decks, one-pagers, demo scripts |
| `revops` | Revenue operations and lead lifecycle |
| `pricing` | Pricing strategy and packaging |
| `product-marketing` | Product positioning and ICP |
| `competitor-profiling` | Competitor research from URLs |
| `competitors` | Competitor comparison pages |
| `customer-research` | Customer interviews and survey analysis |
| `co-marketing` | Partnership and joint campaigns |
| `community-marketing` | Community-led growth |

### Chinese Specialties

Skills from the Chinese Claude Code community.

| Skill | Description |
|-------|-------------|
| `guizang-ppt-skill` | Web-based PPT (magazine style / Swiss style) |
| `huashu-md-html` | md/html/docx multi-format pipeline |
| `learn-anything-skill` | Universal tutor with mastery learning |
| `webnovel-writer` | Web novel writing plugin (marketplace) |

### Competition & Academic

Skills for academic competitions and research.

| Skill | Description |
|-------|-------------|
| `mathmodel-pro` | Mathematical modeling competition (CUMCM/MCM/ICM) |
| `biz-analysis-pro` | Business analysis competition |
| `competition-factory` | Auto-dispatch competition workflows |

### Built-in Skills (not in this repo)

These come bundled with Claude Code and don't need syncing:

`init`, `review`, `security-review`, `loop`, `simplify`, `claude-api`, `update-config`, `keybindings-help`, `fewer-permission-prompts`

---

## Adding New Skills

1. Copy the skill directory into this repo
2. Add an entry to the appropriate category table in this README
3. If it's a new category, add a new section
4. Commit and push

## Sync Back to Local

```bash
# Sync all skills from repo to Claude Code
cp -r skills-for-myself/*/ ~/.claude/skills/ --no-clobber

# Or sync a specific skill
cp -r skills-for-myself/skill-name/ ~/.claude/skills/
```

## Stats

- **69** global skills
- **1** marketplace plugin (webnovel-writer)
- **70** directories total

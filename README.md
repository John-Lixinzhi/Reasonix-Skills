# Reasonix AI Agent Skills

[![GitHub stars](https://img.shields.io/github/stars/John-Lixinzhi/Reasonix-Skills?style=flat-square)](https://github.com/John-Lixinzhi/Reasonix-Skills/stargazers)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/John-Lixinzhi/Reasonix-Skills/pulls)

**47 production-ready agent skills · 9 categories · Auto-triggering**

A collection of agent skills for AI coding assistants — Claude Code, Codex, Cursor, and any agent that reads `SKILL.md` files. Each skill knows when to activate itself. You don't tell the agent which skill to use; the agent figures it out from the conversation.

---

## Quickstart (10-second setup)

```bash
npx skills add John-Lixinzhi/reasonix-skills
```

That's it. Now try saying things like:

> "Help me think through this feature"
> "Write a test for this code"
> "Make a Swiss-style web PPT"
> "Look up the citations for this paper"
> "Debug this error — I don't know what's wrong"

The agent automatically matches your intent to the right skill. No manual routing needed.

---

## Why These Skills Exist

Skills exist because **prompts are brittle and context is expensive**. Every time you tell an agent *how* to do something — "first reproduce the bug, then isolate the root cause, then fix it" — you're burning tokens on instructions that should be baked in.

Each `SKILL.md` is a pre-loaded playbook. It tells the agent what to do, when to do it, and — just as importantly — **when NOT to do it**. The agent reads the skill, understands its boundaries, and executes. No repetition, no forgetting steps, no hallucinations about the process.

Here's what the current collection helps you with.

### 🔬 You Need a Systematic Engineering Process

The most common failure mode in AI-assisted development is the agent running off in a random direction. You ask for a feature, it starts coding immediately, and what comes back doesn't match what you had in mind.

**The Fix** is a set of disciplines that force alignment before execution:

- **[/grill-me](./skills/dev/grill-me/SKILL.md)** — Before you start, let the agent interview you relentlessly about your plan. Every branch of the decision tree gets resolved before a single line of code is written.
- **[/superpowers-brainstorming](./skills/dev/superpowers-brainstorming/SKILL.md)** — When requirements are fuzzy, this produces a structured design doc and gets your approval before moving forward.
- **[/superpowers-writing-plans](./skills/dev/superpowers-writing-plans/SKILL.md)** — Once the design is approved, break it into 2-5 minute executable tasks with file paths, expected changes, and verification steps.
- **[/domain-modeling](./skills/dev/domain-modeling/SKILL.md)** — When the agent and you are using different words for the same thing, build a shared glossary. This pays off in every subsequent session.

After alignment comes **execution discipline**:

- **[/superpowers-tdd](./skills/dev/superpowers-tdd/SKILL.md)** — Red-green-refactor. Write the failing test first, then the minimal code to pass it, then refactor. The feedback loop catches mistakes instantly.
- **[/superpowers-debugging](./skills/dev/superpowers-debugging/SKILL.md)** — Four-phase root cause analysis: reproduce → isolate → locate → fix + verify. No guessing.
- **[/diagnosing-bugs](./skills/dev/diagnosing-bugs/SKILL.md)** — For the really nasty ones — intermittent issues, performance regressions — a five-step loop: reproduce, minimize, hypothesize, probe, fix + regression test.
- **[/code-simplifier](./skills/dev/code-simplifier/SKILL.md)** — Refactor for readability without changing behavior.
- **[/ponytail](./skills/dev/ponytail/SKILL.md)** — Before writing code, check for over-engineering. A five-level ladder: YAGNI → stdlib → native → deps → one-liner.

And finally, **quality gates**:

- **[/superpowers-review](./skills/dev/superpowers-review/SKILL.md)** — Code review by severity, against the plan.
- **[/superpowers-verify](./skills/dev/superpowers-verify/SKILL.md)** — Before claiming done, run the verification commands and confirm output.
- **[/security-guidance](./skills/dev/security-guidance/SKILL.md)** — Three-layer security review: pattern warnings, LLM diff review, agentic commit audit.
- **[/improve-codebase-architecture](./skills/dev/improve-codebase-architecture/SKILL.md)** — Scan the whole codebase for architecture rot, get an HTML report, then fix things one by one.

> [!TIP]
> The **Superpowers** suite (brainstorming → plans → tdd → debugging → review → verify) forms a complete engineering workflow. Many users run them as a pipeline on every feature.

### 📊 You Work With Data

- **[/scrapling-agent-skill](./skills/data/scrapling-agent-skill/SKILL.md)** — Scrape websites, bypass Cloudflare, extract structured data. Uses the Scrapling MCP under the hood.
- **[/excel-table-processor](./skills/data/excel-table-processor/SKILL.md)** — Process student attendance and Excel tables with format preservation, pinyin sorting, and auto-renumbering.

### 🎯 You Need Presentations — Real Ones

This is the deepest category in the collection: **12 skills** covering the full PPT pipeline. Whether you need a quick web deck or a polished, editable PPTX with animations, there's a skill for that stage.

**Planning & style:**

- **[/guizang-ppt-skill](./skills/ppt/guizang-ppt-skill/SKILL.md)** — Generate horizontal-scroll web PPTs in magazine or Swiss International Style.
- **[/visual-style-ppt-skill](./skills/ppt/visual-style-ppt-skill/SKILL.md)** — Extract a design system from reference images and apply it consistently.
- **[/premium-visual-guide](./skills/ppt/premium-visual-guide/SKILL.md)** — Make it look high-end: color system, typography, whitespace, background design.

**Production:**

- **[/ppt-master](./skills/ppt/ppt-master/SKILL.md)** — Generate editable PPTX files with precise control (pptxgenjs-based).
- **[/ppt-workflow](./skills/ppt/ppt-workflow/SKILL.md)** — The full pipeline from content to design to animation to export.

**Animation & effects:**

- **[/ppt-motion](./skills/ppt/ppt-motion/SKILL.md)** — Slide transitions and entry animations.
- **[/ppt-creative-animation](./skills/ppt/ppt-creative-animation/SKILL.md)** — Opening animations, rotating wreaths, film reel, 3D, text reveals, cutout covers.
- **[/ppt-transitions](./skills/ppt/ppt-transitions/SKILL.md)** — Morph, zoom, parallax, and carousel effects.
- **[/ppt-dynamic-layout](./skills/ppt/ppt-dynamic-layout/SKILL.md)** — Parallelogram splits, diamond layouts, gradient text, mirror effects.

**Data & style:**

- **[/ppt-data-visualization](./skills/ppt/ppt-data-visualization/SKILL.md)** — Charts, KPIs, data storytelling, infographics.
- **[/ppt-douyin-style](./skills/ppt/ppt-douyin-style/SKILL.md)** — High-impact, short-video style: deep backgrounds, high contrast, bold fonts, fast-paced.
- **[/ppt-image-processing](./skills/ppt/ppt-image-processing/SKILL.md)** — Boolean operations, image fills, circular layouts, transparency.

### 🎨 You Build Frontends

- **[/frontend-design](./skills/design/frontend-design/SKILL.md)** — UI/UX design driven by a design system. Page layout, component design, consistent interfaces.

### ⚙️ You Run the Skill Ecosystem

These skills manage the skill system itself:

- **[/skill-router](./skills/system/skill-router/SKILL.md)** — When multiple skills could match, this queries the catalog, ranks candidates, and dispatches.
- **[/skill-onboarder](./skills/system/skill-onboarder/SKILL.md)** — Install new skills into the ecosystem: fetch, analyze, install, update catalog.
- **[/skillspector-wrapper](./skills/system/skillspector-wrapper/SKILL.md)** — Scan skills for 64 vulnerability patterns before installing.
- **[/skillopt-wrapper](./skills/system/skillopt-wrapper/SKILL.md)** — Auto-improve skill quality with trajectory-driven, validation-gated edits.
- **[/github-publish-flow](./skills/system/github-publish-flow/SKILL.md)** — Push skill updates and create repos via local commit + GitHub API.

### 🛠️ You Need Tools

- **[/powertoys-skill](./skills/tools/powertoys-skill/SKILL.md)** — Windows PowerToys integration: color picker, batch rename, window layout, screenshot.
- **[/handoff](./skills/tools/handoff/SKILL.md)** — Compact a conversation into a handoff document so another agent can pick up where you left off.
- **[/cua-skill](./skills/tools/cua-skill/SKILL.md)** — Let the AI control your desktop: mouse, keyboard, screenshots (macOS / Windows / Linux).
- **[/pixelle-video-skill](./skills/tools/pixelle-video-skill/SKILL.md)** — Generate short videos from a topic or script, with digital human support.
- **[/agent-reach-skill](./skills/tools/agent-reach-skill/SKILL.md)** — Collect data from Twitter, Bilibili, Xiaohongshu, Reddit, LinkedIn — no API fees.

### 📖 You Need Reference

- **[/system-prompt-leaks-skill](./skills/reference/system-prompt-leaks-skill/SKILL.md)** — Study collected system prompts from Anthropic, OpenAI, Google, xAI, and others.
- **[/writing-great-skills](./skills/reference/writing-great-skills/SKILL.md)** — Best practices for writing your own skills: predictable, composable, bounded.
- **[/skeptical-cognition](./skills/reference/skeptical-cognition/SKILL.md)** — Six-step framework for evaluating information credibility.
- **[/humanize-skill](./skills/reference/humanize-skill/SKILL.md)** — Detect and reduce AI traces in text using 9 levers, with forensic scoring.

### 🔬 You Do Research

- **[/ml-intern-skill](./skills/research/ml-intern-skill/SKILL.md)** — Autonomous ML research: read papers, train models, deploy via HuggingFace.
- **[/matlab-research](./skills/research/matlab-research/SKILL.md)** — MATLAB programming, research plotting, signal processing with R2025b toolkits.
- **[/research-writing](./skills/research/research-writing/SKILL.md)** — Literature search, review writing, IMRaD structure, BibTeX management.
- **[/devils-advocate](./skills/research/devils-advocate/SKILL.md)** — Stress-test your research ideas with a concession-threshold debate protocol.
- **[/research-pipeline](./skills/research/research-pipeline/SKILL.md)** — Ten-stage research project orchestrator with integrity gates at each stage.
- **[/ralph-loop](./skills/dev/ralph-loop/SKILL.md)** — Rapid iteration loop for experimental development. Auto-feedback until truly done.

### 🏆 You Compete

- **[/math-modeling](./skills/competition/math-modeling/SKILL.md)** — For math modeling competitions: model selection, code templates, paper writing. Covers regression, optimization, and more.

---

## Design Principles

Every skill in this repo follows a consistent description convention:

```
USE when  <trigger scenario>
DO        <what the skill does>
NOT for   <when it should NOT be used>
Triggers: <keywords for auto-matching>
```

This lets the agent **auto-trigger** the right skill from natural conversation. You don't say "use the debugging skill" — you say "this code is broken, why?" and the agent matches it.

The catalog (`SKILLS_CATALOG.json`) adds structured metadata: category, tags, dependencies, priority, and negative samples — used by the skill-router for disambiguation.

---

## Local Development

```bash
git clone https://github.com/John-Lixinzhi/Reasonix-Skills.git
cd Reasonix-Skills
# Skills live in skills/{category}/{skill-name}/SKILL.md
# Edit, commit, and PR
```

---

## Acknowledgments

These skills are adapted from or inspired by several excellent open-source projects:

- [obra/superpowers](https://github.com/obra/superpowers) — Engineering methodology framework
- [mattpocock/skills](https://github.com/mattpocock/skills) — Skills for Real Engineers
- [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) — Security scanning
- [microsoft/SkillOpt](https://github.com/microsoft/SkillOpt) — Skill optimization
- [op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill) — Web PPT generation
- [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) — Cross-platform data collection
- [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) — Research skills

---

<div align="center">

**Skills over prompts. Let the agent decide when to use what.**

</div>

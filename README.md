<div align="center">

# Reasonix AI Agent Skills

**47 production-ready agent skills 路 9 categories 路 Auto-triggering**

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/John-Lixinzhi/Reasonix-Skills/pulls)

</div>

A collection of agent skills for AI coding assistants (Claude Code, Cursor, Codex, etc.). Each skill describes when to trigger, what to do, and when not to use it. The AI reads it and decides for itself.

---

## Quick Start

```bash
npx skills add John-Lixinzhi/reasonix-skills
```

Then try:

> "Help me think through this feature"  
> "Write tests for this code"  
> "Make a Swiss-style PPT"  
> "Check this paper's citations"

The AI will match the right skill automatically.

---

## Skills

### 馃敩 Development (14)

`brainstorming` 路 `tdd` 路 `debugging` 路 `verify` 路 `writing-plans` 路 `review` 路 `security-guidance` 路 `code-simplifier` 路 `ralph-loop` 路 `ponytail` 路 `grill-me` 路 `diagnosing-bugs` 路 `domain-modeling` 路 `improve-codebase-architecture`

### 馃搳 Data (2)

`scrapling-agent-skill` 路 `excel-table-processor`

### 馃幆 Office/PPT (12)

`guizang-ppt-skill` 路 `ppt-master` 路 `visual-style-ppt-skill` 路 `premium-visual-guide` 路 `ppt-motion` 路 `ppt-dynamic-layout` 路 `ppt-creative-animation` 路 `ppt-transitions` 路 `ppt-data-visualization` 路 `ppt-douyin-style` 路 `ppt-image-processing` 路 `ppt-workflow`

### 馃帹 Design (1)

`frontend-design`

### 鈿欙笍 System (4)

`skill-router` 路 `skill-onboarder` 路 `skillspector-wrapper` 路 `skillopt-wrapper`

### 馃洜锔?Tools (5)

`powertoys-skill` 路 `handoff` 路 `cua-skill` 路 `pixelle-video-skill` 路 `agent-reach-skill`

### 馃摉 Reference (4)

`system-prompt-leaks-skill` 路 `writing-great-skills` 路 `skeptical-cognition` 路 `humanize-skill`

### 馃敩 Research (5)

`ml-intern-skill` 路 `matlab-research` 路 `research-writing` 路 `devils-advocate` 路 `research-pipeline`

### 馃弳 Competition (1)

`math-modeling`

---

## Skill Design

Every skill follows this format:

```
description: [category] name - USE when [trigger]. DO [what it does]. NOT for [exclusions]. Triggers: [keywords]
```

This lets the AI match skills automatically. Say "help me debug this" and debugging fires without being told.

---

## Contributing

```bash
git clone https://github.com/John-Lixinzhi/Reasonix-Skills.git
# Skills live in skills/{category}/{name}/SKILL.md
# Submit a PR with your changes
```

---

## Credits

Inspired by [obra/superpowers](https://github.com/obra/superpowers), [mattpocock/skills](https://github.com/mattpocock/skills), [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector), [microsoft/SkillOpt](https://github.com/microsoft/SkillOpt), [op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill), [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach), [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills).

---

<div align="center">

**Skills over prompts. Let the AI decide.**

</div>
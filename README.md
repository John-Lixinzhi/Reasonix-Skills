<div align="center">

# Reasonix AI Agent Skills

**47 production-ready agent skills 路 9 categories 路 Auto-triggering**

[![GitHub stars](https://img.shields.io/github/stars/John-Lixinzhi/Reasonix-Skills?style=flat-square)](https://github.com/John-Lixinzhi/Reasonix-Skills/stargazers)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

</div>

---

## What is this

A collection of agent skills for AI coding assistants.

Each skill is a SKILL.md file that describes when to trigger, what to do, and when NOT to use it. The AI reads it and decides for itself 鈥?no need to manually specify every time.

Currently **47 skills** across 9 categories: Development, Data, Office/PPT, Design, System, Tools, Reference, Research, Competition.

---

## Quick Install

```bash
npx skills add John-Lixinzhi/reasonix-skills
```

Then try in your AI assistant (Claude Code, Cursor, Codex, etc.):

> "Help me think through this feature"
> "Write tests for this code"
> "Make a Swiss-style PPT"
> "Check this paper's citations"

The AI will automatically match the right skill.

---

## Skills Overview

### 馃敩 Development (14 skills)

| Skill | When to use |
|-------|-------------|
| **brainstorming** | New feature, fuzzy requirements, need to think first |
| **tdd** | Before writing code. Test first, then implement |
| **debugging** | Code errors, unexpected behavior, unknown cause |
| **verify** | Before claiming done. Run verification commands |
| **writing-plans** | Design approved, break into executable tasks |
| **review** | Code is done, need a review |
| **security-guidance** | Security audit, find vulnerabilities |
| **code-simplifier** | Code is too complex, simplify it |
| **ralph-loop** | Iterative polishing, rapid feedback cycles |
| **ponytail** | Check for unnecessary code, YAGNI |
| **grill-me** | Requirements unclear, get grilled first |
| **diagnosing-bugs** | Complex bugs, systematic troubleshooting |
| **domain-modeling** | Project terminology娣蜂贡, build shared glossary |
| **improve-codebase-architecture** | Code quality degrading, architecture checkup |

### 馃搳 Data (2 skills)

| Skill | When to use |
|-------|-------------|
| **scrapling-agent-skill** | Web scraping, anti-bot bypass |
| **excel-table-processor** | Excel spreadsheet processing, preserve formatting |

### 馃幆 Office/PPT (12 skills)

| Skill | When to use |
|-------|-------------|
| **guizang-ppt-skill** | HTML web PPT, magazine or Swiss style |
| **ppt-master** | Generate editable PPTX files |
| **visual-style-ppt-skill** | Reference image based style-consistent design |
| **premium-visual-guide** | Make PPTs look premium |
| **ppt-motion** | Slide transition animations |
| **ppt-dynamic-layout** | Creative layouts: parallelogram, diamond, etc. |
| **ppt-creative-animation** | Opening effects: rotating wreath, film reel |
| **ppt-transitions** | Morph transitions, Zoom navigation |
| **ppt-data-visualization** | Turn data into charts |
| **ppt-douyin-style** | High-impact short-video style presentations |
| **ppt-image-processing** | Boolean operations, image fill |
| **ppt-workflow** | Standard PPT production pipeline |

### 馃帹 Design (1 skill)

| Skill | When to use |
|-------|-------------|
| **frontend-design** | UI/UX design, page layout |

### 鈿欙笍 System (4 skills)

| Skill | When to use |
|-------|-------------|
| **skill-router** | Multiple skills match, auto-route |
| **skill-onboarder** | New skill needs onboarding |
| **skillspector-wrapper** | Security scan before installing skills |
| **skillopt-wrapper** | Auto-optimize skill quality |

### 馃洜锔?Tools (5 skills)

| Skill | When to use |
|-------|-------------|
| **powertoys-skill** | Windows PowerToys: color picker, window layout |
| **handoff** | Switch between AI agents, preserve context |
| **cua-skill** | AI desktop control (mouse, keyboard, screenshots) |
| **pixelle-video-skill** | AI auto video generation from topic |
| **agent-reach-skill** | Multi-platform data collection: Twitter, Bilibili, Xiaohongshu |

### 馃摉 Reference (4 skills)

| Skill | When to use |
|-------|-------------|
| **system-prompt-leaks-skill** | Reference AI system prompt designs |
| **writing-great-skills** | Guide for writing quality skills |
| **skeptical-cognition** | Evaluate information credibility |
| **humanize-skill** | AI text detection and humanization |

### 馃敩 Research (5 skills)

| Skill | When to use |
|-------|-------------|
| **ml-intern-skill** | Read papers, train models, deploy |
| **matlab-research** | MATLAB computation and plotting |
| **research-writing** | Literature search, review writing, citation management |
| **devils-advocate** | Stress-test research ideas before writing |
| **research-pipeline** | Full research project lifecycle management |

### 馃弳 Competition (1 skill)

| Skill | When to use |
|-------|-------------|
| **math-modeling** | Math modeling competitions: models + code + paper |

---

## Skill Design

Every skill description follows this format:

```
USE when [trigger scenario]
DO   [what it does]
NOT for [exclusions]
Triggers: [keywords]
```

This way when the user says "help me debug this error", the AI automatically matches the debugging skill without being told to.

---

## Local Development

```bash
git clone https://github.com/John-Lixinzhi/Reasonix-Skills.git
cd Reasonix-Skills
# Skills live in skills/{category}/{skill-name}/SKILL.md
# Edit and submit a PR
```

---

## Credits

These skills are adapted from or inspired by several excellent open-source projects:

- [obra/superpowers](https://github.com/obra/superpowers) 鈥?Agentic skills framework
- [mattpocock/skills](https://github.com/mattpocock/skills) 鈥?Skills for Real Engineers
- [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) 鈥?Security scanner
- [microsoft/SkillOpt](https://github.com/microsoft/SkillOpt) 鈥?Skill optimization
- [op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill) 鈥?Web PPT
- [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) 鈥?Data collection
- [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) 鈥?Research skills

---

<div align="center">

**Skills over prompts. Let the AI decide when to use what.**

</div>

# Reasonix Skills

Skills are organized into bucket folders under `skills/`:

- `dev/` — Engineering methodology and code workflow (Superpowers suite, debugging, architecture)
- `data/` — Web scraping and spreadsheet processing
- `ppt/` — Presentation generation (web PPT, PPTX, animations, data viz)
- `design/` — Frontend UI/UX design
- `system/` — Skill ecosystem management (router, onboarder, scanner, optimizer)
- `tools/` — Desktop utilities, handoff, video generation, social-media collection
- `reference/` — Prompt engineering, skill-writing guides, critical thinking
- `research/` — ML, MATLAB, literature review, research pipeline
- `competition/` — Math modeling competition toolkit

## Rules for Agents

1. **Read `SKILLS_CATALOG.json`** for the full index with metadata — category, tags, triggers, negative samples, dependencies, and priority. Use the catalog to disambiguate when multiple skills could match.

2. **Browse `skills/{category}/{skill-name}/SKILL.md`** for the actual playbook. Each skill file contains the full instructions: when to USE it, what to DO, and when NOT to use it.

3. **Auto-trigger from conversation.** Do not wait for the user to name a skill. Match the user's intent against the `Triggers` field in the skill descriptions. For example, if the user says "this code is broken, why?" and the `diagnosing-bugs` skill lists `Triggers: bug/error/debug/why is this failing`, you should activate it.

4. **Respect `negative_samples`.** Every skill explicitly lists scenarios where it should NOT be used. If the current situation matches a negative sample, do not invoke that skill even if the positive triggers also match.

5. **Use `skill-router` for ambiguity.** When your confidence in selecting a single skill is low, invoke the skill-router to query the catalog, rank candidates, and dispatch.

6. **Skill chaining** is allowed: a skill may invoke other skills it depends on (declared in its `dependencies` field). This is how the Superpowers suite chains brainstorming → plans → tdd → review → verify.

7. **Never modify `SKILL.md` files** during normal execution. Skills are read-only artifacts. If a skill needs improvement, use `writing-great-skills` as a reference and submit a PR.

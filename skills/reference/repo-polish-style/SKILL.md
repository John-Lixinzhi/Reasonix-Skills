---
name: repo-polish-style
description: "[reference] Repo polish style — USE when polishing README/repo docs for professional look. DO follow mattpocock-style narrative + encoding-safe push. NOT for code changes. Triggers: polish README/improve repo/docs look professional/formalize descriptions/style repo"
---

# Repo Polish Style — 仓库文档修饰指南

Polish your GitHub repository README and docs with a professional, narrative-driven style inspired by [mattpocock/skills](https://github.com/mattpocock/skills). This skill covers both the **writing style** and the **technical encoding techniques** to ensure emojis/icons survive the push.

## Core Style Principles

### 1. Narrative-Driven, Not Feature-List
Don't just list features — tell a story. Answer "why does this exist?" before "what's in it?"

| ❌ Flat listing | ✅ Narrative-driven |
|---------------|-------------------|
| `- Feature A` `- Feature B` `- Feature C` | A problem paragraph → **The Fix** → skills as solutions |
| `## Install` `## Usage` `## API` | `## Why This Exists` → `## Quickstart` → `## Reference` |

### 2. Problem → Solution Format
For each major section, frame it as:

```
**The Problem**: <one sentence about what goes wrong>
**The Fix**: <one sentence about how the skills solve it>
- **[/skill-name](./path/SKILL.md)** — <one-line active description>
```

This is the core pattern from mattpocock. It makes the README scannable and compelling.

### 3. Quickstart First
Put the install command at the top so readers can try immediately. Use:

```
## Quickstart (10-second setup)

\`\`\`bash
npx skills add owner/repo
\`\`\`

Now try saying things like:
> "Example prompt 1"
> "Example prompt 2"
```

### 4. Personal Voice
Write as if one engineer talking to another. Use:
- **Bold** for emphasis on key concepts
- `Inline code` for file names and commands
- > Blockquotes for insightful quotes or tips
- > [!TIP] GitHub alerts for callouts

### 5. Every Skill Gets a One-Line Description
Format each skill reference as:

```
- **[/skill-name](./path/SKILL.md)** — Active-verb description (≤15 words)
```

The description should start with a verb and tell what the skill *does*, not what it *is*.

### 6. Group Related Skills
Don't dump all 47 skills in one flat list. Group them:
- By category heading (with emoji)
- By sub-group (Planning & style / Production / Animation & effects)
- The deepest category gets special treatment (e.g. "This is the deepest category: **12 skills** covering the full pipeline")

### 7. End with Principles and Acknowledgments
- A **Design Principles** section explaining the consistent format
- A **Local Development** section for contributors
- An **Acknowledgments** section crediting sources
- A centered motto as the closing line

---

## Encoding Preservation (Emoji/Icon Safety)

This is critical. Pushing files with emojis via API **will corrupt them** if you use the wrong encoding method.

### ✅ Correct: Read as bytes → Base64

```powershell
# PowerShell — safe for emoji
$bytes = [System.IO.File]::ReadAllBytes("path/to/file.md")
$b64 = [Convert]::ToBase64String($bytes)

# Then include $b64 as the "content" field in the API JSON payload
```

```bash
# Linux/macOS/WSL — safe for emoji
base64 -w0 README.md > /tmp/encoded.txt
# or
cat README.md | base64 -w0
```

### ❌ Wrong: Read as text then encode

```powershell
# PowerShell — DESTROYS emoji!
$content = Get-Content -Raw "file.md"  # ❌ Corrupts multi-byte chars
$b64 = [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes($content))
```

### Full API Push Example (PowerShell)

```powershell
$token = "YOUR_GITHUB_TOKEN"
$sha = "current_file_sha_from_github"

$content = [Convert]::ToBase64String(
    [System.IO.File]::ReadAllBytes("D:\Repo\README.md")
)

$body = @{
    message = "docs: describe the change"
    content = $content
    sha     = $sha
    branch  = "main"
} | ConvertTo-Json

Invoke-RestMethod -Uri "https://api.github.com/repos/owner/repo/contents/README.md" `
    -Method PUT -Body $body -ContentType "application/json" `
    -Headers @{Authorization = "Bearer $token"}
```

### Full API Push Example (curl / bash)

```bash
TOKEN="YOUR_GITHUB_TOKEN"
SHA="current_file_sha"

curl -s -X PUT "https://api.github.com/repos/owner/repo/contents/README.md" \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d "$(printf '{"message":"docs: describe change","content":"%s","sha":"%s","branch":"main"}' \
       "$(base64 -w0 README.md)" "$SHA")"
```

### Key Rules
- **Always** use `ReadAllBytes` (PowerShell) or `base64` CLI (Linux) — never `Get-Content` or text readers
- The JSON payload's `"content"` field must be the **Base64 of the raw bytes**, not of a UTF8 string derived from text
- Files must be **UTF-8 without BOM** before encoding
- Verify the result by fetching the raw content from GitHub after push

---

## README Structure Template

```
# Project Title
[![badges](url)](link)

**Tagline:** N skills · M categories · Auto-triggering

One-paragraph elevator pitch explaining what this is.

---

## Quickstart (X-second setup)

\`\`\`bash
install command
\`\`\`

Example prompts the reader can try immediately.

---

## Why This [Project] Exists

Skills exist because <core problem statement>.

Here's what the collection helps you with.

### 🔬 Category 1 — Problem Name

**The Problem**: <what goes wrong>

**The Fix**: <how the skills fix it>

- **[/skill-a](./path/SKILL.md)** — Active description.
- **[/skill-b](./path/SKILL.md)** — Active description.

> [!TIP]
> Callout for an important note.

### 📊 Category 2 — ...

... (repeat for each category)

---

## Design Principles

Every skill follows a consistent format:

\`\`\`
USE when  <trigger scenario>
DO        <instructions>
NOT for   <when not to use>
Triggers: <keywords>
\`\`\`

---

## Local Development

\`\`\`bash
git clone ...
cd repo
# edit skills/{category}/{name}/SKILL.md
\`\`\`

---

## Acknowledgments

- [Source A](url) — Description
- [Source B](url) — Description

---

<div align="center">

**Motto.**
</div>
```

---

## What NOT to Do

- ❌ Don't write in Chinese if the repo uses English (keep consistent)
- ❌ Don't use tables for skill lists — they're less scannable than bold lists
- ❌ Don't bury the install command at the bottom
- ❌ Don't describe skills by what they *are* ("This is a debugging skill") — describe by what they *do* ("Debug systematically with a 4-phase RCA loop")
- ❌ Don't use `Get-Content` when encoding files with emoji
- ❌ Don't push via `git` if the network is unreliable — use GitHub API directly
- ❌ Don't forget to update `SKILLS_CATALOG.json` when adding new skills

## Self-Checklist

Before submitting, verify:
- [ ] Quickstart is visible above the fold
- [ ] Every section follows problem → solution structure
- [ ] All emojis/icons survived the push (check raw URL)
- [ ] Every skill link points to a real SKILL.md
- [ ] Consistent voice throughout (no mixing formal/casual)
- [ ] Design Principles section explains the format
- [ ] Acknowledgments section credits sources
- [ ] No tables used for skill lists (use bold lists instead)

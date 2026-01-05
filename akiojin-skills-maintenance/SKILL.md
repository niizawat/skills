---
name: akiojin-skills-maintenance
description: "Add or update skills in the akiojin/skills repository for Codex and/or Claude Code. Use when creating new skills, packaging .skill files for Codex, or converting a skill into a Claude Code plugin (marketplace.json + plugin.json updates)."
---

# Akiojin Skills Maintenance

## Overview

Maintain the akiojin/skills repository and keep Codex + Claude Code artifacts in sync.

## Workflow

### 1) Decide the target runtime(s)

- **Codex only**: add a skill folder with `SKILL.md` at repo root.
- **Claude Code only**: add a plugin folder with `.claude-plugin/plugin.json` and update `.claude-plugin/marketplace.json`.
- **Both**: do both of the above and package `.skill` files for Codex.

### 2) Create the skill content

- Skill folder must contain `SKILL.md` with proper YAML frontmatter (`name`, `description`).
- Keep names lowercase + hyphens.
- Put additional materials under `references/`, `scripts/`, `assets/` as needed.

### 3) Claude Code plugin requirements (if applicable)

- Plugin lives at repo root (e.g. `drawio/`, `gh-fix-ci/`, `cli-design/`).
- Add `.claude-plugin/plugin.json` inside the plugin folder.
- Add an entry to `.claude-plugin/marketplace.json`:
  - `name`, `source`, `description`, `version`, `category`, `keywords`
- If the plugin contains multiple skills, place them under `<plugin>/skills/<skill-name>/SKILL.md`.

### 4) Codex packaging (if applicable)

- Package to `codex-skills/dist/` using the skill packager.
- On Windows, set UTF-8 to avoid decode errors.

```powershell
$env:PYTHONUTF8=1
$codexHome = $env:CODEX_HOME
if (-not $codexHome) { $codexHome = "$env:USERPROFILE\.codex" }
python "$codexHome\skills\.system\skill-creator\scripts\package_skill.py" `
  "E:\gwt\.worktrees\akiojin-skills\<skill-folder>" `
  "E:\gwt\.worktrees\akiojin-skills\codex-skills\dist"
```

Repeat for each Codex-supported skill.

### 5) Update documentation

- `README.md`
  - Add to **Available Plugins** and **Usage (Claude Code)** when pluginized.
  - Add to **Available Codex skills** and **Usage (Codex)** when packaged.

### 6) Commit + push

- Ensure `codex-skills/dist/*.skill` are tracked for Codex delivery.
- Push changes and open PR if required by your workflow.

## Notes

- Codex reads skills from `.codex/skills` folders; `.skill` is a packaged zip for distribution.
- Claude Code requires the plugin entry in `.claude-plugin/marketplace.json`.

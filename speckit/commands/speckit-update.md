---
description: Update the GitHub Spec Kit base version and sync templates/scripts
author: akiojin
allowed-tools: Read, Glob, Grep, Write, Bash
---

# Spec Kit Update Command

Use this command to sync your local Spec Kit setup with upstream GitHub releases.

## Usage

```
/speckit:speckit-update [target version]
```

## Steps

1. Load `speckit/skills/speckit-update/SKILL.md` and follow the workflow.
2. Preserve local constraints: **日本語**, **ブランチ非操作**, **SPEC-[UUID8桁]**.
3. Update version references in docs after syncing.

## Examples

```
/speckit:speckit-update v0.0.90
```

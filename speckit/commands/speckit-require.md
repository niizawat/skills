---
description: Run the Spec Kit requirements workflow (specify/clarify/plan/tasks)
author: akiojin
allowed-tools: Read, Glob, Grep, Write, Bash
---

# Spec Kit Requirements Command

Use this command to create or update requirements with Spec Kit and generate `spec.md → plan.md → tasks.md`.

## Usage

```
/speckit:speckit-require [feature description|SPEC-ID]
```

## Steps

1. Load `speckit/skills/speckit-require/SKILL.md` and follow the workflow.
2. Ensure outputs remain **日本語** and SPEC ID is **SPEC-[UUID8桁]**.
3. Do not create or switch branches (user-managed only).

## Examples

```
/speckit:speckit-require 新しい認証フローを追加
```

```
/speckit:speckit-require SPEC-1234abcd 追記
```

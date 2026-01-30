---
description: Inspect and fix failing GitHub Actions checks using the gh-fix-ci skill
author: akiojin
allowed-tools: Read, Glob, Grep, Bash
---

# GitHub CI Fix Command

Use this command to diagnose and fix CI failures for a PR.

## Usage

```
/github:gh-fix-ci [pr-number|pr-url|optional context]
```

## Steps

1. Load `github/skills/gh-fix-ci/SKILL.md` and follow the workflow.
2. Run the inspection script to gather CI results.
3. Propose fixes and apply them after user approval.

## Examples

```
/github:gh-fix-ci 123
```

```
/github:gh-fix-ci https://github.com/org/repo/pull/123
```

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A Claude Code skill (`SKILL.md`) that strips AI writing patterns from prose. It scores text on 5 dimensions, identifies violations of 8 core rules, rewrites the text, and re-scores. Based on [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) (MIT).

There is no build system, test suite, or package manager. The repository is purely markdown files.

## Files

- `SKILL.md` — The skill itself. Install by copying it to `.claude/commands/stop-slop.md` in a project, or to `skills/stop-slop/SKILL.md` as a standalone directory.
- `feedback.log` — Persistent learning log. The skill reads this before every execution and appends new corrections during use. Edit it directly to add permanent preferences.
- `README.md` — Install instructions and a summary of the 8 rules.

## How the skill works

Invocation with existing text: score → identify violations → rewrite → re-score → show before/after.

Invocation with an instruction (e.g. "write an email to..."): draft following all 8 rules → score → revise until ≥ 35/50.

The 5 scoring dimensions are directness, rhythm, trust, authenticity, and density (each 1–10). A total below 35/50 triggers a rewrite.

## feedback.log conventions

- One entry per line, prefixed with an ISO date (`YYYY-MM-DD: ...`).
- Log general stylistic preferences that apply across future sessions, not task-specific details.
- The skill appends to this file automatically during use; you can also append manually.

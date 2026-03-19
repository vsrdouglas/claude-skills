---
name: show-active-skills
description: Use on every interaction. Lists which skills are active in each response, grouped by scope (user vs project). Always show the skills header before any other content — no exceptions.
---

# Show Active Skills

## Why This Exists

The user wants full transparency into which skills Claude is using in every response, and crucially, wants to know **where each skill comes from** — whether it's a personal user-level skill or a project-specific one.

## How to Apply

At the **very beginning** of every response, before any other content, include a skills header that groups active skills by scope.

### Format

```
**Skills (user):** skill-a, skill-b
**Skills (project):** skill-c, skill-d
```

- **user** = skills from `~/.claude/skills/` — these follow the user across all projects
- **project** = everything else — skills from `.claude/skills/` within the current repo, or skills from plugins/extensions (names containing `:` like `superpowers:*`, `feature-dev:*`, `figma:*`, `claude-mem:*`, `skill-creator:*`, `engineering-skills:*`), or built-in harness skills (`update-config`, `keybindings-help`, `simplify`, `loop`, `claude-api`)

Omit a scope line entirely if no skills from that scope are active.

### How to Determine Scope — Dynamic Resolution

Do NOT rely on a hardcoded list. Instead, determine scope at runtime:

1. **User-level**: Any skill whose SKILL.md lives under `~/.claude/skills/`. **If a skill name matches a directory in `~/.claude/skills/`, it's user-level.**

2. **Project-level**: Any skill whose SKILL.md lives under the repo's `.claude/skills/`, plus any plugin/extension skill (identifiable by the `:` in its name, e.g. `superpowers:brainstorming`), plus built-in harness skills.

3. **When uncertain**: If you haven't seen the skill before and can't determine its origin, list it under project.

### What Counts as "Using a Skill"

A skill is active if:

- You invoked it via the Skill tool in this response
- You are following its instructions to shape your behavior (e.g., `always-english` affecting language, `no-coauthor` affecting commits, `confirm-understanding` causing you to restate before acting)
- It was triggered by the context of the user's request (e.g., `nestjs-expert` while working on NestJS code)

### Rules

1. **Every response gets the header** — no exceptions, even for short answers
2. **List ALL skills influencing the response** — don't miss passive skills like `always-english` or `no-coauthor`
3. **Be honest** — if a skill is loaded but not actually influencing this particular response, don't list it
4. **Keep it concise** — skill names grouped by scope, no descriptions needed
5. **Place it first** — the skills header comes before any other content

### Examples

**Writing NestJS code while responding in English to a Portuguese message:**
```
**Skills (user):** show-active-skills, always-english, confirm-understanding
**Skills (project):** nestjs-expert
```

**Making a git commit:**
```
**Skills (user):** show-active-skills, always-english, no-coauthor
```

**Simple question, no other skills relevant:**
```
**Skills (user):** show-active-skills
```

**Listing skills:**
```
**Skills (user):** show-active-skills, list-skills
```

**Creating a skill via plugin:**
```
**Skills (user):** show-active-skills, always-english
**Skills (project):** skill-creator:skill-creator
```

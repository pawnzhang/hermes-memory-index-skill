# hermes-memory-index-skill

A [Hermes Agent](https://hermes-agent.nousresearch.com) skill for efficient memory management.

## Purpose
When an agent's memory store approaches capacity, this skill provides a systematic method to:
1. **Audit** — identify memory entries that consume disproportionate space
2. **Externalize** — move bulky content to `~/.hermes/conventions/*.md` files
3. **Index** — replace memory entries with compact index pointers
4. **Preserve** — keep core concepts (philosophy, user profile, behavior rules) in memory

## Usage
Trigger: Memory usage > 80% or user requests memory optimization.

## How It Works
- Memory acts as an **index layer**; filesystem stores **content**
- Index format: `Name → ~/.hermes/conventions/<name>.md`
- Closed-loop: updating content must keep index valid
- Always backup before any operation

## Example
**Before:** `【Git 管理规范】所有代码改动必须走 git 流程...` (~260 chars)
**After:** `Git 规范 → ~/.hermes/conventions/git-rules.md` (~44 chars)
**Space saved:** ~216 chars per entry.

## Installation
```bash
cp skill.json ~/.hermes/skills/memory-index/
cp SKILL.md ~/.hermes/skills/memory-index/
```

## Author
Created by Davis (pawnzhang) for the Hermes Agent community.

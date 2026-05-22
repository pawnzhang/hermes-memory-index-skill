---
name: memory-index
description: Memory indexing: externalize bulky memory entries to convention files, keep only index pointers with search keywords
category: memory
trigger: memory-usage-above-80-percent, user-request-memory-audit
---

# Memory Index Skill

## Trigger Conditions
- Memory usage > 80% or user requests memory audit
- New memory entry would exceed the character limit

## Core Principle
Memory stores only **index pointers with keywords** (e.g., `Git Rules (commit, 原子提交) → ~/.hermes/conventions/git-rules.md`).
Full content lives in `~/.hermes/conventions/*.md` files.
Memory = index layer; Filesystem = content layer.

## Critical Rule: Keywords Are Mandatory
Every index pointer MUST include search keywords in parentheses.
Without keywords, the index becomes a dead link — the agent can never find the file by search.
Format: `Name (keyword1, keyword2, keyword3) → /path/to/file.md`

## Execution Steps
1. **Backup** — `cp memory.md memory.md.backup.TIMESTAMP`
2. **Audit** — identify bulky entries suitable for externalization
3. **Externalize** — write full content to `~/.hermes/conventions/<name>.md`
4. **Replace** — update memory entry to `Name (keyword1, keyword2) → /path/to/file.md`
5. **Verify** — confirm space freed and keyword search resolves correctly

## What to Keep in Memory (Do NOT externalize)
- Core philosophy/identity definitions (needed every turn)
- Behavioral principles (SOUL.md first principles)
- User identity/preferences (critical facts for every session)
- Active project state (e.g., novel chapter progress)

## Anti-Patterns
- ❌ Externalizing everything (core concepts must stay in memory)
- ❌ Index pointers WITHOUT keywords (search can't find them → content unreachable)
- ❌ Index and file content out of sync (content becomes unreachable)
- ❌ Operating without backup (irreversible damage)

## Closed-Loop Constraint
When updating a conventions file, verify the memory index pointer and its keywords are still valid.
When searching, check memory index first by keyword, then load the referenced file.

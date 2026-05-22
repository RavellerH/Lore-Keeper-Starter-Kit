# GEMINI.md — [YOUR WORLD] Story Vault

This workspace is an Obsidian-based knowledge vault for the **[YOUR WORLD]** series.

## Project Overview
- **IP Name:** [YOUR WORLD]
- **Primary Setting:** [Continent/Region name]
- **Core Works:** [List books]
- **Technical Components:**
  - **Lore Navigator:** A single-file HTML interactive encyclopedia.
  - **Agent System:** Specialized sub-agent configurations and a cross-session memory system.

## Vault Structure

| Directory | Purpose |
| :--- | :--- |
| `Lore/` | Authoritative world-building (Factions, Magic, Timeline, Geography). |
| `Book 1/` | Planning, character designs, and drafts for Book 1. |
| `Lore Navigator/` | Source for the `index.html` interactive tool. |
| `Gemini/` | **Gemini's Engineering Hub** (Technical planning and roadmaps). |
| `_meta/` | Session logs, key decisions, and open questions (Memory System). |
| `memory/` | Claude's persistent memory files. |

## Collaboration Protocol — Claude (Lead) + Gemini (Support)

### Division of ownership — HARD RULES

| File / Directory | Owner | Gemini may edit? |
|-----------------|-------|-----------------|
| `Lore/*.md` | **Claude only** | **NO** |
| `Book 1/*.md` | **Claude only** | **NO** |
| `_meta/*.md` | **Claude only** | **NO** |
| `memory/*.md` | **Claude only** | **NO** |
| `CLAUDE.md` | **Claude only** | **NO** |
| `Lore Navigator/index.html` | **Gemini** | YES — Gemini's primary responsibility |
| `Gemini/` | **Gemini** | YES — your primary workspace |
| `GEMINI.md` | Gemini | YES — your own file |

**Lore is Claude's responsibility. index.html is Gemini's responsibility. These do not cross.**

### Gemini Memory (Parallel Layer)
- [`Gemini/MEMORY/INDEX.md`](Gemini/MEMORY/INDEX.md) — Gemini's context router
- [`Gemini/MEMORY/session_log.md`](Gemini/MEMORY/session_log.md) — Gemini's session tracking

**Sync bridge:** [`_meta/HANDOFF.md`](_meta/HANDOFF.md) — write your section at session end when lore or game state changed.

**At every Gemini session start:**
1. Load `GEMINI.md` + `_meta/HANDOFF.md`
2. Declare mode: GAME_DEV or LORE_SYNC
3. Load mode list from `Gemini/MEMORY/INDEX.md`
4. Check HANDOFF.md pending items

**At every Gemini session end:**
1. Write entry to `Gemini/MEMORY/session_log.md`
2. Update `_meta/HANDOFF.md` → Gemini→Claude section if cross-agent items exist

## Technical Guidance

### Lore Navigator (`Lore Navigator/index.html`)
- **Architecture:** Single-file HTML/JS/CSS.
- **Data objects:** `TIMELINE_DATA`, `LORE`, `SEARCH_INDEX` — all in the `<script>` block.
- **To add a new lore page:** Add a new key to the `LORE` object, add entries to `SEARCH_INDEX`, add a tile to `LORE.home.render()`.
- **State:** Uses `localStorage` to track progress and achievements.

### If in doubt on a story or lore decision
Do not decide. Do not edit. Flag it and wait for Claude or the author.

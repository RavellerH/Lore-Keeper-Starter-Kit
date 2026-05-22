# Story Starter Kit

A portable foundation for building a new story vault with AI assistance.

## What's Included

| Folder/File | Purpose |
|-------------|---------|
| `CLAUDE.md` | Claude Code project instructions — edit with your world name |
| `GEMINI.md` | Gemini CLI project instructions |
| `.claude/rules/` | Session protocol, file update rules, canon rules |
| `_meta/` | Session log, decisions, open questions, entity index |
| `memory/` | Claude's persistent memory files |
| `Lore/` | World-building templates (characters, factions, magic, etc.) |
| `Book 1/` | Writing plan template for your first book |
| `Gemini/MEMORY/` | Gemini's parallel memory system |
| `Lore Navigator/` | Interactive lore encyclopedia (HTML/JS/CSS — blank template) |

## Setup on a New Device

1. Clone this repo
2. Open Claude Code in this folder
3. Edit `CLAUDE.md` — replace `[YOUR WORLD]` with your world name
4. Edit `.claude/rules/canon.md` — add your absolute rules
5. Edit `_meta/CONTEXT_ROUTER.md` — adjust modes for your project
6. Start a session: Claude will ask which mode you're working in

## AI Tool Setup

### Claude Code (primary)
- `CLAUDE.md` is auto-loaded by Claude Code
- Memory files in `memory/` persist across sessions
- Rules in `.claude/rules/` are auto-loaded via `CLAUDE.md` @-references

### Gemini CLI
- `GEMINI.md` is Gemini's context file
- Gemini owns `Lore Navigator/index.html` and `Gemini/`
- Claude owns all `Lore/*.md`, `_meta/`, and `memory/` files

### Aider
- Respects `.gitignore` — PDFs, binaries, and OS noise are excluded
- Run from the vault root: `aider --model claude-sonnet-4-6`

### Codex
- Works from the vault root
- Follow `CLAUDE.md` context — Codex reads the same project instructions

## Work Modes

| Mode | Use when |
|------|---------|
| `PROSE_WRITING` | Drafting or editing chapter text |
| `LORE_BUILDING` | World decisions, factions, magic, geography |
| `GAME_NAVIGATOR` | HTML/JS work on the Lore Navigator |
| `AUDIT_QA` | Canon checks, contradiction hunting |

## Lore Navigator

`Lore Navigator/index.html` is a standalone HTML app — open it in any browser.
To add content: edit the `LORE` object and `TIMELINE_DATA` in the file.
Gemini is responsible for keeping it in sync with `Lore/*.md` files.

## Session Flow

**Start:** Claude reads `_meta/session-log.md` (last entry) + blocking questions, declares mode.  
**During:** New entities → `_meta/entity-index.md`. Decisions → `_meta/decisions.md`.  
**End:** Claude writes session log entry, updates open questions. "Memory written. Session closed."

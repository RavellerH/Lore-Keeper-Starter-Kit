# Agent Instructions — [YOUR WORLD] Vault

*Context file for Codex and other code-generation agents.*

## Project Context
This is a creative writing vault for the **[YOUR WORLD]** series.
Primary language: Markdown (lore files) + HTML/JS/CSS (Lore Navigator).

## File Ownership Rules
| Files | Owner | Others may edit? |
|-------|-------|-----------------|
| `Lore/*.md`, `_meta/*.md`, `memory/*.md` | Claude | No |
| `Lore Navigator/index.html` | Gemini | Yes, with care |
| `Book 1/*.md` | Claude | No |

## What Codex Should Focus On
- Lore Navigator (`Lore Navigator/index.html`) — HTML/JS/CSS only
- Any new mini-game HTML files
- Data parsing or formatting scripts

## What Codex Should NOT Touch
- `Lore/*.md` — lore files are Claude's domain
- `_meta/*.md` — session tracking files
- `memory/*.md` — Claude's memory files
- `CLAUDE.md` — project instructions

## Coding Conventions
- Lore Navigator is a single-file HTML app — keep it that way
- Use `localStorage` for any persistent state
- Dark fantasy aesthetic: CSS variables defined in `:root` at top of file
- Add new lore pages by extending the `LORE` object and `SEARCH_INDEX`

## Session Protocol
Read `_meta/HANDOFF.md` before any Lore Navigator work to see what's pending.

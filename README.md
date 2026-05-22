# Lore Keeper Starter Kit

A portable, multi-AI story vault you can clone on any device and start writing immediately. Built for novelists who use Claude Code, Gemini CLI, Aider, and Codex together.

Clone it. Fill in your world name. Start building.

---

## What's Inside

```
Lore-Keeper-Starter-Kit/
├── CLAUDE.md                    ← Claude project instructions
├── GEMINI.md                    ← Gemini CLI instructions
├── AGENTS.md                    ← Codex instructions
├── .claude/
│   └── rules/
│       ├── canon.md             ← Your absolute world rules (never violate)
│       ├── session.md           ← Session start/end protocol
│       └── files.md             ← File update rules
├── _meta/
│   ├── CONTEXT_ROUTER.md        ← Mode-based file routing (4 modes)
│   ├── HANDOFF.md               ← Claude ↔ Gemini sync bridge
│   ├── session-log.md           ← Session history
│   ├── decisions.md             ← Lore decision log with anchors
│   ├── open-questions.md        ← Blocking / open / resolved questions
│   └── entity-index.md          ← All named characters, places, objects
├── memory/
│   ├── MEMORY.md                ← Memory index
│   ├── project_core.md          ← World facts baseline
│   ├── feedback_collab.md       ← How to work on this vault
│   └── user_profile.md          ← Author profile
├── Lore/
│   ├── CHARACTERS.md
│   ├── FACTIONS.md
│   ├── MAGIC_SYSTEM.md
│   ├── TIMELINE.md
│   ├── WORLD_GEOGRAPHY.md
│   └── LORE_QUICK_REFERENCE.md  ← Read this before every session
├── Book 1/
│   └── Writing_Plan.md          ← Beat sheet + chapter tracker
├── Gemini/MEMORY/               ← Gemini's parallel memory
└── Lore Navigator/
    └── index.html               ← Interactive lore app (open in browser)
```

---

## Quick Start

```bash
git clone https://github.com/RavellerH/Lore-Keeper-Starter-Kit.git my-story
cd my-story
```

Open the folder in Claude Code, then fill in these four files:

| File | What to fill in |
|------|----------------|
| `CLAUDE.md` | Replace `[YOUR WORLD]` and `[YOUR SERIES NAME]` |
| `memory/project_core.md` | World facts, factions, magic system |
| `.claude/rules/canon.md` | Your absolute rules — facts that never change |
| `Lore/LORE_QUICK_REFERENCE.md` | Most important facts for quick reference |

---

## Work Modes

Declare your mode at the start of every session. Claude loads only the files that mode needs.

| Mode | Use when |
|------|---------|
| `PROSE_WRITING` | Drafting or editing chapter text |
| `LORE_BUILDING` | World decisions, factions, magic, geography, culture |
| `GAME_NAVIGATOR` | HTML/JS work on the Lore Navigator |
| `AUDIT_QA` | Canon checks, contradiction hunting, consistency passes |

---

## AI Tools

### Claude Code
- `CLAUDE.md` is loaded automatically
- `.claude/rules/` files are loaded via `@` references in `CLAUDE.md`
- `memory/` files persist across sessions — Claude builds up world knowledge over time
- Session protocol: start → read last log entry + blocking questions → declare mode → work → write log

### Gemini CLI
- `GEMINI.md` is Gemini's context file
- Gemini owns `Lore Navigator/index.html` — keeps it in sync with lore decisions from Claude
- `_meta/HANDOFF.md` is the sync bridge between the two agents

### Aider
- Run from vault root: `aider --model claude-sonnet-4-6`
- `.gitignore` excludes PDFs, large binaries, and OS noise

### Codex
- Works from vault root
- Reads `AGENTS.md` for project context and ownership rules

---

## Lore Navigator

`Lore Navigator/index.html` is a standalone interactive lore encyclopedia. Open it in any browser — no server needed.

**Features:** Dark/light theme · Search · Page-flip reader · localStorage progress · Achievement tracking

**To add content:**
1. Add a new key to the `LORE` object in `index.html`
2. Add a tile for it in `LORE.home.render()`
3. Add keywords to `SEARCH_INDEX`

Gemini is responsible for keeping the Navigator in sync with `Lore/*.md` changes. Claude writes the lore; Gemini reflects it in the app.

---

## Session Flow

**Session start**
1. Claude reads `_meta/session-log.md` (last entry only)
2. Claude reads `_meta/open-questions.md` (blocking items only)
3. Declare mode — Claude loads the matching file list from `_meta/CONTEXT_ROUTER.md`
4. Claude says: *"Ready. Here's where we left off:"* + one-paragraph summary

**During the session**
- New named entity created → `_meta/entity-index.md`
- Lore decision made → `_meta/decisions.md`
- Contradiction found → flag ⚠️ CONFLICT, resolve before continuing
- Lore change needs Navigator sync → write `_meta/HANDOFF.md` → Gemini section

**Session end**
1. Write `_meta/session-log.md` entry
2. Update `_meta/open-questions.md`
3. If lore changed: update `_meta/HANDOFF.md`
4. Claude says: *"Memory written. Session closed."*

---

## File Ownership

| Files | Owner | Others may edit? |
|-------|-------|-----------------|
| `Lore/*.md`, `_meta/*.md`, `memory/*.md` | Claude | No |
| `Book 1/*.md` | Claude | No |
| `Lore Navigator/index.html` | Gemini | Yes |
| `Gemini/` | Gemini | Yes |
| `GEMINI.md` | Gemini | Yes |

---

## Based On

Built from the production workflow used in the **Kalmirth** dark fantasy series vault — battle-tested across multiple books, sessions, and AI agents.

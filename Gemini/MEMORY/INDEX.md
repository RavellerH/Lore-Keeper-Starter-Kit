# Gemini Memory Index — [YOUR WORLD]

*Gemini's context router. Load this at every Gemini session start after GEMINI.md + HANDOFF.md.*

---

## ALWAYS LOAD

| File | Why |
|------|-----|
| `GEMINI.md` | Project overview and collaboration rules |
| `_meta/HANDOFF.md` | Pending items from Claude, what Gemini last did |

---

## BY MODE

### MODE: GAME_DEV
*HTML/JS work on Lore Navigator or mini-games.*

**Load:**
- `Lore Navigator/index.html` — the app to edit
- `_meta/HANDOFF.md` — Claude's pending lore sync requests

**Skip:** All `Lore/*.md`, `_meta/decisions.md`, `memory/`.

---

### MODE: LORE_SYNC
*Syncing new lore decisions from Claude into index.html.*

**Load:**
- `_meta/HANDOFF.md` — what Claude updated and needs reflected in the Navigator
- Specific `Lore/` file mentioned in HANDOFF (one file only, on demand)

---

## Session Log
See [`session_log.md`](session_log.md) for Gemini's session history.

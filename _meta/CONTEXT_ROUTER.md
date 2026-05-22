# Context Router — [YOUR WORLD] Vault

*Declare your work mode → load only these files. Skip everything else until needed mid-session.*

---

## ALWAYS (every session, every mode)

| File | Why |
|------|-----|
| `memory/project_core.md` | World facts baseline — series, factions, magic system |
| `memory/feedback_collab.md` | Mistakes to avoid, file protocol |
| `Lore/LORE_QUICK_REFERENCE.md` | Most important facts — read before any lore session |

---

## MODE: PROSE_WRITING

*Drafting or editing chapter text. Character voice, beat continuity, scene logic.*

**Load:**
- `memory/project_characters.md` — voice notes, MBTI, personality (create this when ready)
- `memory/project_writing_progress.md` — current chapter status, what's next (create this when ready)
- `Book 1/Writing_Plan.md` — beat sheet and part structure
- Current chapter draft file

**Skip:** All `Lore/` files, `_meta/decisions.md`, audit files, game files.
**Load on demand only:** A specific lore fact when a scene requires it — grep `_meta/entity-index.md`.

---

## MODE: LORE_BUILDING

*World decisions, faction facts, magic rules, geography, culture, character history.*

**Load:**
- `_meta/decisions.md` — last 2 date-sections only (most recent canon)
- `_meta/entity-index.md` — entity registry for cross-reference

**Load on demand:** Specific `Lore/` files only when making a decision that touches that domain.
**Skip:** Character design, writing progress, git infra, game files.

---

## MODE: GAME_NAVIGATOR

*HTML/JS work on Lore Navigator. Gemini handoff. Tech sync.*

**Load:**
- `_meta/HANDOFF.md` — what Gemini last did / what Claude owes Gemini
- `Gemini/MEMORY/INDEX.md` — Gemini's context router

**Skip:** All `Lore/` files, character design, writing progress, audit files.
**Load on demand:** Specific lore entries when a scene requires a fact check.

---

## MODE: AUDIT_QA

*Canon checks, contradiction hunting, lore consistency passes.*

**Load:**
- `_meta/decisions.md` — full file (authoritative canon log)
- `_meta/entity-index.md` — entity registry for cross-referencing

**Skip:** Writing progress, character design, game files.
**Load on demand:** Specific `Lore/` files when running a targeted audit pass.

---

## Protocol

**At session start:**
1. Declare mode (user states it, or Claude asks)
2. Load ALWAYS files (3 files)
3. Load mode-specific list above
4. Scan `_meta/open-questions.md` for blocking items only

**Token budget target:** Session start context ≤ 5 files. Never load more than 8 before first user message.

# Session Protocol — [YOUR WORLD] Vault

## Session Start
Load in this order:
1. `_meta/session-log.md` — last entry only
2. `_meta/open-questions.md` — blocking items only (## BLOCKING section)
3. **Declare mode** — user states it, or ask: "What are we working on today? (PROSE_WRITING / LORE_BUILDING / GAME_NAVIGATOR / AUDIT_QA)"
4. Read `_meta/CONTEXT_ROUTER.md` → load ALWAYS files + that mode's file list only
5. If mode is GAME_NAVIGATOR or last session involved Gemini: also load `_meta/HANDOFF.md`

Say: "Ready. Here's where we left off:" + one-paragraph summary of last session + top blocking question.

**Token budget:** ≤ 5 files loaded before first user message. Never exceed 8 before any substantive work.

## Write-Back Triggers (fire immediately, mid-session)
| Trigger | Write to |
|---------|---------|
| New named entity created | `_meta/entity-index.md` |
| Lore decision made | `_meta/decisions.md` (with anchor `{#YYYY-MM-DD-slug}`) |
| Contradiction found | Flag ⚠️ CONFLICT, resolve before continuing |
| Lore change requires Navigator sync | `_meta/HANDOFF.md` → Claude→Gemini section |

## Session End Checklist
1. `_meta/session-log.md` — new entry using the template block
2. `_meta/open-questions.md` — remove resolved (mark `[RESOLVED YYYY-MM-DD]`), add new with next OQ-NN ID
3. If lore changed: update `_meta/HANDOFF.md` → Claude→Gemini section
4. Say: "Memory written. Session closed."

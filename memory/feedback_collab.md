---
name: feedback-collab
description: How to work on this vault — collaboration rules, mistakes to avoid, file update protocol
metadata:
  type: feedback
---

# Collaboration Rules & Feedback

## File Protocol
- Always Read a file before editing it — never assume current content.
- A lore change ripples: update CHARACTERS.md → TIMELINE.md → FACTIONS.md as needed.
- After any lore decision: update the source file AND write an entry in `_meta/decisions.md`.

**Why:** Stale edits cause inconsistencies that are hard to find later.
**How to apply:** Every edit session, read the target file first. Every lore decision, write it down.

## Lore Navigator Sync
- When updating any `.md` lore file, flag in `_meta/HANDOFF.md` what Gemini needs to sync in `index.html`.
- Gemini owns `index.html`. Claude owns all `.md` files. These do not cross.

**Why:** Two agents editing the same file causes conflicts.
**How to apply:** After any lore session, check if index.html needs updating and write the HANDOFF entry.

## Canon Discipline
- Do not invent canon — always check `_meta/decisions.md` before making a lore claim.
- If a contradiction is found: flag ⚠️ CONFLICT before continuing. Resolve it, then write the resolution.

**Why:** Unresolved contradictions compound. A small inconsistency now becomes a plot hole in Chapter 10.
**How to apply:** When uncertain about a fact, grep `_meta/entity-index.md` first, then `_meta/decisions.md`.

## Session Discipline
- Token budget: ≤ 5 files loaded before first user message. Never exceed 8 before any substantive work.
- Load mode-specific files only — do not load the entire lore folder at session start.

**Why:** Loading too many files wastes context and slows every response.
**How to apply:** Follow CONTEXT_ROUTER.md mode lists strictly.

<!-- Add project-specific feedback below as the story grows -->

---
title: "OG-018-Designmd — Design.md"
type: project-bootstrap
created: "2026-04-13"
---

# OG-018-Designmd — Design.md

> **Bootstrap order — read these in order before doing any work in this project:**
>
> 1. `~/.claude/CLAUDE.md` → `Open-Memory-Vault/system/identity/MASTER-PROMPT.md` — Phil's identity (auto-loaded via symlink in Claude Code; other tools should mirror this).
> 2. `~/AGENT.md` → `agent-config/AGENT.md` — global operating manual (work style, skills routing, secrets policy, layering rules in §2.10).
> 3. `Open-Memory-Vault/AGENTS.md` — vault operating contract (read **only** if you will write to the vault during this session).
> 4. `Open-Memory-Vault/projects/OG-018-Designmd/README.md` — durable project page (status, decisions, recent activity, vault-side context).
> 5. **This file** — project-specific overrides and live operational references (below).
>
> **The project's `AGENT.md` is a bootstrap manifest, not a knowledge dump.** It points at everything else. Durable knowledge lives in the vault project page. Do not duplicate.

---

## At a glance

- **Code**: `OG-018`
- **Name**: Design.md
- **Stakeholder**: Phil (self)
- **Status**: `active`
- **Priority**: `medium`
- **Revenue lane**: `3-oganiko`
- **Purpose** (one sentence): Define the scaffolding for Oganiko branding, aligned with the Oganiko brand guidelines — the central place to document requirements and provide clear guidelines for all applications that need on-brand output.
- **Last touched**: `2026-04-13`

---

## Where things live

| Resource | Location |
|---|---|
| **Code root** | this folder (`OG-projects/OG-018-Designmd/`) |
| **Project docs** | `./docs/` |
| **Vault project page** | `Open-Memory-Vault/projects/OG-018-Designmd/README.md` |
| **GitHub repo** | https://github.com/parrysan/OG-018-Designmd |
| **External systems** | Google Drive: `OGANIKO-DRIVE/OG-Brand/` (brand source PDFs, colour palettes, guidelines) |

---

## Live references

> **Operational facts that should never have to be re-discovered.** Deployed URLs, store handles, theme IDs, API endpoints, credentials *location* (never the credentials themselves — those live in the global `.env`, see global AGENT.md §2.5). Update this section whenever a fact changes — it is the canonical source.

- **Production URL**: none (documentation project)
- **Staging / preview URL**: none
- **Platform handle / project ID**: none
- **Other identifiers**: none
- **Credentials**: n/a
- **Brand source files**: `~/Library/CloudStorage/GoogleDrive-phil.parry@gmail.com/My Drive/OGANIKO-DRIVE/OG-Brand/`
- **Existing oganiko-branding skill**: `~/.claude/skills/oganiko-branding/` (CSS tokens, brand-tokens.md, styleguide)

---

## Tech stack (overrides global defaults)

> Only list what differs from the global defaults in `agent-config/AGENT.md` §2.7. If everything matches the global defaults, write "Inherits global defaults" and stop.

- TODO — determine stack once scope is finalised. This is primarily a documentation/specification project; code output will be design tokens, CSS, and guidelines in markdown.

---

## Project-specific rules

> Domain rules, naming conventions, "do not" lists. Anything an LLM working in this project must know that isn't true globally. If empty, write "None — global rules apply" and stop.

- All brand colour values must match the canonical palette (see brand-tokens.md). Never approximate.
- Typography is Helvetica Neue only (Arial fallback). No decorative, serif, or novelty fonts.
- Brand voice: authentic, nurturing, informative, warm. Never hype-driven or preachy.
- OGANIKO Green (#109200) must always be present as brand signature in any output.
- Products are "unaltered, not cooked or added to" — this language is a core brand claim.

---

## Skills

> List any project-specific skills in `./.claude/skills/`. If none, the project uses the global library at `agent-config/skills/`. Do not duplicate the global skills inventory here — see global AGENT.md §2.2.

- **Project-local skills**: none — uses global library
- **Most relevant global skills for this project**: `oganiko-branding`, `design-system-creator`, `canvas-design`, `nanobanana`

---

## Notes for the next session

> **Optional, ephemeral.** A 2–3 line free-form scratch pad of "where I left off" — not durable knowledge. Durable decisions belong in the vault project page. Wipe and rewrite freely.

Last action: Project scaffolded. Brand source materials gathered from Google Drive PDFs and existing oganiko-branding skill.
Next action: Audit existing oganiko-branding skill against source PDFs. Define the full DESIGN.md specification covering all application types (infographics, slides, web, labels, social).
Open question: Should the DESIGN.md live in this project or replace/extend the existing oganiko-branding skill's references?

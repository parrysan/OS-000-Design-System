---
title: "OS-000-Design-System — Design System"
type: project-bootstrap
created: "2026-04-13"
---

# OS-000-Design-System — Design System

> **Bootstrap order — read these in order before doing any work in this project:**
>
> 1. `~/.claude/CLAUDE.md` → `Open-Memory-Vault/system/identity/MASTER-PROMPT.md` — Phil's identity (auto-loaded via symlink in Claude Code; other tools should mirror this).
> 2. `~/AGENT.md` → `agent-config/AGENT.md` — global operating manual (work style, skills routing, secrets policy, layering rules in §2.10).
> 3. `Open-Memory-Vault/AGENTS.md` — vault operating contract (read **only** if you will write to the vault during this session).
> 4. `Open-Memory-Vault/projects/OS-000-Design-System/README.md` — durable project page (status, decisions, recent activity, vault-side context).
> 5. **This file** — project-specific overrides and live operational references (below).
>
> **The project's `CLAUDE.md` is a bootstrap manifest, not a knowledge dump.** It points at everything else. Durable knowledge lives in the vault project page. Do not duplicate.

---

## At a glance

- **Code**: `OS-000`
- **Name**: Design System
- **Stakeholder**: Phil (OG AI OS)
- **Status**: `active`
- **Priority**: `high`
- **Type**: OS infrastructure (continuous lifecycle)
- **Purpose** (one sentence): The foundational design system for all OG output — central documentation and guidelines for all applications that need on-brand output.
- **Last touched**: `2026-04-13`

---

## Where things live

| Resource | Location |
|---|---|
| **Code root** | this folder (`dev/OS-000-Design-System/`) |
| **Project docs** | `./docs/` |
| **Vault project page** | `Open-Memory-Vault/projects/OS-000-Design-System/README.md` |
| **GitHub repo** | https://github.com/parrysan/OS-000-Design-System |
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

## Tech stack

This IS the global default stack. OS-000 is the foundation that all Lane 1-3 projects consume.

- **Tokens**: CSS custom properties via Tailwind v4 `@theme` — `tokens/base.css` (brand-agnostic) + `tokens/theme-*.css` (brand-specific)
- **Components**: React/JSX — `components/` directory, exported via `components/index.js`
- **Viewer**: `/design-system` page template — `viewer/DesignSystemPage.jsx`
- **Themes available**: `theme-oganiko.css` (OGANIKO brand), `theme-neutral.css` (clean slate for clients)
- **Consumption**: Projects import tokens via CSS `@import`, copy components into their own `src/`, override theme values per project

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

Last action: Built v1 foundation — base tokens (base.css), two themes (oganiko + neutral), 6 components (Button, Card, Hero, Nav, Footer, Section), and the /design-system viewer page.
Next action: First consumer — integrate OS-000 into OG-017-Magdas-Website as proof of concept. Then promote learnings back.
Open question: Should oganiko-branding skill point at OS-000 tokens as its source of truth, or remain independent?

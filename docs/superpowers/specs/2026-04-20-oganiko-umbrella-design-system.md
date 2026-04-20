# OGANIKO Umbrella Design System — Spec

**Date**: 2026-04-20
**Status**: Draft (pending user review)
**Project**: OS-000-Design-System
**Author**: Phil Parry (via Snoop / Claude Code brainstorming)

---

## 1. Purpose

Reframe OGANIKO from a healthy-food sub-brand into Phil Parry's **umbrella brand for everything he ships** — food retail (`oganiko.shop`), digital products, service work, and personal brand. Make the resulting design system readable by `claude.ai/design` (Anthropic's design system tool) so generated artifacts automatically respect OGANIKO identity.

## 2. Problem

Brand knowledge is currently scattered across four places:

1. `OS-000-Design-System` repo — tokens, components, catalogue.
2. `~/.claude/skills/oganiko-branding/` — SKILL.md, references, CSS tokens.
3. `~/.claude/skills/brand-guidelines/` — **duplicate** of (2); same trigger words.
4. Google Drive `OG-Brand/` — source PDFs, logos, master reference doc.

All of this is framed as "healthy food / live long" — too narrow for the new umbrella scope. Typography relies on Helvetica Neue, which is commercially licensed and blocks public-repo use.

## 3. Decisions

### 3.1 Brand scope

**OGANIKO is the umbrella brand.** No more "eat healthy / live long" framing. Covers:
- Food retail (`oganiko.shop`) — unchanged
- Digital products (Lane 2: POD, AI)
- Service work (Lane 1: client websites and Shopify)
- Personal brand ("Phil v2")

Colour palette and visual identity **unchanged**. Only voice, copy, and positioning shift.

### 3.2 Repo architecture

**`OS-000-Design-System` is the single canonical source of truth** for OGANIKO brand + design system.

- Multi-theme: `theme-oganiko.css` (flagship) + `theme-neutral.css` (client work that isn't OGANIKO-branded, e.g. BDSynbio, Tartak).
- Skills and `claude.ai/design` point at this repo. Google Drive remains the archive for high-res source material (PDFs, master reference doc).

### 3.3 Typography

**Primary typeface: Open Sans (Google Fonts, SIL Open Font License 1.1).**

Replaces Helvetica Neue across the board.

- **Weights shipped**: 400 Regular, 600 SemiBold, 700 Bold. Add 500 Medium only if a subhead weight is needed. No italics unless an editorial use case appears.
- **Delivery**: both — Google Fonts CDN `<link>` for websites, plus self-hosted `.woff2` files in `brand/typography/` for offline/static artifacts.
- **Fallback stack**: `"Open Sans", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif`

Rationale: free, web-licensed, public-repo safe, no procurement friction. Humanist sans-serif close in feel to Helvetica Neue — minimal visual change.

### 3.4 Skill rename and reshape

- `~/.claude/skills/oganiko-branding/` → renamed to `~/.claude/skills/design-branding-oganiko/`.
- Establishes naming convention `design-branding-<brand>` for future per-brand skills (MabV, BDSynbio, etc.).
- Reshaped into a **thin pointer skill**:
  - `SKILL.md` — 1-paragraph brand statement + quick-reference table (colours, type, voice) + pointer to OS-000 repo for anything deeper.
  - `references/quick-reference.md` — cheat sheet.
  - `assets/oganiko-tokens.css` — **symlink** to `OS-000-Design-System/tokens/theme-oganiko.css`. Zero drift by construction.
- `~/.claude/skills/brand-guidelines/` — **deleted**. Duplicate of the above.

## 4. Repo Changes

### 4.1 New folder: `brand/`

```
brand/
├── README.md            # Canonical brand one-pager (umbrella framing, palette, type, voice)
├── logo/
│   ├── oganiko-primary.svg
│   ├── oganiko-reversed.svg
│   ├── oganiko-monochrome.svg
│   └── favicon.svg
├── colour/
│   ├── palette.svg      # Visual swatch card
│   └── palette.json     # Machine-readable (hex + token name)
├── typography/
│   ├── OpenSans-Regular.woff2
│   ├── OpenSans-SemiBold.woff2
│   ├── OpenSans-Bold.woff2
│   ├── type-scale.svg   # Visual reference
│   └── README.md        # Google Fonts link + @font-face self-hosted snippet
└── imagery/             # 2-3 representative on-brand photos (optional)
```

Assets curated from Google Drive `OG-Brand/` (logos, colour references). Google Drive remains the archive for source PDFs; repo carries derived/optimised assets only.

### 4.2 Token updates

- `tokens/theme-oganiko.css`:
  - Update header comment to umbrella-brand framing.
  - Change `--font-family-primary` from Helvetica Neue stack to Open Sans stack.
- `tokens/base.css`:
  - Update fallback stack to Open Sans family.
- Colour custom properties: **no changes** (OGANIKO Green #109200 etc. remain identical).

### 4.3 Documentation updates

- **Root `README.md`**: add positioning paragraph — "OGANIKO is the flagship brand; neutral theme exists for client work."
- **`CLAUDE.md`** (project): rewrite the "project-specific rules" section — remove Helvetica Neue rule, add Open Sans rule, remove food-specific brand claims ("unaltered, not cooked or added to"), keep OGANIKO Green as signature rule.
- Scan tokens, catalogue entries, viewer copy, and existing READMEs for food-specific language ("eat healthy," "live long," product-specific claims) and remove or neutralise.

### 4.4 Global rule updates (outside the repo)

- `~/OG/config/rules/` — any file referencing Helvetica Neue updates to Open Sans.
- `~/.claude/CLAUDE.md` — no direct typography mention; no change needed.

## 5. Skill Layer Changes

### 5.1 Rename and reshape

1. `git mv ~/.claude/skills/oganiko-branding ~/.claude/skills/design-branding-oganiko`
2. Rewrite `SKILL.md`:
   - Trigger on umbrella brand framing ("OGANIKO", "OGANIKO branding", "OG brand", and any `.shop`/`.digital` sub-brand).
   - Brief positioning paragraph (umbrella).
   - Quick-reference table (palette + Open Sans).
   - Explicit pointer: "Canonical source is `/Users/oganiko/OG/dev/OS-000-Design-System/`. Read `brand/README.md` and `tokens/theme-oganiko.css` for full specification."
3. Replace `assets/oganiko-tokens.css` with a symlink to the repo's `tokens/theme-oganiko.css`.
4. Update `references/brand-tokens.md` → rename to `references/quick-reference.md`, trim to cheat-sheet size.

### 5.2 Deletion

Remove `~/.claude/skills/brand-guidelines/` entirely.

### 5.3 Naming convention

Document in `~/AGENT.md` (or equivalent global agent config): per-brand skills follow the pattern `design-branding-<brand>`. Future: `design-branding-mabv`, `design-branding-bdsynbio`, etc.

## 6. `claude.ai/design` Inputs

Once repo changes are pushed, feed the tool:

### 6.1 Company blurb
> **OGANIKO** — the umbrella brand for everything Phil Parry ships: food retail (`oganiko.shop`), digital products, service work, and personal brand. Core identity is natural, premium, clean, and direct. Colour signature is OGANIKO Green (#109200). Typography is Open Sans (Google Fonts). Voice is warm, informative, factual — never hype. The repo contains flagship OGANIKO tokens plus a neutral theme for client work.

### 6.2 GitHub URL
`https://github.com/parrysan/OS-000-Design-System`

### 6.3 Fonts, logos, assets upload
Drag contents of `brand/`:
- `logo/` — all SVGs
- `typography/` — Open Sans `.woff2` files
- `colour/palette.svg` — visual palette card
- Optionally 2–3 images from `imagery/`

### 6.4 `.fig` file
Skip. No Figma source exists.

## 7. Order of Operations

1. Push the pending local commit + this spec to GitHub. (Done as part of writing this spec.)
2. Execute repo reframe (token updates, `brand/` folder, docs, global rule updates).
3. Execute skill rename + reshape; delete `brand-guidelines`.
4. Commit and push.
5. Open `claude.ai/design`, paste blurb, point at GitHub URL, upload curated `brand/` assets.

## 8. Scope Boundaries

**Out of scope for this round:**
- No new components (Header/Tabs/Footer/Button/Card/Hero/Nav/Section remain as-is).
- No catalogue rework or OS→ODS rename.
- No Figma file creation.
- No website deploy (OS-000 remains documentation-only).
- No token-value changes (colours, spacing, radii all unchanged).
- No Tailwind v4 `@theme` plumbing changes.
- No additional brand themes yet (`theme-mabv.css` etc. come when earned).
- No visual regression tests or CI.
- No vault memory writes during implementation — use `/capture` for decisions after the fact.

**Deferred, flagged explicitly:**
- Full shell layout for catalogue (header + left sidebar) — captured in `CLAUDE.md` notes.
- OS → ODS rename across catalogue files — captured in `CLAUDE.md` notes.

## 9. Open Questions / Risks

- **Google Drive asset curation**: the spec assumes logo SVGs are available in `OG-Brand/03_OG Brand Logo/`. If they're only in PDF or raster form, a one-off vectorisation or export step is needed before the `brand/logo/` folder can be populated. To be checked during implementation.
- **`docs/os000-architecture.excalidraw`** is currently untracked. Decide during implementation whether to commit it (useful architectural reference) or leave it local. Not blocking.

## 10. Success Criteria

- OS-000-Design-System repo on GitHub reflects umbrella-brand framing, Open Sans typography, and a populated `brand/` folder.
- Running any OGANIKO-related task via Claude Code loads `design-branding-oganiko` skill; no duplicate `brand-guidelines` skill loads.
- Typing "OGANIKO" into `claude.ai/design` + pointing at the repo + uploading curated assets produces generated artifacts that use OGANIKO Green, Open Sans, and umbrella-brand voice.
- No residual "healthy food / live long" copy survives in repo, skill, or project `CLAUDE.md`.

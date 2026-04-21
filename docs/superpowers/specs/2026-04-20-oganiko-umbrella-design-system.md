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

**OGANIKO is the umbrella brand.** No more "eat healthy / live long" framing. Scope, **ranked by priority**:

1. **Digital products (flagship)** — POD, AI tools, SaaS, marketplace work, **plus all service work** (client websites, Shopify builds). Most service work is digital-product delivery for clients, so it folds cleanly under this banner rather than sitting as a separate rank.
2. **Personal brand (Phil v2)** — LinkedIn, portfolio, public narrative. Lives in `OG-019-Phil-v2`.
3. **Oganiko Shop (distant third)** — food retail at `oganiko.shop`. Retained but de-scoped from flagship.

Colour palette and visual identity **unchanged**. Only voice, copy, positioning, and relative emphasis shift.

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

### 3.5 Tagline

**"Less is more by design."**

Five-word tagline for the umbrella brand. Non-food, design-forward. Blends Phil's own mantra (*"less is more"*) with a nod to his 25-year design-systems discipline (*"by design"*). Reads as both "minimalist by intention" and "less — achieved through design as a practice."

**Where it appears:**
- `brand/README.md` immediately under the OGANIKO name
- claude.ai/design blurb (§6.1)
- Any bio / about copy in OG-019-Phil-v2
- Email signature and similar short-form contexts

**Where it does NOT appear:** on every artifact. Tagline is for brand-one-pager contexts — not a watermark on every output.

### 3.6 ODS — Oganiko Design System

`ODS` is the internal shorthand for the design system, and a deliberate callback to Phil's 17 years as lead designer of the **Orange Design System** (also ODS) — the design system he built at Orange / France Telecom before the term "design system" was in widespread use.

**Where it appears:**
- `brand/README.md` in a short "Heritage" paragraph (three to four sentences naming the Orange continuity explicitly).
- Token file header comments, skill docs, internal CLAUDE.md files — used casually alongside "OGANIKO".
- OG-019-Phil-v2 bio / about copy — one sentence positioning the continuity without over-explaining.

**Where it does NOT appear:** public-facing taglines, product pages, marketing copy. The callback is credibility infrastructure for the design-literate — not a public positioning move. Readers who recognise the Orange Design System will see the wink; everyone else reads `ODS` as a clean internal acronym.

## 4. Repo Changes

### 4.1 New folder: `brand/`

```
brand/
├── README.md            # Canonical brand one-pager (umbrella framing, tagline, ODS heritage, palette, type, voice)
├── logo/
│   ├── oganiko-primary.svg       # from OG-Brand/03_OG Brand Logo/OG Logo Master Files/OGL-Master.svg
│   ├── oganiko-reversed.svg      # from OGL-Master-SVG-onBlack.svg
│   ├── oganiko-monochrome.svg
│   └── favicon.svg               # leaf-only, derived from the master logo
├── colour/
│   ├── palette.svg      # Visual swatch card
│   └── palette.json     # Machine-readable (hex + token name)
└── typography/
    ├── OpenSans-Regular.woff2
    ├── OpenSans-SemiBold.woff2
    ├── OpenSans-Bold.woff2
    ├── type-scale.svg   # Visual reference
    └── README.md        # Google Fonts link + @font-face self-hosted snippet
```

Assets curated from Google Drive `OG-Brand/` (logos, colour references). Google Drive remains the archive for source PDFs; repo carries derived/optimised assets only.

**No `imagery/` folder.** De-scoped — brand photography is not part of the current OGANIKO umbrella identity. Can be revisited later if needed; not part of this round.

### 4.2 Token updates

- `tokens/theme-oganiko.css`:
  - Update header comment to umbrella-brand framing.
  - Change `--font-family-primary` from Helvetica Neue stack to Open Sans stack.
- `tokens/base.css`:
  - Update fallback stack to Open Sans family.
- Colour custom properties: **no changes** (OGANIKO Green #109200 etc. remain identical).

### 4.3 Documentation updates

- **Root `README.md`**: add positioning paragraph — "OGANIKO is the flagship brand; neutral theme exists for client work."
- **`CLAUDE.md`** (project): rewrite the "project-specific rules" section — remove Helvetica Neue rule, add Open Sans rule, remove the food-specific brand claim (*"unaltered, not cooked or added to"*) since it doesn't fit at umbrella level, keep OGANIKO Green as signature rule, add the tagline reference, add the ODS shorthand note.
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
> **OGANIKO** — the umbrella brand for everything Phil Parry ships. Flagship output is **digital products** (tools, SaaS, client websites, marketplace work), followed by Phil's **personal brand**, with **Oganiko Shop** (food retail at `oganiko.shop`) as a distant third. Core identity: natural, premium, clean, direct. Colour signature: OGANIKO Green (#109200). Typography: Open Sans (Google Fonts). Voice: warm, informative, factual — no hype. Tagline: *"Less is more by design."* Internally known as **ODS** (Oganiko Design System) — a deliberate callback to Phil's 17 years as lead designer of the Orange Design System. The repo contains flagship OGANIKO tokens plus a neutral theme for client work that isn't OGANIKO-branded.

### 6.2 GitHub URL
`https://github.com/parrysan/OS-000-Design-System`

### 6.3 Fonts, logos, assets upload
Drag contents of `brand/`:
- `logo/` — all SVGs (primary, reversed, monochrome, favicon)
- `typography/` — Open Sans `.woff2` files
- `colour/palette.svg` — visual palette card

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

- **Favicon derivation from OGL-Master.svg** *(was: logo availability — now resolved)*: The master logo SVG is confirmed at `OG-Brand/03_OG Brand Logo/OG Logo Master Files/OGL-Master.svg` (34 KB, viewBox `0 0 1251 291`, contains leaf + wordmark). A leaf-only favicon must be derived from it. Three options for the implementation plan:
  - (a) Manual SVG surgery — isolate the leaf paths and set a square viewBox.
  - (b) Affinity Designer export — Phil holds the `.afdesign` source and can export the leaf layer directly for pixel-perfect control.
  - (c) Programmatic crop — adjust viewBox to the leaf's bounding box in the existing SVG.
  - Decide during implementation; Phil-hands-on (b) is cleanest, (a) or (c) works if scripting is preferred.
- **`docs/os000-architecture.excalidraw`** is currently untracked. Decide during implementation whether to commit it (useful architectural reference) or leave it local. Not blocking.

## 10. Success Criteria

- OS-000-Design-System repo on GitHub reflects umbrella-brand framing (with **priority-ordered scope**: digital products → personal brand → oganiko shop), Open Sans typography, the tagline *"Less is more by design."*, the ODS heritage paragraph, and a populated `brand/` folder with `logo/`, `colour/`, and `typography/` (no `imagery/`).
- Running any OGANIKO-related task via Claude Code loads `design-branding-oganiko` skill; no duplicate `brand-guidelines` skill loads.
- Typing "OGANIKO" into `claude.ai/design` + pointing at the repo + uploading curated assets produces generated artifacts that use OGANIKO Green, Open Sans, the umbrella-brand voice, and surface the tagline in appropriate contexts.
- No residual "healthy food / live long" copy survives in repo, skill, or project `CLAUDE.md`. The food-specific product claim (*"unaltered, not cooked or added to"*) is removed from umbrella-level rules.
- `brand/logo/favicon.svg` exists as a leaf-only mark derived from `OGL-Master.svg`, ready to ship as a browser favicon without further editing.

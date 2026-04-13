# How to consume OS-000 in a project

## 1. Import tokens in your project's main CSS

```css
/* app/globals.css or src/styles/main.css */
@import "tailwindcss";

/* OS-000 foundation */
@import "../../OS-000-Design-System/tokens/base.css";
@import "../../OS-000-Design-System/tokens/theme-neutral.css";

/* Project-specific overrides (optional) */
@theme {
  --color-primary: #8B2252;      /* Magda's brand colour */
  --color-cta: #8B2252;
  --color-cta-hover: #6E1B42;
}
```

For OGANIKO projects, swap `theme-neutral.css` for `theme-oganiko.css`.

## 2. Copy components you need

```bash
# Copy all components into your project
cp -r ../../OS-000-Design-System/components/ src/components/ds/

# Or cherry-pick
cp ../../OS-000-Design-System/components/Button.jsx src/components/
cp ../../OS-000-Design-System/components/Hero.jsx src/components/
```

Components use CSS custom property references via Tailwind classes. They'll automatically pick up your project's theme values.

## 3. Add the /design-system page

```bash
# Next.js App Router
mkdir -p app/design-system
cp ../../OS-000-Design-System/viewer/DesignSystemPage.jsx app/design-system/page.jsx
```

Then visit `/design-system` to see all components in your project's theme.

## 4. Build new components

When you build something new for a project, follow the same patterns:
- Use `var(--color-*)` and `var(--spacing-*)` tokens via Tailwind
- Export from a single file
- After the project ships, promote successful components back to OS-000

## Theme files

| File | Use for |
|------|---------|
| `tokens/base.css` | Always import — spacing, typography, radii, shadows |
| `tokens/theme-oganiko.css` | OGANIKO brand projects (Lane 3, some Lane 1) |
| `tokens/theme-neutral.css` | Client projects — override `--color-primary` per brand |

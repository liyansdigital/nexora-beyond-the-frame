# Customizing NEXORA

NEXORA is customised through its CSS layers. Work from the theme inward —
most rebrands need only the token layer.

## 1. Theme tokens (`src/styles/themes/`)

The accent system is defined in `src/styles/themes/scaffold.css`:

```css
--nexora-accent-gradient: linear-gradient(90deg, #38e1ff 0%, #7c5cff 100%);
--nexora-accent-gradient-vertical: linear-gradient(0deg, #38e1ff 0%, #7c5cff 100%);
```

Change the two stops to re-skin the timeline fill, focus accents and gradient
details everywhere at once. Surface colours (deep-space `#05070d` / `#0a0e1a`)
live in the same layer and in `src/styles/video/theme.css`.

## 2. Player styling (`src/video/skin.css`)

Layout, glass treatment, dock shape, menu styling and state visuals
(hover, buffering, controls-hidden) live here. Prefer overriding tokens first;
edit component rules when you need structural changes such as dock position or
corner radius.

## 3. Layout (`src/video/skin.html`)

Add, remove or reorder controls in the template. **Keep source order equal to
visual order** — that order is the keyboard tab order. If you add a control,
also import its component in `src/video/skin.ts`.

## 4. Captions (`src/styles/video/captions.css`)

Caption font, size, colour and background are isolated in the captions layer.

## 5. Preferences (`src/styles/themes/preferences.css`)

Reduced-motion behaviour and other user-preference adaptations live here.

## Verify your changes

```bash
npm run typecheck
npm run build
npm run dev   # eyeball desktop + mobile widths, keyboard-only pass
```

Check keyboard operation and focus visibility after any layout change, and
test legibility over both a bright and a dark scene.

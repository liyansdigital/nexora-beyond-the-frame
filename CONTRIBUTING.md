# Contributing to NEXORA

Thanks for your interest in improving NEXORA. This guide explains how to get
set up and what a good contribution looks like.

## Ground rules

- Be kind and constructive — see the [Code of Conduct](CODE_OF_CONDUCT.md).
- The skin must stay accessible: every control keyboard-operable, labelled,
  with a visible focus indicator, and template order matching visual order.
- Do not regress the error dialog, hotkeys or the status announcer.
- Keep the upstream scaffold layers intact; put visual changes in the theme
  and skin layers (see [ARCHITECTURE.md](ARCHITECTURE.md)).

## Setup

```bash
git clone https://github.com/liyansdigital/nexora-beyond-the-frame.git
cd nexora-beyond-the-frame
npm install
npm run dev        # workbench dev server
```

Before opening a pull request:

```bash
npm run typecheck  # must pass
npm run build      # must pass
```

## Making changes

- **Skin visuals** — edit `src/video/skin.css` and the theme tokens in
  `src/styles/themes/`; avoid editing `scaffold.css` files.
- **Layout** — edit `src/video/skin.html`; preserve source order = tab order.
- **Composition** — new `@videojs/html` components are imported in
  `src/video/skin.ts`.
- **Workbench** — `apps/preview/` is tooling; change it only when the change
  is about the demo or evaluation experience.

## Reporting bugs and requesting features

Use the issue templates. For bugs, include the browser, the steps to
reproduce, and whether the issue also appears with the default Video.js skin —
that distinction saves everyone time.

## Pull requests

- One topic per PR, with a short description of the user-visible change.
- Include before/after screenshots for visual changes (desktop and mobile).
- Note the accessibility impact explicitly if you touch controls or focus.
- By contributing, you agree your work is licensed under Apache-2.0.

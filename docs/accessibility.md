# Accessibility in NEXORA

Accessibility is a design constraint of this skin, not a feature bolted on.

## What is built in

- **Keyboard operation** — every control is reachable and operable by
  keyboard. Template order in `src/video/skin.html` matches visual order, so
  tabbing moves predictably: title bar, centre disc, timeline, then the
  control row.
- **Visible focus** — focus is never suppressed; the aurora accent outlines
  the focused control.
- **Accessible names** — controls keep the labels provided by the
  `@videojs/html` component library; icon-only buttons are labelled.
- **Menus and dialogs** — the settings menu and the error dialog use the
  library's dialog primitives: they open from their trigger, can be dismissed
  with `Escape`, and return focus.
- **Status announcer** — a polite live region announces playback state
  changes (play, pause, seeked, volume) for screen-reader users.
- **Legibility over video** — a gradient scrim and glass surfaces keep text
  and icons readable over bright and dark footage.
- **Reduced motion** — with `prefers-reduced-motion: reduce`, non-essential
  transitions are calmed (see `src/styles/themes/preferences.css`).
- **Touch targets** — on the mobile layout, primary targets are thumb-sized.

## Verification performed

- Keyboard-only walkthrough of the live demo (play, seek, volume, settings,
  captions, fullscreen enter/exit).
- axe-core automated scan of the live demo: **0 violations**.
- Legibility checked against bright (launch) and dark (space) scenes of the
  demo footage.

## Reporting accessibility issues

Accessibility bugs are bugs. Please file them with the bug template and note
the assistive technology and browser involved.

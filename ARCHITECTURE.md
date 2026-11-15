# NEXORA — Architecture

How the skin is put together, based on the actual source in this repository.

## Layers

```
src/
  video/
    skin.ts      Composition: imports and registers the @videojs/html UI components
    skin.html    Declarative layout of the player chrome (source order = tab order)
    skin.css     The NEXORA visual system for the player (glass dock, timeline, menus)
  styles/
    base.css                 Global base styles for the workbench
    video/
      base.css               Player base layer
      captions.css           Caption rendering styles
      scaffold.css           Upstream scaffold styles (kept intact)
      theme.css              Player theme tokens
    themes/
      preferences.css        User-preference driven tokens (e.g. reduced motion)
      scaffold.css           Theme scaffold, incl. the NEXORA accent tokens
      theme.css              Workbench theme
  skin.css       Skin entry stylesheet for the workbench context
apps/preview/    The workbench that runs the skin (React shell + plain-TS frame)
```

## How Video.js v10 is integrated

NEXORA targets the Video.js v10 **HTML renderer** (`@videojs/html` 10.4.0).
`src/video/skin.ts` imports the individual UI components — container, poster,
controls, time slider (with chapters, slider preview and thumbnail), volume
popover, dialogs, buttons for play / seek / PiP / fullscreen / AirPlay / Cast,
the buffering indicator, tooltips and the error dialog — so the player is
composed from the same primitives as the default UI, restyled rather than
reimplemented.

The demo media element is `@videojs/mux-video` 10.4.0, which feeds the player a
Mux playback ID; the skin itself is media-agnostic and works with any source the
HTML renderer supports.

## How the custom UI is structured

- **Layout** is declared in `skin.html`. Element order in the template is the
  keyboard/tab order, and it matches the visual order: title bar, centre disc,
  then the control dock (timeline above the button row).
- **Styling** is layered: scaffold styles stay upstream-compatible, the theme
  layer exposes tokens (surfaces, scrims, the aurora accent gradient
  `--nexora-accent-gradient: linear-gradient(90deg, #38e1ff, #7c5cff)`), and
  `skin.css` composes them into the glass dock, menus and states.
- **State** comes from the player itself: the components expose state through
  attributes/classes (paused, buffering, controls-visible, fullscreen), and the
  CSS reacts — the skin adds no parallel state machine.

## How controls interact with playback

Controls are the standard `@videojs/html` components, so behaviour — seeking,
volume, playback-rate, track selection, PiP, fullscreen, casting — is the
player's own. NEXORA's contribution is presentation and arrangement: grouping,
spacing, hit targets, focus treatment and the visual states for hover, active,
disabled and buffering.

## How timeline previews work

The time slider includes the chapters, preview and thumbnail components. When
the media provides a storyboard (thumbnail) track — the demo's Mux asset does —
hovering or scrubbing shows the frame thumbnail and the hovered time above the
slider, alongside chapter markers and the chapter title.

## How accessibility is implemented

- Components keep their native semantics and ARIA wiring from `@videojs/html`.
- The template order guarantees a logical focus order; focus is always visible.
- A status announcer (live region) reports playback state changes.
- Dialogs (settings, error) trap and return focus per the component library,
  and close on `Escape`.
- `src/styles/themes/preferences.css` carries the reduced-motion treatment:
  with `prefers-reduced-motion`, non-essential transitions are calmed.

## The preview workbench

`apps/preview/` is a Vite app with two parts:

- `src/frame/` — plain TypeScript that creates the player, chooses the media
  and applies workbench options (this is the reference integration).
- `src/shell/` — a React 19 + Tailwind CSS 4 shell (navbar, options panel,
  scenario picker) around the frame. The shell is tooling, not part of the skin.

Build is `vite build`; type safety is checked with `tsc --noEmit`
(`npm run typecheck`). Deployment of the workbench is scripted in
`apps/preview/deploy.mjs` (the public demo runs on Netlify).

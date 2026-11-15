# NEXORA — Beyond the Frame · Design Spec (original design, from owner's brief)

Competition: Contra Video.js Skins Design Challenge. Base: official `videojs skin create`
Scaffold (HTML + CSS), `@videojs/html@10.4.0`. Keep `data-theme` / `data-preset`
attributes and every scaffold control (error dialog, hotkeys, gestures, status
announcer). Change **tokens before rules**; style state via `data-*` attributes;
size with container queries; motion only through the skin's motion tokens so the
preferences stylesheet calms it under `prefers-reduced-motion`.

## Identity
A premium cinema instrument: deep-space dark glass, one aurora accent gradient,
quiet confidence. Not neon, not gamer RGB, not a copy of any existing player or
competition entry (no VHS, no hardware recorders, no colour-from-film gimmicks).

## Tokens
- Base/ink: `#05070d`; panel ink: `#0a0e1a`
- Glass surface: `rgba(13, 18, 32, 0.55)`, backdrop blur 14px, saturate 140%
- Hairline border: `rgba(255, 255, 255, 0.09)`
- Accent gradient (progress fill, focus ring, active states, spinner):
  `#38e1ff` → `#7c5cff` (used sparingly, never as background wash)
- Text primary `#f4f7ff`; secondary `rgba(226, 232, 255, 0.72)`
- Buffered track: `rgba(255, 255, 255, 0.20)` — visually distinct from played fill
- Track base: `rgba(255, 255, 255, 0.14)`
- Radius: dock 16px, buttons 12px, menus 14px, player frame 20px
- Shadow: `0 24px 60px rgba(2, 4, 12, 0.55)` on dock/menus
- Type: `"Inter", "SF Pro Display", "Segoe UI", system-ui, sans-serif`;
  time readouts `font-variant-numeric: tabular-nums`; title letterspaced uppercase 11px
- Ambient glow: soft radial accent glow behind the player frame (pseudo-element),
  static (no animation), removed under reduced motion

## Layout
- Player frame: rounded 20px, overflow hidden, deep shadow.
- Bottom controls live in a **floating glass dock**: inset 12px, rounded 16px,
  glass surface + blur, containing slider row + control row.
- Top bar: media title left; airplay/cast/PiP/fullscreen as quiet glass chips.
- Centre cluster: seek −10s / play / +10s; play is a 72px glass disc with accent
  ring; seek buttons are glass chips with labels.
- Scrim: subtle top/bottom gradient behind control zones for legibility over
  bright footage (in addition to the dock's own surface).

## Timeline
- 4px track, grows to 8px on hover / focus-within / while scrubbing.
- Played = accent gradient fill; buffered = lighter neutral, clearly distinct.
- Chapter markers: 2px notches in a contrasting tone on the track.
- Thumb: 13px glowing dot, scale-in on hover/focus; visible when keyboard-focused.
- Preview bubble: glass pill, time in tabular numerals + chapter title below.

## Controls & states
- Buttons ≥ 44px hit area, icon 22px, radius 12px.
- Hover: `rgba(255,255,255,0.10)` wash. Active/pressed: accent-tinted wash.
- **Focus-visible: 2px solid `#38e1ff`, offset 2px — never removed.**
- Menus/popovers: glass dark surface, hairline border, deep shadow, 14px radius;
  selected radio item shows accent check + label emphasis.
- Volume popover: same glass treatment; slider fill = accent gradient.
- Buffering spinner: accent coloured. Indicators (volume/seek/status): glass pills.
- Captions text: dark pill behind text (`rgba(3,5,10,0.75)`), white text, for
  legibility over bright and dark footage.

## Responsive (container queries, not viewport)
- ≤ 480px container: dock insets 8px; time group shows current + duration in
  compact form; centre seek chips shrink; no overflow, no clipped labels;
  essential controls (play, seek, time, volume/mute, fullscreen) always present.
- ≤ 340px: hide title text if it would collide; keep tap targets ≥ 40px.

## Motion
- Fades/slides ≤ 200ms ease-out via motion tokens only; controls auto-hide keeps
  scaffold behaviour; ambient glow never animates; everything calms under
  `prefers-reduced-motion` (preferences stylesheet + no token bypass).

## Derived decisions (execution, not direction)
Hover shades, gaps (8px in groups, 4px in slider row), and menu padding are
derived from the tokens above. No new controls, overlays, or text are added.

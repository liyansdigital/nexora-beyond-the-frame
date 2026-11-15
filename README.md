# NEXORA — Beyond the Frame

A cinematic skin for **Video.js v10** — dark glass controls that float beyond the
frame of the picture, with an ambient glow drawn from the scene and an
aurora-gradient timeline. Built for the **Video.js Skins Design Challenge** by Mux
on Contra.

**Live demo:** https://nexora-beyond-the-frame.netlify.app/preview.html
The demo plays a NASA "Cosmic Dawn" trailer hosted on the author's own Mux
account, with chapter markers and English/Japanese subtitle tracks.

## The design

- The picture stays clean: one quiet dock, visible before playback, carries
  every control — nothing competes with the film.
- Timeline hover shows the time, the chapter title and a real frame preview
  from a storyboard sprite.
- Legible over bright and dark footage; controls meet a 44px touch target.
- Fully keyboard-operable (Tab order, `k` play/pause, arrows seek/volume,
  `m` mute, `f` fullscreen, `c` captions) with a visible 2px focus ring.
- `prefers-reduced-motion` calms all animation.
- Responsive from desktop down to a 390px phone with no horizontal overflow.

## Technology

Video.js v10 (`@videojs/html`, `@videojs/mux-video`), React, TypeScript, CSS.
The skin itself lives in `src/video/` (`skin.css`, `skin.html`, `skin.ts`);
`apps/preview/` is the demo page that hosts it.

## Run it

```sh
npm install
npm run build   # production build into dist/
```

## Author

**Vikas Kumar Meena** — designer & developer, LIYANS DIGITAL

- GitHub: [@aiworkfromhome555](https://github.com/aiworkfromhome555)
- Contra: [liyanspaperlab](https://contra.com/liyanspaperlab)

## Licence

Apache License 2.0 — see `LICENSE`. Entry to the Video.js Skins Design
Challenge; the author retains ownership.

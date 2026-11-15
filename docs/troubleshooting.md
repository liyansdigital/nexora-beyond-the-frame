# Troubleshooting

## The dev server starts but the player area is empty

The workbench loads its media from Mux. Check your network connection, and
confirm the demo page itself loaded (the shell renders around the player).
Try `npm run build` followed by `npm run preview` to rule out a dev-only issue.

## Styles look like the default Video.js skin

The skin styles were not loaded or were overridden. Confirm the skin entry
(`src/video/skin.ts` and its styles) is imported before the player UI is
created, and that no second copy of the default theme is loaded after it.
Clear the Vite cache by restarting `npm run dev`.

## `npm run typecheck` fails after editing the template

`skin.html` and `skin.ts` must agree: every component used in the template
needs its import in `skin.ts`. Add the missing `@videojs/html` import.

## Storyboard previews do not appear

Previews require a storyboard (thumbnail) track on the media. The bundled demo
asset includes one; arbitrary sources usually do not. Chapters and time
tooltips still work without it.

## Captions menu is empty

The media has no text tracks. The demo includes English and Japanese tracks;
your own media needs WebVTT tracks attached to the asset or the element.

## Fullscreen or PiP behaves differently between browsers

These follow the platform: AirPlay is Safari-only, Cast needs Chrome, and PiP
availability varies. This matches Video.js behaviour and is not skin-specific.

## Still stuck?

Open an issue with the bug template — include browser, OS, and whether the
problem also occurs with the default Video.js skin.

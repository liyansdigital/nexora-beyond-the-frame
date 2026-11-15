# Deploying the preview workbench

The skin is a library-style layer; what gets deployed in this repository is
the **preview workbench** (the live demo).

## Build

```bash
npm install
npm run build     # outputs dist/
```

`dist/` is a static site and can be hosted on any static host.

## Scripted deploys

`apps/preview/deploy.mjs` wraps the supported targets:

```bash
npm run deploy            # uses the project's deploy helper
npm run deploy:netlify    # Netlify (the public demo runs on Netlify)
npm run deploy:vercel     # Vercel
npm run deploy:cloudflare # Cloudflare Pages
```

Each target CLI will ask you to sign in the first time; no credentials are
stored in this repository.

## Notes

- The demo video is streamed from Mux; hosting the static site does not move
  or copy the media.
- No environment variables are required (see `.env.example`).

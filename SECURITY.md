# Security Policy

## Supported versions

NEXORA is a skin (HTML/CSS/TypeScript) for the Video.js v10 HTML renderer.
Security fixes are applied to the latest release on the `main` branch.

## Reporting a vulnerability

Please do **not** open a public issue for a suspected vulnerability.

Use GitHub's private vulnerability reporting on this repository
(**Security → Report a vulnerability**), or contact the maintainer through
[Contra](https://contra.com/liyanspaperlab).

Include what you found, the browser/environment, and steps to reproduce.
You can expect an acknowledgement within a few days. Because NEXORA ships no
server component and collects no data, the most relevant reports concern the
player UI itself (for example, unsafe rendering of titles or caption text) or
the build tooling.

## Scope notes

- The demo video is hosted on Mux; playback IDs used in the demo are public
  by design and are not credentials.
- This repository contains no API keys, tokens or private configuration, and
  contributions must not add any.

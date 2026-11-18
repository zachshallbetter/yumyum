# Security Policy

## Reporting a vulnerability

Report security issues privately through GitHub private vulnerability reporting:
<https://github.com/zachshallbetter/yumyum/security/advisories/new>.
Do not open a public issue for a vulnerability.

Include a description of the issue and its impact, steps to reproduce (a minimal example is ideal), and the affected version or commit.

This is a solo-maintained project. Handling is best-effort with no SLA: there is no guaranteed acknowledgement or fix time, and the maintainer will respond when next active.

## Scope

`@snackstudio/yumyum` is a client-side animation library for React and vanilla JavaScript. It makes no network requests, stores nothing, and has no server component. The input it handles is data supplied by the host page: SVG path strings, colors, configuration objects, and images passed to the image-eating components. In scope are crashes, hangs or unbounded resource use on crafted path or configuration input, and any way the library lets host-supplied data run as code or markup (for example through DOM injection). React and `react-dom` are optional peer dependencies.

## Supported versions

Only the latest release of the package receives fixes.

# Contributing to YumYum

YumYum is a React and vanilla JavaScript library for interactive eating animations, progress loaders and delete transitions. This guide covers setup, the checks to run, and the conventions the repository uses. The longer developer guide is [docs/development.md](docs/development.md), and the structure is described in [docs/architecture.md](docs/architecture.md).

## Setup

You need Node.js 22 and pnpm 9 (the versions CI uses).

```sh
git clone https://github.com/zachshallbetter/yumyum.git
cd yumyum
pnpm install
pnpm dev          # the demo app, usually at http://localhost:5173
```

## Checks

There is no automated test suite. Before opening a pull request, run:

```sh
pnpm build:lib    # tsc, then the library build into dist/
pnpm build        # the demo app into dist-demo/ (what CI runs)
```

Then run `pnpm dev` and check your change in the demo app. CI (`.github/workflows/deploy.yml`) runs `pnpm install --frozen-lockfile` and `pnpm build`, then deploys the demo to GitHub Pages.

## Conventions

- **One engine, two interfaces.** The eating algorithm lives in `lib/core/EatingEngine.ts` and is shared by the React hook (`hooks/useYumYum.ts`) and the vanilla `YumEater` class. Change the engine, not a copy of it.
- **Style-agnostic.** Components use inline styles for structure. Do not add a CSS framework or a stylesheet requirement to the library.
- **Public API.** Anything exported from `lib/index.ts` is public. Document changes in `docs/api-reference.md`.
- **Lockfile.** Commit `pnpm-lock.yaml` with any dependency change; CI installs with `--frozen-lockfile`.
- **Commits.** Conventional style: `feat:`, `fix:`, `refactor:`, `docs:`, `ci:`, `chore:`, `build:`, with an optional scope.
- **Changelog.** Note user-visible changes under `## Unreleased` in `CHANGELOG.md`.

## Pull requests

Describe what changed and why, list the checks you ran, and keep the diff to one concern. Use the pull request template.

Report vulnerabilities through [SECURITY.md](SECURITY.md), not a public issue.

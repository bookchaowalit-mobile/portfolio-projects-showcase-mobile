# Projects Showcase — Mobile

React Native CLI (bare workflow) mobile app for **Projects Showcase**.

Part of [Chaowalit Greepoke](https://bookchaowalit.com)'s 101 Portfolio Projects.

## Canonical React Native CLI template

This repository **is the canonical React Native CLI template** in
`bookchaowalit-mobile`. Its name-substituted copies are:

- `bookchaowalit-mobile/ai-recommendation-engine-mobile`
- `bookchaowalit-mobile/content-press-mobile`

Fix template-level problems here first; each copy owns its own code and CI
file (no shared package). Consolidation/archive of the copies is pending owner
decision D5 (BD-033), see `repository-catalog/portfolio/MOBILE-CONSOLIDATION-2026-10.md`
in solo-empire.

There are **no native `android/` or `ios/` projects** in this repo, so there is
no native (APK/IPA) build. CI builds the Metro Android JS bundle instead.
Product scope: [PRODUCT.md](PRODUCT.md).

## Tech Stack

- **Framework:** React Native 0.76 (bare CLI)
- **Language:** TypeScript
- **Navigation:** React Navigation v6
- **UI:** React Native Vector Icons

## Features

- **Projects** tab: the bundled list of Bookchaowalit projects (46 links,
  copied by hand, not checked for liveness), searchable (all words
  must match name, slug or category) and filterable by category chips with
  counts; tap to open, or "Surprise me" for a random pick from the results.
- **Overview** tab: total projects and a bar per category.
- Static catalog shipped with the app (`src/lib/catalog.ts`); no network
  calls except opening a project in the browser.

## Getting Started

```bash
npm ci
npm start
```

The native `android/` and `ios/` projects have not been generated yet, so
`npm run android` / `npm run ios` need that step first (see
`docs/UPGRADE-PLAN.md`).

## Validation

```bash
npm run validate      # eslint + tsc --noEmit + jest
mkdir -p dist && npm run bundle:android   # Metro bundle smoke check
```

Pure logic lives in `src/lib/` and is unit-tested with Jest (`__tests__/`).
CI (`.github/workflows/ci.yml`) calls the shared
`bookchaowalit/platform-ci-workflows` v1.1.1 jobs (pinned by SHA): `npm ci`,
lint, typecheck, Jest with a line-coverage gate, the Android bundle, and the
security scans. Reviewed scanner exceptions (dev-tooling advisories that only a
React Native upgrade fixes) are in `osv-scanner.toml` and `.trivyignore`.

## Related

- **Frontend:** [bookchaowalit-website/projects-showcase-frontend](https://github.com/bookchaowalit-website/projects-showcase-frontend)
- **Portfolio:** [bookchaowalit.com](https://bookchaowalit.com)

## License

MIT

# Product: Projects Showcase (mobile)

Status: portfolio demo and the canonical React Native CLI template of
`bookchaowalit-mobile`. Not published to any app store.

## What it is

A small React Native 0.76 app that lists the Bookchaowalit portfolio projects
and opens a chosen project in the phone's browser.

## Screens (bottom tabs)

| Tab | What it does |
|---|---|
| Projects | Search box (every word must match a project's name, slug or category), category chips with counts, a favourites-only toggle, a star per project, and "Surprise me" (opens a random project from the current results). Tapping a project opens its URL in the browser. |
| Overview | Total number of projects and a bar per category. |
| Profile | Static name and site text (`bookchaowalit.com`). |

## Data

- The project list is a static file shipped in the app
  (`src/lib/catalog.ts`, 46 links in categories). It is copied by hand from a
  web frontend, so it can be out of date; the app does not check whether a
  link is still live.
- Favourites are the only user data. They are stored on the device with
  AsyncStorage (versioned envelope; corrupt or old data is ignored).
- No backend, no account, no analytics, no network calls except opening a
  link in the browser.

## What does not exist yet

- No generated `android/` or `ios/` native projects, so there is no APK/IPA
  build; CI builds the Metro Android JS bundle instead.
- No store listing, no crash reporting (no runtime to report from yet).
- No project detail screen; the catalog has only name, URL, slug and category.

## Quality

- Jest: 5 test files (search/catalog logic, favourites, persistence codec,
  Projects screen render and favourites flow).
- CI (`.github/workflows/ci.yml`): shared `platform-ci-workflows` v1.1.1 —
  `npm ci`, ESLint (0 warnings), `tsc --noEmit` (strict), Jest with a line
  coverage gate, Metro Android bundle, and security scans (Gitleaks, Semgrep,
  OSV-Scanner, Trivy). Reviewed scanner exceptions: `osv-scanner.toml`,
  `.trivyignore`.

Backlog: `docs/UPGRADE-PLAN.md`.

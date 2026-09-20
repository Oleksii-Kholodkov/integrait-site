# Integrait — Company Site

AI integration for business. This repository is the pilot for the AI-native SDLC defined in the `knowledge-operations` repo (`sdlc-ai-native/`).

## Stack

- [Astro](https://astro.build) (static output)
- Deployed via GitHub Actions to GitHub Pages

## Development

```sh
npm install
npm run dev      # local dev server
npm run build    # production build to ./dist
```

## SDLC Process

Every change follows the workflow defined in `sdlc-ai-native/requirements-architecture.md` (in `knowledge-operations`):

1. Create `work/<id>/spec.md` from `templates/spec.md` — requirement + acceptance criteria + routine/non-routine classification.
2. Create `work/<id>/plan.md` from `templates/plan.md`.
3. Implement on a branch, open a PR.
4. CI enforces build, lint/validate, accessibility, security, and traceability gates (`.github/workflows/ci.yml`).
5. Non-routine changes (see `CODEOWNERS` and pilot scope) require human approval before merge.
6. `deploy.yml` deploys automatically after CI passes on `main`.

Fill in `work/<id>/verification-report.md` and `decision-log.md` per the templates for every change.


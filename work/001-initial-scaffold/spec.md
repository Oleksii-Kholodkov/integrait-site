# Spec: Initial site scaffold

**Work item ID:** 001-initial-scaffold
**Classification:** non-routine
**Source:** Repository bootstrap (pilot for AI-native SDLC)

## Requirement Summary

Stand up the initial Integrait company site project: Astro static site skeleton, CI/CD workflows, CODEOWNERS, and the SDLC artifact structure (`work/`, `templates/`) required by the AI-native SDLC design.

## Acceptance Criteria

- [x] Astro project builds successfully (`npm run build`)
- [x] CI workflow (`.github/workflows/ci.yml`) defines build, lint/validate, accessibility, security, and traceability gates
- [x] Deploy workflow (`.github/workflows/deploy.yml`) deploys only after CI succeeds on `main`
- [x] `CODEOWNERS` marks non-routine paths for mandatory human review
- [x] `templates/` contains spec/plan/traceability/verification-report/decision-log templates

## Assumptions

- GitHub Pages is an acceptable initial hosting target for the pilot (can be revisited — a hosting/DNS change is itself non-routine).
- No page content beyond the default scaffold is required for this work item; content pages are separate, routine work items.

## Risks

- Astro/Node toolchain version drift between local and CI — mitigated by pinning Node 22 in CI.

## Non-Routine Justification

Touches `astro.config.mjs`, `.github/`, `package.json`, and `CODEOWNERS` itself — all flagged non-routine per `pilot-scope.md` §4 (repo/deploy configuration). Reviewed and approved directly by the repo owner as the bootstrap action.

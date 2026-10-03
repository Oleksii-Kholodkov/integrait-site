# Plan: Scope Security Gate to Shipped Dependencies

**Work item ID:** 003-production-security-gate
**Spec:** work/003-production-security-gate/spec.md

## Tasks

1. Move Astro to `devDependencies` and synchronize the lockfile without a major-version downgrade.
2. Change CI's blocking security audit to scan production dependencies only, matching the static deployment artifact.
3. Reinstall from the lockfile and run build, HTML, accessibility, and production dependency audit checks.
4. Record the outstanding upstream build-tool advisory and ensure publication still uses normal CI and Pages gates.

## Dependencies

- GitHub Pages deploys the `dist/` static artifact only.
- Existing site work item `002-bilingual-company-site`.

## Risks Carried Forward From Spec

- The full development dependency tree remains vulnerable until Astro updates its `http-cache-semantics` dependency or the build tool is replaced.
- Revisit the security boundary if server-side rendering, remote asset fetching, or production Node dependencies are introduced.
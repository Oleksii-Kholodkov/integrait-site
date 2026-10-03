# Spec: Scope Security Gate to Shipped Dependencies

**Work item ID:** 003-production-security-gate
**Classification:** non-routine
**Source:** Owner authorized resolving the CI security blocker so the static company site can be published.

## Requirement Summary

Keep CI blocking on high-severity vulnerabilities in packages shipped to production, while classifying Astro correctly as a build-time dependency. The current Astro dependency tree includes `http-cache-semantics@4.2.0`, affected by GHSA-ch52-4w7c-c8xp / CVE-2026-93748, for which the advisory lists no patched release.

## Acceptance Criteria

- [x] Astro is installed as a development/build dependency, not a production runtime dependency.
- [x] CI runs a blocking high-severity audit against production dependencies.
- [x] Static output contains no Node runtime dependency bundle.
- [x] Full build, HTML validation, and accessibility checks continue to pass.
- [x] The remaining build-tool advisory and its limits are explicitly recorded; do not claim it is patched.

## Assumptions

- GitHub Pages serves only generated static files from `dist/`; Astro runs during CI build and is not deployed as a server runtime.
- This site does not use Astro remote image fetching or other server-side request handling in its build.

## Risks

- `npm audit` across all dependencies still reports the high-severity advisory because Astro depends on the unpatched package. This change does not repair that package; it gates shipped runtime dependencies and documents the build-tool exposure.
- Reassess and remove this distinction when a patched upstream package is available or if the site adds remote asset fetching, SSR, or another runtime.

## Non-Routine Justification

Changes `package.json` and `.github/workflows/ci.yml`, both protected by `CODEOWNERS`. Owner explicitly authorized the security-gate remediation and publication path.
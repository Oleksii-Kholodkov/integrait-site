# Verification Report: Production Dependency Security Gate

**Work item ID:** 003-production-security-gate
**PR:** Direct owner-authorized push to `main`; CI traceability PR-only check does not apply.

| Gate | Result | Evidence |
|---|---|---|
| Clean install | pass | `npm ci` completed from the updated lockfile |
| Build | pass | `npm run build` generated `/` and `/de/` |
| HTML validation | pass | `npm exec -- html-validate dist/index.html dist/de/index.html` |
| Accessibility | pass | Pa11y WCAG2AA on both routes; no issues found |
| Production dependency security | pass | `npm audit --omit=dev --audit-level=high`; zero vulnerabilities |
| Full dependency audit | known finding | `npm audit` still reports GHSA-ch52-4w7c-c8xp in Astro's build-only `http-cache-semantics@4.2.0`; advisory has no patched release |
| Traceability check | not applicable locally | CI runs this check only on pull requests; work-item traceability artifact is present |

## Overall Result

pass with documented build-tool advisory

## Notes

- Astro is a build-time dependency. GitHub Pages receives only static HTML, CSS, and favicon files from `dist/`; the built site has no Node runtime package bundle.
- Astro's remote-asset module imports the vulnerable package, but this site does not use remote asset fetching or server-side request handling.
- No major downgrade, audit bypass, or claim that the upstream advisory is patched was made. Reassess when Astro ships a patched dependency or if the site adopts remote assets/SSR.
- `npm ci` on local Node 22.18 reports an `EBADENGINE` warning for transitive `undici` requiring Node >=22.19; the build succeeds. CI config selects Node 22 and should resolve its current compatible release.
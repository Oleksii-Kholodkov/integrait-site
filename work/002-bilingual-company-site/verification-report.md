# Verification Report: Bilingual Company Landing Page

**Work item ID:** 002-bilingual-company-site
**PR:** Not opened

| Gate | Result | Evidence |
|---|---|---|
| Build | pass | `npm run build`; generated `/` and `/de/` |
| Lint | not configured | No lint script or separate lint tool is configured in `package.json` |
| Link/HTML validation | pass | `npm exec -- html-validate dist/index.html dist/de/index.html` |
| Accessibility | pass | Pa11y WCAG2AA scans of both generated pages; no issues found |
| Security scan | pass | `npm audit --omit=dev --audit-level=high` reports zero production dependency vulnerabilities |
| GitHub Pages base path | pass locally | Production preview returned HTTP 200 for `/integrait-site/_astro/LandingPage.BScSdkmM.css`; English and German routes have correct language metadata |
| Deploy | pending | Base-path fix awaits CI and Pages redeployment |
| Traceability check | not run | Work-item traceability artifact exists; the repository gate runs in pull-request CI |

## Overall Result

pass

## Notes

- Browser review verified English `/`, German `/de/`, language switching, and no horizontal overflow at desktop and mobile viewports. The workflow diagram is horizontal on desktop and stacked on mobile.
- Production-preview browser check confirmed the generated stylesheet loads at the GitHub Pages project path and computed styles are applied.
- No dependency, deployment, domain, analytics, form, or tracking configuration was changed.
- Full-tree `npm audit` still reports the unpatched Astro build-tool dependency `http-cache-semantics@4.2.0`; it is not shipped with the static Pages artifact. See work item `003-production-security-gate`.
- No contact destination or verified company/legal details were supplied; the published site has no working lead-contact path or legal notice/privacy pages. Add and review these before promoting the site as a complete commercial launch.
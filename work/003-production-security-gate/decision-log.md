# Decision Log: Production Dependency Security Gate

**Work item ID:** 003-production-security-gate

| Timestamp | Decision Type | Decision | Reviewer | Rationale |
|---|---|---|---|---|
| 2026-10-03 | approval | Owner authorized resolving the required CI security blocker and publishing the site without another confirmation prompt | Repository owner (explicit request) | Preserve a blocking high-severity audit for shipped dependencies. Do not force-downgrade Astro or claim the unpatched build-tool advisory is fixed. |

The remaining development-tool advisory is documented in `spec.md` and must be reassessed when upstream patches it or the build/runtime boundary changes.
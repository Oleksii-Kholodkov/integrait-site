# Spec: Bilingual Company Landing Page

**Work item ID:** 002-bilingual-company-site
**Classification:** non-routine
**Source:** Owner request to create a production-ready Integrait company website; owner specified international audience, English as primary language, and German as the local-language alternative.

## Requirement Summary

Replace the empty site scaffold with an accessible, responsive landing page that explains Integrait's practical AI-integration positioning in English and German. Help prospective customers understand the approach without inventing client results, guarantees, contact details, or unsupported company facts.

## Acceptance Criteria

- [x] English landing page is available at `/` and German translation at `/de/`, with correct document language.
- [x] Visitors can understand the service framing, working principles, first-project approach, and common answers.
- [x] Layout and navigation work at desktop and mobile widths; keyboard focus and reduced-motion preferences are supported.
- [x] Build, HTML validation, and accessibility checks pass for both language routes.
- [ ] The production dependency audit has no high-severity findings.
- [x] No new dependencies, data-collection form, analytics, tracking scripts, or fabricated contact details are introduced.
- [x] The primary path, stylesheets, and language routes work under the GitHub Pages project base `/integrait-site/`.

## Assumptions

- English is the default; German is provided as a secondary language. Ukrainian and Russian are excluded from this initial scope.
- Site copy remains general and factual until the owner supplies specific service details, proof, and contact destination.
- This work builds the site but does not publish it, change domains, or change hosting configuration.

## Risks

- A real contact destination and business/legal details are not yet available; the site cannot be treated as launch-complete for lead conversion or German legal publication until those are supplied and reviewed.
- Broad positioning may need refinement against a specific target segment and offer.

## Non-Routine Justification

The GitHub Pages project path requires `astro.config.mjs` to set the public `site` and `/integrait-site` base. This protected configuration change was made in response to the owner's explicit request to fix the unstyled published page.
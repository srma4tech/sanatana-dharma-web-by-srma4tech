# Web Application Architecture

**Status:** Proposed foundation for review. No application stack has been installed and no UI has been implemented yet.

## Goals

- Build a free, responsive Hindi-English Sanātana Dharma knowledge and devotion website.
- Make content readable without sign-in.
- Prioritize discoverability, accessibility, fast page loads, and a useful mobile experience.
- Consume only a pinned, validated content release from `srma4tech/sanatana-dharma-content`.
- Keep content research and approval independent from frontend releases.

## Proposed stack

- **Astro + TypeScript** for static-first, content-oriented pages and SEO-friendly rendered HTML.
- Use interactive islands only where interaction provides value; avoid shipping a large client runtime to every page.
- Use semantic HTML and accessible design tokens/components. Select a styling approach after the first design-system spike.
- Generate the public site at build time from a pinned content release and its allow-listed manifest.
- Add PWA/offline capabilities after core routes, metadata, accessibility, and content loading are tested.
- Use GitHub Actions for linting, type checks, unit/build checks, link checks where practical, and deployment previews.

This is a recommendation to validate in a small spike, not a claim that these dependencies are already configured.

## Content integration contract

- Never consume the content repository's moving default branch at runtime.
- Pin an immutable release tag or commit and verify the manifest checksum before build.
- Fail the build if the release reference, manifest, hashes, or required locales are missing or invalid.
- Render only manifest-approved published records.
- Do not create public routes for drafts, blocked records, or content with unresolved source/review states.
- Preserve source references and uncertainty notices in the UI.
- Avoid inventing claims, translations, ritual instructions, or relationships in frontend code.

## SEO and accessibility

- Render indexable page content in the initial HTML.
- Use unique, accurate titles and descriptions per route, canonical URLs when a public domain is chosen, sitemap and robots rules, and localized Hindi/English routes with correct language metadata.
- Add structured data only where its fields are factual and supported; never use schema markup to imply verification or authority that the sources do not establish.
- Use keyboard-accessible navigation, visible focus, semantic headings, adequate contrast, reduced-motion support, and meaningful alternative text.
- Keep performance budgets and mobile testing in CI as the app matures.

## Security and privacy

- No secrets in source control or browser bundles.
- No analytics or third-party trackers without an explicit privacy decision.
- Public reading must not depend on authentication.
- If accounts or personalization are added later, treat them as a separate approved scope.

## Next implementation gates

1. Approve the content schema/release contract.
2. Run a minimal Astro/TypeScript build spike and verify output paths for the intended hosting target.
3. Define localized routing and page templates against real approved content fixtures.
4. Add automated checks before building the full UI.

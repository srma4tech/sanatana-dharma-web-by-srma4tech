# Content Release Integration

**Status:** Contract proposal for the web spike; no content loader is wired yet.

## Non-negotiable rules

- `srma4tech/sanatana-dharma-content` is canonical for content, sources, taxonomies, schemas, and publication manifests.
- The web build must consume an immutable release tag or commit, never the moving `master` branch.
- Only records explicitly allow-listed in a validated manifest with `status: published` may become public routes.
- Verify every record's SHA-256 against the manifest before parsing/rendering it.
- Require both `hi` and `en`, plus the source and editorial gates defined by the content repository's validator.
- Missing refs, mismatched hashes, missing locales, unapproved publisher metadata, or invalid manifests must fail the production build closed.
- No draft inventory item is content. Do not synthesize articles or fill missing evidence in frontend code.
- Keep initiation-restricted mantra and ritual limitations intact in both routing and rendering.

## Private repository delivery decision

The content repository is currently private while this web repository is public. Do not embed a GitHub token in browser code or commit it to the repository. Before implementing the release downloader, choose and document a server-side build-time delivery mechanism (for example, a narrowly scoped GitHub Actions secret that can read only the content release, or a reviewed public release artifact). The build must pin an exact immutable release identifier and verify the manifest and file hashes.

## Spike boundary

This PR intentionally does not fetch or render content. It validates that Astro + TypeScript can host a responsive static shell. Content routes, release download, hash verification, localization routing, and PWA behavior remain gated on a reviewed release artifact and automated tests.

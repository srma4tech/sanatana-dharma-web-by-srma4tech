# Content Release Integration

**Status:** Build-time release bridge implemented; no real content release is configured yet.

## Source of truth and immutable pin

- `srma4tech/sanatana-dharma-content` remains canonical.
- A production release must be checked out at an exact immutable commit SHA or reviewed release tag. Never read the moving `master` branch.
- Run the content repository's `npm run validate:release` successfully before the web build.
- The web release preparer independently checks the manifest, publisher approval, allow-listed entity paths, record IDs/types/statuses, SHA-256 hashes, Hindi and English approval states, editorial approval, and verified claim-level source references.
- Only records listed in `content/manifest.json` are included in `src/data/published-content.json`. Inventory items and unlisted entity files are never treated as publishable content.

## Build modes

- `npm run build` is the foundation/preview build. If `SANATANA_CONTENT_DIR` is not set, it writes an explicit `not-configured` dataset with zero records.
- `npm run build:production` requires `SANATANA_CONTENT_DIR` and fails closed if the release is missing, empty, or invalid.
- Do not deploy the foundation build as a production content release. A production workflow must provide the pinned checkout and run the content repository's release validator before the web build.
- Content release files are build inputs only; private repository credentials must never enter browser code or generated assets.

## Private repository delivery

The content repository is private and the web repository is public. A production workflow must use a narrowly scoped GitHub Actions secret with read-only access to the content repository, check out an exact SHA, run its validator, and only then build the public artifact. Do not commit a token, put it in `PUBLIC_*` variables, or expose it client-side. No secret or deployment workflow is configured in this PR because no approved non-empty content release exists yet.

## Current publication status

No religious article or record is currently approved for the website. Passing technical tests verifies the release gate implementation, not factual or religious accuracy. Human review and explicit product-owner approval remain mandatory.

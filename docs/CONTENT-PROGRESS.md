# Content Delivery Progress & Sprint Tracker

**Tracker role:** Website-side view of content readiness and integration dependencies. The content repository remains authoritative for topic, research, editorial, and publication status.  
**Snapshot date:** 2026-10-18  
**Web repository:** `srma4tech/sanatana-dharma-web-by-srma4tech`  
**Canonical content repository:** `srma4tech/sanatana-dharma-content`  
**Current phase:** Content-release bridge implemented; waiting for a reviewed, approved content release.  
**UI design:** Intentionally deferred to a separate project conversation. This tracker does not approve or specify the full visual design.

## 1. Current state

- [x] Astro/TypeScript website foundation is merged into `master`.
- [x] Static content-release preparer and fail-closed foundation build are implemented.
- [x] Manual content-release-candidate workflow accepts an exact content commit SHA.
- [x] Production build validates the content release before building localized pages.
- [x] Hindi and English library routes and localized article routes are generated from the validated manifest dataset.
- [x] The release-candidate workflow uploads a review artifact only; it does not deploy.
- [ ] Real content release — none exists yet.
- [ ] `CONTENT_REPO_READ_TOKEN` secret — repository documentation says it is not configured yet; configuration must be verified before running the private-content checkout workflow.
- [ ] Published article routes from real approved records — none.
- [ ] Production deployment — not performed.
- [ ] Full UI/UX design and visual implementation — intentionally deferred.

## 2. Content source of truth

The canonical progress and research backlog live in the content repository:

- Repository: [sanatana-dharma-content](https://github.com/srma4tech/sanatana-dharma-content)
- Progress tracker: [docs/CONTENT-PROGRESS.md](https://github.com/srma4tech/sanatana-dharma-content/blob/master/docs/CONTENT-PROGRESS.md)
- Master inventory: [content/inventory/master-inventory.json](https://github.com/srma4tech/sanatana-dharma-content/blob/master/content/inventory/master-inventory.json)

At the 2026-10-18 snapshot, the inventory has **32 provisional topics** across five collections. All 32 are planned, Hindi and English are not started for every topic, and all are marked not publishable. There are no authored entity/source records and no release manifest.

**Do not treat inventory entries, draft branches, the foundation dataset, or a passing web CI run as published religious content.**

## 3. Content-to-web delivery contract

1. Content is researched and authored in the canonical content repository.
2. Work is grouped into small batches of approximately 3–5 entities.
3. Each locale receives independent language review; both locales must satisfy publication gates.
4. Source verification, editorial approval, rights checks, and restricted-practice checks are recorded explicitly.
5. Only approved records with valid paths and hashes may enter `content/manifest.json`.
6. The product owner approves the exact content release before it is used.
7. The web workflow checks out the exact immutable content commit and runs the content validator.
8. The web release preparer independently validates the manifest, hashes, status, locale approvals, source references, and restricted-content gates.
9. A successful candidate build produces an artifact for review. It does not publish or deploy automatically.
10. Any missing, empty, or invalid release must fail closed.

## 4. Sprint board — website dependencies

### Sprint W0 — Foundation and release bridge

- [x] Repository foundation and static-first stack.
- [x] Content release bridge and fail-closed build behavior.
- [x] Bilingual library and article routes generated from validated data.
- [x] Manual-only release candidate workflow and artifact review path.
- [ ] Verify/configure the narrowly scoped `CONTENT_REPO_READ_TOKEN` secret.
- [ ] Run the release-candidate workflow only after an approved content release exists.

### Sprint W1 — First real content integration

- [ ] Receive an explicitly approved, pinned content commit and manifest.
- [ ] Run the content validator and web release-candidate workflow against that exact SHA.
- [ ] Review generated Hindi/English library and article routes, source references, and metadata.
- [ ] Check route integrity, missing-content behavior, and publication allow-list.
- [ ] Record artifact review findings and fix any defects before considering deployment.

### Sprint W2 — Full website UI/UX

**Out of scope for this content-planning conversation.** The dedicated UI-design conversation should review the product experience, information architecture, page templates, responsive behavior, accessibility, typography, navigation, search, and visual direction before implementation is proposed. No visual redesign or deployment is authorized by this tracker.

### Sprint W3 — Release and deployment readiness

- [ ] Approve UI and accessibility/performance review separately.
- [ ] Confirm hosting and deployment workflow; do not assume GitHub Pages or any production target is already configured.
- [ ] Verify the reviewed artifact corresponds to the approved immutable content release.
- [ ] Document rollback and correction procedures.
- [ ] Deploy only after explicit approval.

## 5. Definition of done for a web content integration

- [ ] Exact content commit SHA is pinned.
- [ ] Content validator passes without bypasses.
- [ ] Manifest allow-list, entity paths, IDs, hashes, source references, and locale approvals are valid.
- [ ] No draft, inventory-only, unverified, or incomplete item is rendered.
- [ ] Hindi and English routes have equivalent approved content coverage.
- [ ] Article source references are visible and resolve correctly.
- [ ] Built-site tests and workflow checks pass.
- [ ] Candidate artifact is manually reviewed.
- [ ] Deployment remains a separate explicit decision.

## 6. Known blockers and risks

- No real content records or source records exist yet.
- The content manifest does not exist; production release validation is expected to fail until a complete approved release is created.
- The private content checkout secret needs setup/verification before the manual workflow can access the content repository.
- UI design is intentionally separated from the content sprint; do not conflate content readiness with visual design completion.
- Passing CI proves implementation checks, not the religious accuracy of future content.
- No production deployment has been performed.

## 7. Change log

| Date | Change | Evidence |
|---|---|---|
| 2026-10-18 | Initial website-side content delivery tracker created after merging the pinned bilingual content-release workflow. | Web repository `master` snapshot |

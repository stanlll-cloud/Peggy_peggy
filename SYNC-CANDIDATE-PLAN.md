## 2026-11-10 — 0.8.11 source candidate (publication blocked)

Both upstream source branches release-0.8.11 and grmod-0.8.11 point to 469e54731cef5056838f350716b2bb2035ee9b2d. GitHub Latest still returns v0.8.10 and there is no v0.8.11 tag as checked. The published Customizer stays 0.7.5-en.8 at upstream e12ce7f7e1346740619e6df674d39487e507ebd9.

Compared with 31d9734, the source adds optional Auto LCD curves, GR IV 1.20 exposure preview and a soft focus menu entry, and About acknowledgements. See https://github.com/Maxwooow/Ricoh-GRMod/compare/31d9734...469e547. Explicit-base three-way trial still has conflicts in README.md, package.json, shell/updates.go, ui/src/app.tsx and ui/src/i18n.ts. Clean upstream frontend built; tests: 208 passed, 3 failed (existing GR IIIx tests calling removed bridge methods), 231 skipped, including 14 exposure and Auto LCD cases. No Mac packages or camera testing completed.

Resolve the presentation conflicts while preserving the Customizer name, bilingual UI, store promotion, English documentation and GPL attribution. Review the new UI events, store, host bridge, credits fetch/fallback and updater separately against the upstream behavior. Translate new keys and check placeholders. Run the skipped relevant firmware checks with the required fixtures and reconcile the existing UI test failures before Intel and Apple silicon builds and ZIP/guide verification. Keep existing downloads and the published baseline until verification passes.

## 2026-11-09 — 0.8.10 candidate (publication blocked)

The GitHub release v0.8.10 (2026-11-09 07:29:03 UTC) is tagged at default-branch commit 38e25ffa6055527138167d4e1bce7f57e5c34eb6. Both release-0.8.10 and grmod-0.8.10 point to 31d973415f31847cdf94b7d34775b66553c9cdf3 (package version 0.8.10); exact release binary provenance is unverified. The published Customizer remains 0.7.5-en.8, upstream e12ce7f7e1346740619e6df674d39487e507ebd9.

Compared with fe9ca39, the two upstream commits change GR IV white halation, the HDR gain map curve and the model-specific UI preview; preserve these runtime changes verbatim. See https://github.com/Maxwooow/Ricoh-GRMod/compare/fe9ca39...31d9734. An explicit-base three-way trial against the published fork reports conflicts in README.md, package.json, shell/updates.go, ui/src/app.tsx and ui/src/i18n.ts. Clean upstream web build passed; the test suite had 208 passes, 217 skips, and the same three GR IIIx tests failing on removed bridge APIs. This is not a camera test.

Resolve the five conflicts in a review branch: preserve the English README, attribution and GPL-2.0, branding, Traditional Chinese default, English switch and More Color Recipes link; compare UI event handlers and native bridge calls with the source branch, and limit updater changes to fork destinations. Validate bilingual keys and placeholders. Reconcile the stale test contract against actual upstream behavior and exercise fixture and emulator cases for the new firmware changes. Then build and verify Intel and Apple silicon packages on macOS, check the English PDF, 00-START-HERE.txt and download links, and label camera testing as pending unless completed. Publish only after required verification passes, retain older packages, and verify remote source and ZIP before moving the published baseline. Signed in-app updates remain unconfigured.

# Candidate synchronization plan — 2026-10-17

Published version remains 0.7.5-en.8, upstream baseline e12ce7f7e1346740619e6df674d39487e507ebd9.
Candidate: c45d274b72d4bdcb578ce3aaca20a62cec9fe2df (source 0.7.6).
Latest released upstream tag: v0.7.5.

## New upstream work

Five commits add Linux desktop support (Chromium window, sysfs card enumeration, udisksctl eject), firmware-integrated power-off pictures selected in the camera End Screen menu, a Type/Picture submenu, and version 0.7.6.
Compare: https://github.com/Maxwooow/Ricoh-GRMod/compare/e12ce7f7e1346740619e6df674d39487e507ebd9...c45d274b72d4bdcb578ce3aaca20a62cec9fe2df

## Actual checks

Applied the upstream binary diff with git apply --3way in a separate local candidate worktree. Core, tools, UI store, worker and engine changes applied cleanly and match the candidate upstream byte-for-byte. README, package version and translation dictionaries conflict; these have not been fully resolved or approved. No assertion of complete UI/bridge behavioral equivalence is made.

Ran the unchanged core/test/shutdown.test.ts: 2 data tests passed; 3 firmware tests skipped because private official.bin is absent. These include build/inspect round trips with 1/2/8 pictures and combinations, changed identity/name/order, and invalid-list rejection. No dummy firmware, bypass or weakened safety checks was added.

The upstream tools/shutdown/menu_check.py also requires built RTOS/ICONBIN and official RTOS images. Its camera-menu emulator checks have not run here. New firmware RES growth, menu hooks and self-check ranges therefore remain unverified in this environment. No new regression was established, but the checks are insufficient to publish this candidate.

## Completion plan

1. Resolve three-way presentation conflicts, preserving branding, Traditional Chinese default/English toggle, store banner, license and attribution; translate all new keys and validate placeholders.
2. Retain exact upstream functional files; review app/pages event bindings and Linux bridge/card behavior separately from presentation differences.
3. Supply the legitimately available private firmware fixture in the existing upstream test workflow; run full firmware tests and upstream menu emulation without modifying signature/safety checks.
4. Run frontend/core/Go checks and Intel/Apple silicon builds; inspect signatures, guides and package contents; update English PDF and start-here instructions.
5. Publish a new version only after necessary checks pass, retaining every old package and verifying remote downloads.

Current code, PDFs and download packages on main were not replaced by this candidate. Existing Mac/camera testing limitations and unsigned one-click-update limitation remain. The ongoing upstream watch can continue; this is a candidate release-validation blocker, not a loss of repository access.

## Follow-up upstream review — 2026-10-17

Candidate now 226e14b1f9dff949e862c2a51c55254957826b96, three additional commits after c45d274. The build script now rejects stale UI bundles. End Screen pictures now reuse the camera's own End Screen controller in picture mode, and map the picture list to the End Screen hardware-key map. Upstream comments explicitly report that hardware keys previously did not work while touch did; this concerns the unpublished candidate, not the preserved en.8 release.

Applied the follow-up patch to the isolated candidate after the initial three-way merge. Core and tools still match the new upstream exactly. The unchanged shutdown tests again pass 2 data tests and skip 3 firmware tests. The private official.bin and menu-emulation input images remain unavailable. No new Mac package, full UI equivalence result or camera test is claimed. Existing publication hold remains in effect; complete the review steps above before releasing.

## Upstream v0.8.0 — 2026-10-17

New commit/tag: 16327dbe7bf9e5fd5e4db99ef47237b2240e5487. Latest release is now v0.8.0. Candidate designation is 0.8.0-en.9, not a published package.

The UI now offers power-off pictures only through the camera menu and writes firmware from every editing page. Legacy startup-script creation/restoration controls are removed upstream; legacy wallpaper core remains for older formats. Store, page, output-bar and tour changes must be synchronized as functional changes, not overridden to preserve the previous UI. Existing fork translations must be reconciled with removed/new keys, and English instructions/PDF must no longer prescribe the legacy script flow for 0.8.

This run inspected the upstream diff and verified the release tag against its commit. It did not merge the new UI changes, complete UI/bridge behavioral equivalence checks, build a Mac candidate or publish new binaries. The private firmware fixture and menu-emulation images are still absent, so the previously recorded firmware-validation hold remains. Published version 0.7.5-en.8 and every existing package remain unchanged. The older candidate review sections above are historical; this section is the latest candidate scope.

## Upstream v0.8.1 — 2026-10-21

New commit/tag: 3eadc6a057f46c2f357c7bd7b5470efc61fdaab7. Latest release is now v0.8.1. Candidate designation is 0.8.1-en.10, not a published package.

Ricoh now lists firmware 1.20 for GR IV / GR IV HDF. GR Mod still builds only on official 1.11, and a camera upgraded to 1.20 no longer accepts the 1.11-based modified firmware. Upstream v0.8.1 therefore recognizes the combined model row, shows 1.20 as unsupported with a do-not-upgrade warning, retrieves the still-hosted 1.11 archive from a pinned Ricoh URL, and refuses it unless its SHA-256 matches. The download API, UI bridge and translations changed together; these are functional and safety changes that must remain identical apart from this fork's naming and bilingual presentation.

The upstream e12ce7f..3eadc6a diff was applied with `git apply --3way` in a fresh isolated worktree. Core, shell functionality, UI host/firmware flow and tests applied cleanly; only README, package version, app presentation and i18n conflicted with the fork's approved customizations. The live Ricoh 1.11 archive was retrieved from the pinned upstream URL and independently matched the committed size (34,478,368 bytes) and SHA-256 `ded47aa6385886e4b1f8f41f8551866ab0f1ecd0aef89934a43ef0e456539e8f`.

On the clean upstream v0.8.1 tree, the TypeScript UI production build passed. With the official 1.11 firmware fixture, 175 core tests passed, including bridge firmware, power-off-picture build/inspect/self-check for 1/2/8 pictures, combinations, added slots, date imprint, soft focus and aspect-ratio oracle checks. Five tests still could not run because the upstream private fixture set also expects `official.decoded`, `B.bin`, `C.bin`, `q400.xmp` and `c200.xmp`; these are not in the public archive. Go tests and Intel/Apple-silicon packaging could not run because this execution environment has no Go toolchain. The shutdown menu emulator also remains pending because its built RTOS/ICONBIN inputs and Unicorn/Capstone environment have not been completed. No camera or physical-Mac test is claimed.

The candidate remains blocked: resolve and review all presentation conflicts while retaining upstream event bindings and download safeguards, provide or reproducibly derive the remaining legitimate test inputs, run the menu emulator and Go tests, and complete both Mac architecture builds before publishing. Main, the published 0.7.5-en.8 package and all older packages remain unchanged.

## Upstream source 0.8.2 — 2026-10-23

Candidate: fb14a2a9c35d822a306b966ecd00c3a602a56763 (12 commits after v0.8.1; 38 changed files). Latest official release remains v0.8.1. Candidate designation: 0.8.2-en.11, unpublished.

New functional scope includes 20 added slots, slot fingerprints and settings guard, look stash, date imprint by look, in-camera halation Off/On with Strength and Colour submenus (including RAW development), landscape-only added ratios, and updater release-line separation. Intermediate live-view repaint experiments were subsequently removed upstream. These changes must be taken from the final commit exactly, not reimplemented from intermediate commits.

Fetched upstream into an isolated clean worktree and inspected the diff, including UI store and updater changes. Clean upstream TypeScript type checking and production UI build passed. Go is still unavailable; no Go tests or Mac Intel/Apple-silicon builds ran. Full new firmware tests, menu emulation and customized UI/bridge equivalence have not been validated. The previous unresolved three-way candidate is preserved without overwrite. No candidate source or binary was published.

Completion: reconcile the cumulative upstream diff from the published e12ce7f baseline using three-way merging; separate approved presentation/i18n/package changes from functional changes; translate new keys and audit placeholders/event bindings; run full fixture-backed firmware and menu tests plus Go tests and both Mac builds; update English guides and inspect final ZIP before publication. Retain published 0.7.5-en.8 and all older packages until those gates pass. No new camera or physical-Mac test is claimed.

## Upstream source 0.8.3 — 2026-10-23

Candidate is now 12c58a5d26f4fe045ada8bc926726c2c83012b4e (five commits after v0.8.2), designated 0.8.3-en.12, unpublished. Latest release remains v0.8.2. Compare: https://github.com/Maxwooow/Ricoh-GRMod/compare/fb14a2a9c35d822a306b966ecd00c3a602a56763...12c58a5d26f4fe045ada8bc926726c2c83012b4e

Date imprint follows camera orientation for shooting and RAW development, including main image, screennail and thumbnail. The new in-camera Follow Orientation switch defaults On; the final implementation captures orientation at exposure start, and corrects the third submenu row's value-icon position. New orientation emulator coverage and date/menu tests accompany these changes. Use the final implementation, not the superseded intermediate orientation hook.

This run verified the upstream HEAD and source version and inspected commit descriptions and changed-file scope (13 files). It did not merge or build this candidate, run its tests, or establish full UI/bridge equivalence. Go remains absent. Previously documented private test inputs and menu-emulation requirements remain unresolved. Existing published 0.7.5-en.8 and older packages were not changed. Extend the cumulative three-way merge, bilingual review and firmware/menu/Go/Mac validation plan above to cover these orientation changes before any release. No physical camera or Mac test is claimed.

## Upstream source 0.8.5 — 2026-10-25

Observed HEAD: 8b4ca5eac085d4acd0464f87539874cc33931751, 86 commits after the previous 0.8.3 candidate. Latest official release remains v0.8.2. Candidate designation: 0.8.5-en.13, unpublished.

The cumulative scope now includes GR III / III HDF (2.10) and GR IIIx / IIIx HDF (1.60), family-specific firmware caching and project migration, GR IV Direct Flash, date-imprint look names, look layout/visibility and color-fitting changes. Upstream README contains historical round descriptions with differing defaults; the final source and tests must decide behavior, not a paraphrased README. Upstream-reported hardware tests are not tests performed by this fork.

This run checked the remote commit comparison, HEAD, package version and README scope. No merge, candidate test, Mac build or functional equivalence claim is made. Go is still absent. Existing private-fixture and emulator blockers remain. Extend the cumulative three-way merge and bilingual UI/bridge audit to all camera families, migration/cache paths, new exposure logic and new tests. Keep functional files identical to the pinned upstream wherever possible; separately list approved branding/i18n/link/package/doc changes. Complete firmware, Go and both Mac architecture checks and bundle-guide verification before publishing. Published 0.7.5-en.8 and older packages are retained.

Compare: https://github.com/Maxwooow/Ricoh-GRMod/compare/12c58a5d26f4fe045ada8bc926726c2c83012b4e...8b4ca5eac085d4acd0464f87539874cc33931751

## Upstream source 0.8.6 — 2026-10-28

Candidate: 1f4216e4b80d737a3e670c0b6169398f57598b5e, 22 commits after the recorded 0.8.5 candidate, 24 changed files. Candidate designation: 0.8.6-en.14, unpublished. Latest official release observed remains v0.8.5.

New scope: Direct Flash exposure planning, compensation and background range, maximum shutter speed defaulting to the camera sync limit, and nested-menu back-target repair; GR III / IIIx film removal with subsequent presets, names, icons, halation, menu order and hidden entries shifted together; GR IV added-slot hue-sector fitting and firmware blocks. The final hue implementation tries both fits for .cube and .xmp automatically and retains sectors only through upstream's quality guard; the earlier experimental switch and slot-card note were removed. Do not restore intermediate defaults, switches or algorithms when reconciling customizations. Upstream's reported test firmware 064 camera results are not fork tests.

This run verified HEAD, package version, release redirect, commit descriptions and changed-file scope, and read the current README. It did not merge or test this candidate or build Mac packages; full source-level equivalence, bilingual UI event/bridge review and fixture-backed validation remain incomplete. The Go executable remains absent. No newly reproduced fork failure is claimed. Published 0.7.5-en.8, its upstream baseline and all old packages remain unchanged.

Completion plan: extend the cumulative three-way merge from e12ce7f through this pinned commit; preserve branding, language defaults/toggle, advertisement, links, license and attribution as separately reviewed presentation differences. Audit removeFilm state transitions and engine/worker/store payloads, hue block serialization/readback/fingerprints and Direct Flash settings/menu behavior against final upstream source. Run hue and Direct Flash tests plus existing firmware, private-fixture and menu-emulation gates, translation keys/placeholders, Go checks and both Mac builds; verify English PDF/start-here and final downloadable bundle before publication. Previously missing private fixtures and emulator inputs remain blockers. No physical camera or Mac verification is claimed.

Compare: https://github.com/Maxwooow/Ricoh-GRMod/compare/8b4ca5eac085d4acd0464f87539874cc33931751...1f4216e4b80d737a3e670c0b6169398f57598b5e


## Upstream v0.8.9 — 2026-11-06

[GitHub release](https://github.com/Maxwooow/Ricoh-GRMod/releases/tag/v0.8.9), published 08:58:15 UTC, advertises GR IV/HDF JPEG HDR gain maps and 5–8 ADJ lever items. Its Mac ZIP is an upstream binary, not a Customizer build. The release tag and default branch still resolve to `1f4216e4b80d737a3e670c0b6169398f57598b5e` (package 0.8.6). The public `release-0.8.9` and `grmod-0.8.9` branches both resolve to [`fe9ca39fd3353803019c814e2408b50d28e27a3f`](https://github.com/Maxwooow/Ricoh-GRMod/commit/fe9ca39fd3353803019c814e2408b50d28e27a3f), with package 0.8.9 and the advertised implementation. This is the proposed source candidate, not an attestation of the release binaries. It adds 40 commits and changes 275 paths relative to the previous candidate; use the pinned commit rather than the stale tag or a moving branch.

An isolated three-way merge trial used the published upstream commit `e12ce7f7e1346740619e6df674d39487e507ebd9` as the explicit base, the current fork as ours and `fe9ca39fd3353803019c814e2408b50d28e27a3f` as theirs. The repositories do not share Git ancestry. This explicit base reduced the unresolved files to README.md, package.json, shell/updates.go, ui/src/app.tsx and ui/src/i18n.ts. No merge was committed to the fork.

- Functional review: match the pinned camera and firmware code byte for byte; audit the HDR/ADJ UI controls, defaults, store, worker, host payloads, output paths and firmware model/guard checks. Review the 1.12 bridge firmware removal and enforce the remaining pre-write checks and model isolation. Do not restore the removed APIs merely to pass stale tests.
- Customization review: resolve README and package branding, reapply the language selector and translate new keys/placeholders, preserve the More Color Recipes banner and both LUTs Maker links, and change only approved updater destinations while retaining the signing key and verification. Preserve GPL-2.0 and credits, then update the English PDF and start-here text. Keep all old ZIPs.
- Verification: the unmodified pinned upstream source built its web UI. Its full core test command returned 200 passed, 216 skipped and 3 failed. All three are in `core/test/gr3x-ui.test.mjs`: removed `outputBridge` / `setBridgeOpen` are still invoked. That suite passed all 22 tests at `1f4216e4`. Upstream commit `628c475d339c2845c5965d8462a6b9a297e3a13a` removed bridge generation. The evidence demonstrates a test regression; it does not demonstrate a camera failure. Resolve the expected test contract while retaining coverage for blocked output and model switches before proceeding. HDR and ADJ suites passed their runnable cases (5 and 4 respectively); firmware-dependent cases were skipped, including the new firmware and monochrome unlock suites. Obtain the required fixture/emulator inputs, run Go tests and build and inspect the Intel and Apple silicon Mac bundle, including its package contents and links. Record physical camera testing separately. The Customizer candidate was not built or published. Independent signed in-app updates remain unconfigured.

## Upstream source 0.8.12 — 2026-11-12

Latest source candidate: `245a2335efd249fdb06af20f560a8197b66b30e6` on release-0.8.12, designated 0.8.12-en.18 (unpublished). Four commits and 12 changed files follow 469e547. Latest formal release remains v0.8.11. The default main branch and v0.8.11 tag now both resolve to 469e547, replacing the previously observed 38e25ffa; the release tag now matches the previously reviewed 0.8.11 candidate. This resolves the observed tag/source mismatch for 0.8.11, but is not proof of release binary provenance.

Functional changes: patch the wide Setup menu copy as well as the original descriptor so GR IV 1.20 End Screen opens the power-off pictures submenu; retain the new unexpected-layout guard. UI store changes shorten the pre-write confirmation list to names/counts. Packaging adds a Python HFS+/DMG writer fallback, and the Image Control icon and brightness labels change. These are upstream changes, not fork customizations.

Checks on pinned clean source: npm dependencies installed; TypeScript/Vite web production build passed on a sequential final run (an earlier build process exited 139; no reproducible application fault established). Core suite: 208 passed, 232 skipped, 3 failed. The same three GR IIIx UI tests call removed outputBridge/setBridgeOpen APIs. The new wide-menu power-off-picture test is among the three skipped exposure tests because GR IV 1.20 firmware is absent. No firmware or camera verification of this fix is claimed. A fresh explicit-base git apply --3way trial from published upstream e12ce7f against the fork source again conflicts in README.md, package.json, shell/updates.go, ui/src/app.tsx and ui/src/i18n.ts. No candidate merge was committed.

Customization review remains separate: preserve Ricoh GR Customizer, Traditional Chinese default/English selector, English description, More Color Recipes banner and https://luts-maker.uk, README footer link, GPL-2.0 and upstream credits. Translate new chkChanges/chkCount/chkPictures/chkHidden/chkRatios keys and check placeholders. Functional review must cover the changed pre-write dialog and wide-menu descriptor guards plus the cumulative UI event bindings, host/worker payloads and camera logic; preserve upstream signature checks. Do not restore removed camera APIs just to satisfy stale tests.

Completion order: resolve and review the cumulative three-way conflicts; verify unchanged functional files and permitted presentation differences; resolve test-contract failures without camera behavior changes and supply legitimate firmware/emulator inputs; run Go checks and both Mac builds; update and inspect English PDF, 00-START-HERE.txt, links and final ZIP; publish only after the required gates pass and verify remote files/downloads. The available /usr/bin/go does not implement the Go language toolchain (`go version` returns “Unknown option”), so it cannot build this project. No Customizer Mac Intel/Apple silicon bundle or new camera test was completed. Published 0.7.5-en.8 and every old package remain unchanged; independently signed one-click updates remain unconfigured.

## 0.8.12 wording follow-up — 2026-11-13

Candidate advances by one commit to `41b985db5c7ee7716aef55f8d44c05664579b2a4` on release-0.8.12; designation remains 0.8.12-en.18, unpublished. Only ui/src/i18n.ts changed (127 lines added/replaced). Default main remains 469e547; latest formal release remains v0.8.11.

AST inspection found 434 keys in each upstream Chinese/English dictionary, no added/removed keys versus 245a233, and no changed or cross-language mismatched placeholder sets. The English roleOther value is now Chinese “（空白）”; translate this presentation value to English when reconciling the fork. The Chinese dictionary is still Simplified Chinese and does not fulfill the fork's Traditional Chinese default requirement. These upstream wording changes do not resolve the five presentation/updater merge conflicts or establish customized UI event/bridge equivalence.

The clean pinned source passed TypeScript checking and Vite production build. Camera/firmware/bridge functional sources and tests are unchanged from 245a233; the prior 208 passed / 232 skipped / 3 failed test result is historical and was not rerun for this wording-only commit. The missing firmware input and unresolved removed-API test failures remain. No candidate merge, Mac builds, package update or camera test was completed; published 0.7.5-en.8 and all old ZIPs remain unchanged. Continue the preceding completion plan before any publication.

## Default branch privacy policy — 2026-11-13

Observed main advances from 469e547 to `6c2e88e750719828a5eab1d1130aa2016a1e7e09` (merge #26 and a978202). The complete diff against 469e547 adds only PRIVACY.md (36 lines); no runtime source, UI binding, bridge, firmware algorithm or tests changed. release-0.8.12 remains 41b985d and latest formal release remains v0.8.11.

Read the complete Chinese/English policy. It covers upstream iOS/Android/Windows/macOS, Bluetooth/Wi-Fi firmware push/log sharing, states “no ads”, and limits network destinations to Ricoh/GitHub/jsDelivr. Those claims cannot be copied as a verified policy for the current desktop Customizer, which intentionally includes a More Color Recipes promotional link to https://luts-maker.uk and has a different published source baseline. Do not remove the approved banner or invent mobile/connectivity behavior to match upstream documentation. Reconcile the policy with the actual reviewed fork source and user-initiated external links during candidate documentation review, retaining upstream attribution. No policy or runtime source was merged into the published fork in this run.

This documentation-only update does not justify rerunning the unchanged runtime tests/builds; earlier candidate checks and all remaining publication gates still apply. No Mac builds or camera tests were performed, no new download package was published, and 0.7.5-en.8 plus all existing packages remain preserved.

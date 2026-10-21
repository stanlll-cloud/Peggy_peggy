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

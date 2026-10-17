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

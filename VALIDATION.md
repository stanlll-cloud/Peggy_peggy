# Current validation - 0.7.4-en.6

See RELEASE-NOTES.md and SYNC-REPORT.md for the current scope and limits.

# Validation — Ricoh GR Customizer 0.7.3-en.4

## Current update

- Upstream 0.7.3 core code, camera defaults and safety checks are unchanged. Repository-specific update addresses replace the original author's addresses; no signature checks were removed. Signed in-app installation is not provisioned, and community updates are manual downloads.
- UI TypeScript and production build passed. Translation coverage and placeholders passed for 344 English/Traditional Chinese keys.
- Core: 118 passed, 110 skipped, one collection failure due to missing private official.bin in bridge.test.ts. No dummy fixture or test-source change was used.
- All seven tested Go packages passed against the upstream placeholder expected by the test. Mac universal cross-build and ad-hoc signing completed with both x86_64 and arm64 slices.
- The PDF includes a third page for 0.7.3 halation, manual updates and validation limits. Links and package contents were checked.
- This version has not been launched on a physical Mac, written to a camera card or flashed to a camera. Apple codesign validation is pending; ad-hoc signing is not notarization.

## Historical edition 3 checks

- UI TypeScript checks and Vite production build: passed.
- Desktop Go tests: all six tested packages passed; two tools have no tests.
- Core suite: 118 tests passed, 107 skipped. One suite failed during collection because upstream bridge.test.ts reads core/testdata/private/official.bin even when its suite is skipped. Private official firmware is not distributed. No firmware-processing source or tests were changed.
- Mac universal executable: x86_64 and arm64 slices confirmed.
- Ad-hoc signing completed with rcodesign 0.29.0. Both slices report ADHOC signatures and the English community bundle identifier. The rcodesign verifier reports missing CMS values for ad-hoc signatures and warns that its verifier is buggy. Apple codesign verification is still required on macOS.
- English interface dictionary, HTML, and macOS permission strings contain no Chinese characters. Existing camera-language options remain supported with English labels.
- git diff --check: passed.
- Browser visual QA blocked: Playwright browser download returned an invalid archive. No visual pass is claimed.
- No Mac launch, physical card access, firmware flashing, or camera behavior validation was possible in this Linux environment.

Before a public release, validate on macOS with:

```sh
codesign --verify --deep --strict --verbose=2 "/Applications/Ricoh GR Customizer.app"
```

Then check first launch, permission prompts, navigation, preset import, preview, and exports. Test card and camera workflows with backed-up data and the exact supported camera/firmware combination.

## English edition 2

- TypeScript and production build passed after adding the store link.
- https://luts-maker.uk returned HTTP 200 over HTTPS.
- The link uses target=_blank and rel=noopener noreferrer, with visible destination text and an accessible label.
- No core/ files were modified.
- The owner confirmed the previous edition opens on macOS; this rebuilt edition still needs a new Mac launch and click check.

## Edition 3: Traditional Chinese

- Added a full Traditional Chinese operation dictionary, defaulting to zh-TW with a persistent English switch.
- Store advertisement copy and URL remain English and unchanged.
- Dictionary key coverage is checked by TypeScript; interpolation and switching verified in a Node harness.
- Rebuilt and ad-hoc signed for Intel and Apple silicon.
- Mac visual and physical-camera validation remains pending.

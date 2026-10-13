# Validation — Ricoh GR Customizer 0.7.0-en.2

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

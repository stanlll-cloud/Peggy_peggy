# Ricoh GR Customizer 0.7.3-en.4

Based on upstream 0.7.3, commit 675ba64f8cf30811a8d4d4a6899f6fbeb445f490.

- Add film-style red halation to added preset slots. Highlight thresholds follow each preset.
- Include upstream RAW-development fixes and added-slot write support.
- Keep the English / Traditional Chinese interface and LUTs Maker links.
- Include the English PDF guide with an updated halation and manual-update supplement.

The community app's update addresses now point to this repository. The original signature checks remain unchanged. Signed in-app installation has not been provisioned for this edition: get updates from the README download link and replace the app manually.

## Validation and limits

Frontend TypeScript / production build, translation-key coverage and placeholders, Go package tests, and Mac Intel / Apple silicon cross-build were checked. Core tests: 118 passed, 110 skipped; the bridge suite cannot collect without the private official.bin firmware fixture. No firmware fixture or bypass was added.

The Mac app is ad-hoc signed. It is not Developer ID signed or notarized. There has been no physical Mac launch, memory-card write or camera flash test of this update. Earlier owner-reported GR IV / GR IV HDF testing applies to the earlier edition. This remains a community beta, not a claim of camera-tested equivalence.

Core firmware behavior, defaults and safety checks match upstream. Presentation changes and repository-specific update destinations are documented in SYNC-REPORT.md.

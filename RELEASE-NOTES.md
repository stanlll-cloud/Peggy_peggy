# Ricoh GR Customizer 0.7.5-en.8

Based on upstream commit e12ce7f7e1346740619e6df674d39487e507ebd9 (source version 0.7.5; latest published upstream release at sync: v0.7.4).

- Upstream version-only bump to 0.7.5; no functional source changes since 0.7.4-en.7.
- Fix ratio-preview hangs on refused intermediate inputs, exactly as upstream. Fourteen actual preview-method inputs checked without loading firmware; all returned in under 30 ms.
- Shorten halation help text in both languages.
- Include halation in every added slot, with preview-only Off / Weak / Strong controls; camera-side Halation sets the actual strength. Unset preview defaults to Off.
- Remove partial-reset alternative advice and allow dialog buttons to wrap.
- Preserve the upstream red camera-reset warning before writing factory firmware, including official backups. Cancel receives focus; explicit confirmation is required.
- Translate updated labels into English and Traditional Chinese. Keep the default Traditional Chinese interface, English switch, branding and More Color Recipes link.
- Include the English PDF guide, a new factory-reset supplement, start-here instructions, complete corresponding source and GPL-2.0 notices.

Community updates are manual downloads from this repository. Independent signed in-app installation is not configured. Signature checks remain unchanged.

## Validation limits

TypeScript / production build and 349 translation keys/placeholders passed. The actual confirmation functions and dialog were exercised for cancel, confirm, red warning and focus attributes. Core tests: 118 passed, 112 skipped; one collection failure requires private official.bin. No dummy firmware or bypass was added.

Mac Intel and Apple silicon cross-build and ad-hoc signing checked. Physical Mac launch, Apple codesign validation, memory-card writing and camera flashing were not performed. Earlier owner-reported GR IV / GR IV HDF testing applies to the earlier edition only. Community beta; not Developer ID signed or notarized.

# Ricoh GR Customizer 0.7.4-en.5

Based on upstream commit 89d2a66e23104a278512f8fc511fc9d7c5a10d96 (source version 0.7.4; latest published upstream release at sync: v0.7.3).

- Preserve the upstream red camera-reset warning before writing factory firmware, including official backups. Cancel receives focus; explicit confirmation is required.
- Translate all six new labels into English and Traditional Chinese. Keep the default Traditional Chinese interface, English switch, branding and More Color Recipes link.
- Include the English PDF guide, a new factory-reset supplement, start-here instructions, complete corresponding source and GPL-2.0 notices.

Community updates are manual downloads from this repository. Independent signed in-app installation is not configured. Signature checks remain unchanged.

## Validation limits

TypeScript / production build and 350 translation keys/placeholders passed. The actual confirmation functions and dialog were exercised for cancel, confirm, red warning and focus attributes. Core tests: 118 passed, 110 skipped; one collection failure requires private official.bin. No dummy firmware or bypass was added.

Mac Intel and Apple silicon cross-build and ad-hoc signing checked. Physical Mac launch, Apple codesign validation, memory-card writing and camera flashing were not performed. Earlier owner-reported GR IV / GR IV HDF testing applies to the earlier edition only. Community beta; not Developer ID signed or notarized.

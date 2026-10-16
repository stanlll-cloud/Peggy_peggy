# Synchronization review - 0.7.4-en.5

Published upstream baseline: 89d2a66e23104a278512f8fc511fc9d7c5a10d96.
Previous baseline: 675ba64f8cf30811a8d4d4a6899f6fbeb445f490.

The upstream patch was applied using git apply --3way. README, package version and i18n conflicts were resolved by retaining fork presentation and incorporating the new upstream documentation and six translations. No functional conflict remained.

## Functional code

- core/ and tools/ are byte-identical to upstream.
- ui/src/store.ts and components.tsx are byte-identical, including factory-reset confirmation, stock export/card conditions, official-copy detection, cancel/confirm handlers, Escape/backdrop dismissal and focus attributes.
- All other UI source files are identical except app.tsx, pages.tsx, i18n.ts and styles.css. app.tsx adds only language subscription/toggle and a date display locale; pages.tsx adds only the external shop banner. Their existing event bindings remain unchanged.
- shell/ matches upstream except build.sh branding/permission text and repository-specific update URLs in updates.go and internal/server/update.go. Original signature key and verification code retained.
- No camera algorithms, defaults, firmware formats, write operations or safety checks were customized.

## Presentation differences

Ricoh GR Customizer name, Traditional Chinese default plus persistent English toggle, English More Color Recipes link to https://luts-maker.uk, English outward README and PDF, package identity and complete source/manual distribution. Upstream README and GPL/author credit retained. Signed one-click installation is not provisioned; use manual downloads.

## Actual checks and limitations

Frontend build, 350-key/placeholder parity, language switching, actual reset confirmation functions and dialog server render passed. Core: 118 passed / 110 skipped / bridge suite cannot collect without private official.bin. Go tests run against their expected upstream placeholder; production UI embedded for build. Universal Mach-O and ad-hoc signatures checked. PDF supplement rendered and reviewed; package contents and remote ZIP hash verified before completion.

No physical Mac launch, Apple codesign verification, memory-card write or camera flash. Previous owner-reported GR IV/HDF tests do not certify this update.

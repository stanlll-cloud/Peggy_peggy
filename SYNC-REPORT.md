# Synchronization review - 0.7.4-en.6

Published upstream baseline: 589e7f48fe21bfdd7e65f5b9973b15e490cd8120.
Previous baseline: 89d2a66e23104a278512f8fc511fc9d7c5a10d96.

The upstream patch was applied using git apply --3way. README and i18n conflicts were resolved by retaining fork presentation and incorporating the new upstream documentation and updated translations. No functional conflict remained.

## Functional code

- core/ and tools/ are byte-identical to upstream.
- ui/src/store.ts and components.tsx are byte-identical, including factory-reset confirmation, stock export/card conditions, official-copy detection, cancel/confirm handlers, Escape/backdrop dismissal and focus attributes.
- All other UI source files are identical except app.tsx, pages.tsx, i18n.ts and styles.css. app.tsx adds only language subscription/toggle and a date display locale; pages.tsx adds only the external shop banner; stripping that banner gives a byte-identical upstream file, including halation preview event bindings. Their existing event bindings remain unchanged.
- shell/ matches upstream except build.sh branding/permission text and repository-specific update URLs in updates.go and internal/server/update.go. Original signature key and verification code retained.
- No camera algorithms, defaults, firmware formats, write operations or safety checks were customized.

## Presentation differences

Ricoh GR Customizer name, Traditional Chinese default plus persistent English toggle, English More Color Recipes link to https://luts-maker.uk, English outward README and PDF, package identity and complete source/manual distribution. Upstream README and GPL/author credit retained. Signed one-click installation is not provisioned; use manual downloads.

## Actual checks and limitations

Frontend build, 349-key/placeholder parity, language switching, actual reset confirmation functions and dialog server render passed. Core: 118 passed / 111 skipped / bridge suite cannot collect without private official.bin. Go tests run against their expected upstream placeholder; production UI embedded for build. Universal Mach-O and ad-hoc signatures checked. Embedded production page, host.js and linked assets served HTTP 200 in a Linux smoke check (not Mac execution). PDF supplement rendered and reviewed; package contents and remote ZIP hash verified before completion.

No physical Mac launch, Apple codesign verification, memory-card write or camera flash. Previous owner-reported GR IV/HDF tests do not certify this update.

The actual extraSpecs function was exercised with six slots whose old halation switches were false: all six now emit halation=true, exactly as upstream. Monochrome emits no extra slots. halationOf defaults to on=true, preview=0. The upstream six-slot firmware combination test is included unchanged but skipped without private official.bin; no camera behavior pass is claimed.

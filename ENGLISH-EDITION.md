# Ricoh GR Customizer — 0.7.5-en.8

An English-language community edition of [GR Mod](https://github.com/Maxwooow/Ricoh-GRMod).
Upstream commit: e12ce7f7e1346740619e6df674d39487e507ebd9 (0.7.5).
This edition is not an official Ricoh or Adobe product.

## Changes

- The interface defaults to Traditional Chinese, with an English switch at the bottom of the sidebar. The selected language is remembered.
- Simple photography terms: Preset, Profile, Crop, Aspect Ratio, Swatches, Before / After, Grain, Soft Focus, and B&W Looks.
- Traditional Chinese and English operation labels, guides, and errors. The More Color Recipes store banner remains English in both languages.
- Camera-menu defaults match upstream. Interface language is independently selectable. Existing saved projects keep their camera language.
- The original firmware-processing code is retained.
- A visible More Color Recipes banner links to https://luts-maker.uk on the Image Control page. The link opens on click only; no store content is embedded or sent camera data.
- Clearer card-formatting instructions: back up files first; formatting erases the card.

## Install on macOS

1. Extract Ricoh-GR-Customizer-0.7.5-en.8.zip.
2. Move Ricoh GR Customizer.app to Applications. The displayed application name is Ricoh GR Customizer.
3. Open the app. If macOS blocks it, use System Settings > Privacy & Security > Open Anyway.
4. Allow access to removable volumes when prompted.
5. Use Chrome, Edge, Brave, Chromium, or Vivaldi for the app window; otherwise the default browser opens.

This is an ad-hoc signed community build, not Developer ID signed or notarized.
The original app data location is retained. Close other GR Mod versions before using this edition.

## Build from source

Install Node.js/npm and Go, then run:

```sh
npm ci
npm run build
cd shell
./build.sh mac
```

The upstream build pins Go 1.24.7 for Apple silicon and Go 1.20.14 for Intel.
On Linux, install rcodesign before building for an ad-hoc signed macOS bundle.
On a Mac without rcodesign, sign the built app before distribution:

```sh
codesign --force --deep --sign - "dist/GR Mod.app"
```

Re-create the ZIP after signing. No Ricoh firmware is bundled.

## Sharing and license

Keep LICENSE, upstream copyright notices, third_party notices, and this document.
Distribute the complete corresponding source with every binary release under GPL-2.0-only.
The preview photograph has separate terms documented in the upstream README; it is not GPL code.

## Verification boundaries

See VALIDATION.md for the checks actually completed for this build.
No camera firmware has been flashed as part of this work. Mac launch, permissions,
real memory-card access, and camera behavior need validation on physical hardware.

## Current halation and restore instructions

Every added slot includes halation support; the app only previews Off / Weak / Strong. Choose Weak or Strong with the camera slot's Halation parameter. Reset all camera settings before restoring factory firmware. There is no partial-reset alternative in the current upstream instructions.

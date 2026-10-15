# Upstream sync candidate — 2026-10-15

## Latest draft update: upstream 0.7.3

Candidate `675ba64f8cf30811a8d4d4a6899f6fbeb445f490`, latest published upstream release v0.7.3. Seven additional commits since yesterday's candidate, ten since the published baseline. Reused PR #1 rather than opening a duplicate.

- Added-slot halation, matched to CineStill 800T, with per-slot thresholds based on the look's highlight brightness.
- More room for added looks in RAW Image Control; writing added slots alone works.
- Release-note history, version tour step and manual-update fallback.
- Added all 18 new dictionary keys in English and Traditional Chinese. Coverage and placeholder parity passed for 344 keys.
- Frontend TypeScript and production build passed. Core: 118 passed, 110 skipped, the same missing-private-official.bin collection failure. All seven tested Go packages passed with the expected upstream placeholder.
- All 190 tracked upstream core/shell/tools files except branding-only shell/build.sh match upstream exactly. host.ts, store.ts, updates.tsx, markdown.tsx and tour.tsx also match. app.tsx and pages.tsx match after removing only documented language-switch, display-format and store-banner changes, so upstream bindings and new halation logic are retained.
- Rebuilt the Mac candidate with the official rcodesign 0.29.0 tool and completed ad-hoc signing for the Intel/Apple silicon universal bundle. A first build failed VCS stamping inside the detached worktree; rerunning with GOFLAGS=-buildvcs=false succeeded without changing functionality. Candidate ZIP size: 9,325,195 bytes; SHA-256: 86aa4e034093b63e118a192fc6f1b064c34dae8b38b81c128fd6c5c14a74ad4a. No new binary has been published. Ad-hoc is not Developer ID signing or notarization. Apple codesign verification, Mac launch and camera/firmware checks remain pending.

The signed-update source and key still belong to the original author; the new manual fallback also opens the original author's download page. A release would risk replacing this fork with the upstream app. Fork-specific signing-key custody and release publishing remain unresolved, and no safety checks or update features were disabled. Main and the 0.7.0-en.3 public download remain unchanged.

## Historical checks: 2026-10-14 candidate

**Draft only. The published 0.7.0-en.3 download remains unchanged.**

Upstream main: `60384f8bbc2851b101f667bbcae832ab184959c3` (version 0.7.1 in source). Latest published upstream release checked: v0.7.0. Three commits since the shipped upstream baseline:

- Signed in-app updates: download, verification, replacement and restart.
- Added looks in RAW development and playback; maker-note codes and parameter rows corrected.
- Independent RAW-development parameters for added looks.

## Merge and parity

Used a three-way file merge against baseline `0d5c4494df6967e434eb73743814bbbb3bb1117d`. Resolved version, translation, CSS and documentation conflicts while keeping branding, the language switch, English store banner and README store link. Added both English and Traditional Chinese update-dialog strings. Restored the original camera-language defaults (`zh-CN`) in store.ts; interface language remains independently selectable and defaults to Traditional Chinese. Existing saved camera-language choices are still respected.

All 185 tracked upstream files under core/, shell/ and tools/, excluding branding-only shell/build.sh, match the candidate upstream byte for byte. ui/src/host.ts, ui/src/store.ts and ui/src/updates.tsx also match exactly. app.tsx differences are branding, language switching and display formatting; pages.tsx difference is the store banner. No camera algorithms or update verification checks were changed. Both PDF and start-here file remain in the repository and current public download; they are not represented as updated candidate documents.

## Validation

- UI TypeScript check and Vite production build passed.
- Translation coverage and placeholder parity passed for 326 keys. Update labels switch correctly between English and Traditional Chinese.
- Core tests: 118 passed, 107 skipped, one collection failure because bridge.test.ts eagerly reads missing private official.bin even inside a skipped suite. Test sources remain unchanged.
- Go tests: all seven tested packages passed with the upstream embedded placeholder, as expected by TestAppEndToEnd. The first run against the branded production page failed its literal `<title>GR Mod</title>` assertion; that failure is a branding fixture mismatch, not a claimed production UI pass. The built UI was restored afterward.
- Mac cross-build completed: Mach-O universal executable with x86_64 and arm64 slices. The bundle was **not signed** because rcodesign is absent; it is not suitable for distribution to Apple silicon users. No new binary was uploaded.
- No macOS launch, card write, firmware flash or physical-camera tests were performed. Prior user-reported GR IV/HDF testing applies to the prior edition only.

## Release blockers

The new shell/updates.go contains the original author's update URL and Ed25519 public key. Installing an offered update would install an upstream package and remove this fork's UI/branding/store customizations. Redirecting the URL alone is insufficient: the fork needs its own persistent signing-key custody and signed release manifests/packages. No signature check was disabled, no original-author private key was requested, and the updater was not silently removed. This must be resolved without violating the requested functionality parity before releasing this candidate.

Signing and complete firmware/macOS validation are also pending. The main branch, download ZIP and current user instructions are unchanged. See SYNC-STATUS.json for the published baseline versus pending candidate; do not treat this draft as successfully published or create a duplicate draft for the same upstream commit.

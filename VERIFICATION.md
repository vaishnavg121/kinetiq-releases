# KINETIQ offline Beta verification

Delivery date: 6 November 2026. This extends the existing application; Room remains schema 3 and the permanent signing identities are unchanged.

## What changed

**GPS diagnosis.** In the preserved emulator Guest database, the three saved sessions still contain 142, 116 and 14 points. Every point lies within the configured 500 m endpoint zones, so an empty public route was the intended privacy result. Those are emulator records, not an audit of an unavailable physical phone. A separate renderer defect also existed: any non-null map bitmap suppressed independent polyline drawing, even when the capture lacked the route, while detail rendering depended on map/style readiness. Both paths now use shared validated, deduplicated, dateline-aware geometry. Exports composite their own route using captured projection metadata, or render a route-only poster. A tile-free detail overlay does not wait for a basemap. Invalid/no-track/protected tracks never invent a path. Privacy controls initialize from saved radii; revealing a full route requires explicit consent for that image. See `test-results/offline-saved-route-audit.json` and `preview/offline-proof`.

**Food.** 13,118 usable USDA entries: 7,687 SR Legacy and 5,431 FNDDS. The separate read-only SQLite/FTS asset is 18,935,808 bytes (18.06 MiB), CC0/public domain. Missing micronutrients stay unknown. Household units use source-specific weights; volume needs a known reference/density. Custom foods expose optional nutrients/weights, recipes support cooked yield and fractional portions, and meal multipliers accept fractions. Definitions used by historical diaries remain snapshots. Content-hashed asset installation avoids rewriting personal Room data. Indian staples/aliases are included, but regional Indian coverage is incomplete; unlicensed IFCT/NIN redistribution was excluded. Provenance/checksums/licenses: `docs/DATA_SOURCES.md` and bundled manifests.

**Exercises.** 1,064 normalized records: 287 Everkinetic and 777 additional free-exercise-db metadata records. 96 duplicate names were merged and five instruction-less records excluded. Every catalog record has an offline visual: 268 exact source pose sets and 796 original labelled muscle-target maps. The 537 source SVG files total 10,653,234 bytes; all were pinned/hash-verified and device-decoded. Everkinetic/Greg Priday is CC BY-SA 4.0; free-exercise-db metadata is Unlicense. Its uncertain photographs are excluded. Target diagrams are not movement technique demonstrations. Dedicated verified yoga/Pilates sequences and complete starting/ending pose coverage remain gaps. Filters, favorites/recent, custom metadata and tracking defaults preserve legacy workout identities.

**Online food errors.** Typed searches previously automatically contacted the provider at a 350 ms cadence and surfaced generic failures. Actual probes observed timeouts and HTTP 503, so provider availability is also a factor; a missing User-Agent was not the cause. Local search now stays local. Optional online requests are explicit, cancellable, spaced at 6.5 seconds, query-cached, trimmed to needed response fields, and handle cooldown/network/server errors without hiding offline results. The final real barcode and search probes both returned HTTP 200 and parsed nutrition/five products (`test-results/live-food-api.txt`). This does not guarantee future provider uptime. Personal USDA keys are encrypted locally and excluded from cloud/backup.

**UI.** Static halftone/accent card details, restrained press springs, animated macro proportions, compact catalog headers, structured filters, source imagery and clear unknown/empty/privacy states. Existing themes and AMOLED persist; motion follows Android animation preferences. Twelve actual screen captures use isolated QA records, not personal screenshots or fabricated music playback: `preview/offline.html`.

## Verification

| Check | Actual result |
|---|---|
| Debug + signed release + Android test APK | Passed; full dry-run build 7m 1s, incremental publication build 8s |
| JVM calculation/logic regression | 37 passed, zero failures/errors (five XML receipts in test-results) |
| Device regression | 25 passed in final publication run (21.852 s), using direct upgrade installs |
| Lint debug and release | Both passed; each reports 0 errors and 67 warnings |
| Firebase configuration/preflight | 6 tests passed; both package configurations matched kinetiq-10b98 |
| Live deployed Firebase | 1 passed: authenticated upload/download, conflict resolution, tombstones and owner-rule denial, one real account/two isolated stores |
| Live Open Food Facts | HTTP 200 barcode nutrition and HTTP 200 search/five parsed products; earlier timeout/503 probes also recorded |
| Food calculations | Six new portion cases cover 75 g, kg conversion, source-weighted roti/cup, 250 ml/litre references/density, 1.5 servings and unknown recipe micronutrients; unmeasured cup conversion is rejected |
| Offline data/art | Food aliases/search/snapshot tests and exercise metadata/537 SVG decode/legacy identity tests pass inside the 25-case suite |
| Actual app UI tour | 1 passed, 12 reviewed real screenshots on isolated records (41.548 s) |
| Installed production smoke | Home/Food/Train/Activity/Insights passed; food and source-illustrated exercise searches passed in airplane mode; connectivity restored |
| Route proof | Four JVM + four device cases pass; 15 actual PNGs show four shapes/three formats, tile-free details and no-track/privacy cases |
| APK identity and alignment | Both packages/codes/certificates verified; ZIP and native arm64/x86_64 ELF 16 KB alignment checks passed |

Evidence: `test-results/offline-full-device-tests.txt`, `offline-live-firebase.txt`, `live-food-api.txt`, `offline-production-smoke.json`, `offline-release-dry-run.log`, `offline-release-publish.log`, lint reports and XML results. These are distinct groups, not an inflated total that counts repeated runs as new cases.

## Release, update and retained data

Published **2.4.0-beta.1 / code 7 / v7-beta**: https://github.com/vaishnavg121/kinetiq-releases/releases/tag/v7-beta . Stable remains code 5.

| APK | Package | Bytes | SHA-256 |
|---|---|---:|---|
| KINETIQ.apk | com.vanta | 85127953 | `75c787bf8a57254e712e0ef0597f11787e5822217ac00fd53a73088906c63737` |
| KINETIQ-debug.apk | com.vanta.debug | 108510785 | `cebe2923357d1383ac9ff8738c4cd504e5c7212d3f88170f11a90235754baaf3` |

Production certificate SHA-256: `ba14769d4bc881657350f76264525debdd75ec6c28f3485a2275154078c2fa3f`. Debug certificate SHA-256: `5667e8fe0c42b0b45c10c335b61cf22092cb30e207ebe44eaabb2bcb4ac6c37e`. Permanent keys are preserved outside Git. Local delivery copies are `dist/KINETIQ-beta.apk` and `dist/KINETIQ-debug-beta.apk`.

The release script's **dry run passed without publication and restored version.properties**. The actual run revalidated both variants and 25 device cases, pushed version commit **78a4bbb**, uploaded draft assets, downloaded both APKs and compared hashes, then published. BrowserOS Neo independently showed the public pre-release, both APK links, update metadata, README, screenshot links and public presentation commit **c5bf3de**.

**Actual production upgrade 6→7 passed through Settings → About → Beta → Check for Updates → Download & Install.** Android's Update confirmation opened; Play Protect scanned the app, reported “This app looks safe”, and installation completed after its Install confirmation. No ADB production installation was substituted for this flow. Both installed APK hashes match the published files (`offline-native-upgrade.json`, `offline-installed-and-data.json`).

Before/after exports compare every original row across all 16 production application tables and favorite-food IDs, with no missing original rows. The current production profile contained seeded definitions and no logged food/workout/GPS sessions; its exercises grew from 10 to 1,074 without changing the original ten. Separately, the populated historical debug Guest database retained every original row: four food entries, one workout/set, three GPS sessions/272 points, recipes, meals, templates, water, settings and measurements. The comparison does not imply a populated production profile was tested. Private backup contents were not committed; QA exports were removed from the device Downloads folder. Room remains schema 3.

The API 37 emulator is left running on production KINETIQ Home. Connectivity was restored after offline tests.

## Security, publication and remaining acceptance

A bounded text-pattern audit covers historical Git blobs and current tracked/unignored text. No credential-pattern matches remained after reviewing environment/property reads; this is not an exhaustive secret guarantee or OCR audit. Older authenticated screenshots/device-derived fixtures remain in source history. Therefore the existing source repository stays private, without history rewriting or force-push. Reviewed new screenshots, provenance, personal origin README and signed binaries are published in the existing public distribution repository.

Keyed USDA online lookup was not exercised; the tested online provider was Open Food Facts. Physical GNSS accuracy, OEM background limits, real Health Connect sensor data, physical barcode optics, a second real Firebase account/device, and live Spotify authentication/playback remain unverified. The user could not log into Spotify; no live playback success is claimed. Source exercise technique has not been medically validated. Full pose coverage, comprehensive regional dishes and dedicated yoga/Pilates sequences are unfinished content coverage, not claimed completed features.

Source: https://github.com/vaishnavg121/kinetiq (private). Public presentation/distribution: https://github.com/vaishnavg121/kinetiq-releases . Implementation checkpoint: `acfb237`; route checkpoint: `00136d8`; pre-change checkpoint: `f1fbd7f`.

## Installation and future releases

On a phone, open the Beta release and install KINETIQ.apk (`com.vanta`), allowing browser installation when Android asks. For an existing debug installation use KINETIQ-debug.apk (`com.vanta.debug`). Do not uninstall first; these packages have separate journals. Future updates: Settings → About → Beta → Check for Updates → Download & Install, then approve Android's installer. Stable remains separate; changing channels never downgrades installed versions.

From a clean, pushed default checkout on the signing computer, validate with `.\scripts\Publish-Release.ps1 -Channel Beta -VersionName <next-version> -NotesFile release-notes.md -DryRun`. Omit `-DryRun` to publish after review. The script allocates an increasing global code, runs build/tests/lint, verifies permanent certificates/package/size/hash/alignment, and verifies downloaded GitHub APKs before publishing. Signing files remain outside Git.

Public visual evidence: [route exports and tile-free detail proof](docs/route-proof/) and [installed production APK in airplane mode](docs/production-proof/). Main screens are under [docs/assets](docs/assets/). Private backup contents and historical personal screenshots are not published.

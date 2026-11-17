# KINETIQ 2.8.0-beta.2 verification

## Verified delivery

Published **2.8.0-beta.2 / code 14 / v14-beta**: [release and APKs](https://github.com/vaishnavg121/kinetiq-releases/releases/tag/v14-beta). Source implementation: `96285c1`; release commit: `75f49bd823a7b67c9cea6cd8b93b0d4369b55b4a`. Checkpoint `checkpoint-readable-home-v13` and previous releases remain available. No history was rewritten.

| Check | Actual result |
|---|---|
| JVM calculation/model tests | 104 passed, zero failures/errors |
| Python portions/configuration checks | 11 passed |
| Delivered code-14 device regression | 68 passed, zero failures |
| 720 × 1600 / 150% text | Four candidate checks passed: energy sources/navigation, exact entry edits, hourly/year history, all four accent themes |
| Final code-14 main-screen/theme tours | Two passed; actual QA screen captures saved |
| Debug and release lint | Zero errors/fatal issues; debug: 67 warnings; release: 67 warnings |
| APK identity and alignment | Packages, codes, permanent certificates and 64-bit 16 KB native alignment verified |
| Hosted distribution | Four public assets downloaded and matched to local bytes; both installed APK hashes match |
| Actual production update | 13 → 14 through the app and Android installer; no production ADB install |
| Data preservation | All original rows/columns in 16 exported tables and favourite-food IDs unchanged, schema 5; no added food entries |
| Production smoke | Six main screens, local banana search and quantity-1.0 defined-portion form; no test entry saved |

Repeated scale/tour checks are separate verification groups, not additional unique regression cases. Populated logging, entry edits, chart interactions and provider-source scenarios use isolated QA stores. The production comparison covers the current profile.

| Package | Bytes | SHA-256 |
|---|---:|---|
| com.vanta | 85,907,112 | `c538991ad6e892793b532029b0cafc1229d65a8cc8e38915632422480057280c` |
| com.vanta.debug | 109,298,879 | `07a2e0e622526c6170a98fe3e7271d5d8d19fa3357e453c8d25408aac7b1212e` |

Permanent signing certificate SHA-256:

- `com.vanta`: `ba14769d4bc881657350f76264525debdd75ec6c28f3485a2275154078c2fa3f`
- `com.vanta.debug`: `5667e8fe0c42b0b45c10c335b61cf22092cb30e207ebe44eaabb2bcb4ac6c37e`

Local APKs: `dist/KINETIQ.apk` and `dist/KINETIQ-debug.apk`; matching Beta aliases are retained. The complete review gallery retained with the private source project includes the rounded cards, full decimal values, main screens and themes. Normal-size images were refreshed on delivered code 14. The 150%-text image comes from the code-13 pre-release candidate with the same implementation, checked before release. Production screenshots and raw before/after backups stay private and excluded from Git.

Evidence: `test-results/readable-release-verification.json`, `readable-native-update.json`, `readable-production-upgrade.json`, `readable-home-production-smoke.json`, `readable-release-device.txt`, `readable-large-text.txt`, and `readable-showcase-device.txt`.

Physical GNSS/Health Connect accuracy, camera optics, OEM background behavior, measured battery drain, live Spotify login/playback, a fresh second-device Firebase sync and keyed USDA online lookup remain unverified. Existing offline data coverage limits remain documented. This UI revision adds no new external integration or dataset.

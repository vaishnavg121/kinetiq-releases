# KINETIQ 2.8.0-beta.1 verification

## Verified delivery

Published **2.8.0-beta.1 / code 13 / v13-beta**: [Public release and APKs](https://github.com/vaishnavg121/kinetiq-releases/releases/tag/v13-beta). Source implementation: `a29c212`; release commit: `c1b157fe1d3ab208f19878a471c58093671dba76`. The checkpoint and previous Beta remain available; no history was rewritten or force-pushed.

| Check | Actual result |
|---|---|
| JVM calculation/model regression | 103 passed, zero failures/errors |
| Python portions/Firebase configuration checks | 11 passed |
| Final code-13 device regression | 68 passed, zero failures |
| Small screen / 150% text | Seven candidate checks passed; both date-navigation cases passed again on final code 13 |
| Final code-13 main-screen/theme tours | Two passed; all four accents captured. AMOLED preference persistence is covered by device regression |
| Debug and release lint | Zero errors/fatal issues; 67 warnings per variant, primarily dependency-update and API-style advisories |
| APK identity | Both packages, version names/codes and permanent signing certificates verified |
| Distribution | All four public release assets downloaded and compared with local files; both installed APK hashes match |
| Native alignment | ZIP/native 64-bit 16 KB alignment verified by the publisher |
| Actual production upgrade | 12 → 13 through the app's Download & Install flow and Android installer |
| Data retention | All original rows and columns in the 16 exported production tables, and favourite-food IDs, are unchanged; schema 5 retained |
| Production smoke | Six main screens plus local food search / quantity-1.0 form checked without saving a test food; left on Home |

The production comparison covers the current profile. Populated logging, edits, backup round trips and synthetic provider scenarios use isolated account stores on the actual emulator. They are not claims of physical sensor measurements or fresh two-device cloud transport.

| Package | Bytes | SHA-256 |
|---|---:|---|
| com.vanta | 85,907,112 | `6d18f11d36910a39908bdb2ca83c3f4fab432167374ed27ea1c4dc61cf0ebf83` |
| com.vanta.debug | 109,589,370 | `9a4b5d2bfaad66cb9058a7305da24074c8e47148dd45db1c8aa851434fb6584f` |

Permanent signing certificate SHA-256:

- `com.vanta`: `ba14769d4bc881657350f76264525debdd75ec6c28f3485a2275154078c2fa3f`
- `com.vanta.debug`: `5667e8fe0c42b0b45c10c335b61cf22092cb30e207ebe44eaabb2bcb4ac6c37e`

Installable local copies are in `dist/KINETIQ.apk` and `dist/KINETIQ-debug.apk`; Beta aliases match. The complete review gallery is retained with the private source project contains the main screens, energy details, portions and themes. The 150%-text screenshots were captured from the pre-release candidate; the final navigation code was separately checked at the same scale. Production screenshots are kept locally under `preview/private-production/` and excluded from Git/public assets. Raw before/after backups remain private in `.bootstrap/home-production/`.

Evidence: `test-results/home-release-verification.json`, `home-production-upgrade.json`, `home-production-smoke.json`, `home-release-device.txt`, `home-large-text-device.txt`, `home-code13-large-text.txt`, and `home-showcase-device.txt`. Repeated scale/tour runs are separate verification groups, not additional unique regression cases.

Opening a dated chart reading now resets the daily view to its top. Calculation/source explanations expand on demand, and evidence is paged without dropping contributions. Gradle 8.11.1 launches with installed Java 21; the Android Studio local Gradle JDK also points to Java 21.

Physical GNSS/Health Connect accuracy, camera optics, OEM background behavior, measured battery drain, live Spotify login/playback, a fresh second-device Firebase sync, and keyed USDA online lookup remain unverified. Offline USDA foods and the shared food forms are verified. Source exercise pose coverage and regional-food coverage retain the existing documented limits. No new sensor, music or account success is fabricated. BrowserOS Neo MCP tools were unavailable in this session; official source references and the GitHub API/CLI were used for source/release checks.

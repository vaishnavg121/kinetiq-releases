# Offline content provenance

Snapshot/preprocessing date: 5 November 2026. Catalogs are separate from personal Room records.

## Food: 13,118 entries, 18,935,808 bytes

USDA FoodData Central SR Legacy (April 2018) contributes 7,687 retained foods; FNDDS 2021–2023 (published 31 October 2024) contributes 5,431. Duplicate normalized descriptions and rows missing energy/protein/carbohydrate/fat were excluded. Missing micronutrients remain null. Foods are normalized per 100 g, with source-specific household weights. Fluid-ounce weights are converted to density only for explicitly fluid food descriptions, using the US fluid ounce (29.5735295625 ml).

- [Official downloads](https://fdc.nal.usda.gov/download-datasets/)
- [USDA licensing statement](https://fdc.nal.usda.gov/api-guide/#bkmk-9): public domain, CC0 1.0. USDA requests attribution; it is shown in food source labels.
- Machine-readable provenance/checksums: `app/src/main/assets/catalog/foods-manifest.json`.
- Rebuild: `python tools/build_offline_foods.py --input-dir .bootstrap/datasets`.

The full raw downloads are not bundled. The packaged SQLite catalog includes a Unicode FTS4 index; installed catalog filenames use its content hash, so future catalog changes install alongside user data rather than modifying food definitions used by diaries. A food selected for logging is copied into Room with its nutrient/serving snapshot. No existing diary or personal food is replaced by a catalog update.

Indian coverage includes source entries for paneer, idli, dosa, palak paneer, naan and chapati/roti, plus pulses/staples and romanized aliases. It is **not** a comprehensive regional Indian recipe database. NIN/IFCT was evaluated but is not redistributed because compatible redistribution permission was not established. No precise values were invented for absent regional preparations. Use weighed recipes/custom foods for those dishes. Historical branded entries are dated composition records, not a promise about a current product's formulation.

Open Food Facts is optional online lookup/cache only, not part of the bundled USDA catalog. Its [database terms](https://world.openfoodfacts.org/terms-of-use) are ODbL/DbCL; product images have separate CC BY-SA terms. Search runs on explicit request, with caching, cancellation and spacing below the published [10 searches/minute limit](https://openfoodfacts.github.io/openfoodfacts-server/api/#rate-limits). The app identifies itself with a User-Agent. No USDA key is bundled; a personal key is encrypted locally and excluded from backups/cloud sync.

## Exercises: 1,064 distinct catalog entries

- **Everkinetic / Greg Priday**: 287 retained movements and 537 unmodified vector assets, CC BY-SA 4.0. [Repository](https://github.com/everkinetic/data), [license](https://github.com/everkinetic/data/blob/main/LICENSE.md). Pinned revision `6f3ce86eb79b17e7bbaf588b7960149725bc8fc7`.
- **yuhonas/free-exercise-db**: 777 additional metadata records under the [repository's Unlicense](https://github.com/yuhonas/free-exercise-db). Revision is pinned in `exercises-manifest.json`. Its photographs are **not** bundled: the maintainer's [image-rights discussion](https://github.com/yuhonas/free-exercise-db/issues/2) leaves their provenance uncertain.
- 96 matching/duplicate names were merged. Five records lacking technique instructions were excluded; the manifest lists them. Existing legacy exercise IDs, custom records, PRs and workout snapshots are preserved.
- The normalized collection and Everkinetic-derived instructions retain CC BY-SA 4.0 terms; individual free-exercise-db metadata remains available under the Unlicense. Attribution, license and source are shown in exercise details.
- Original schematic muscle maps are KINETIQ code, licensed with the application code. They identify targets and **do not claim to depict movement positions**.

**Visual coverage:** 268 catalog movements have exact source pose artwork; 796 have original target-muscle diagrams. Every built-in selection row has an offline visual. Full starting/ending pose coverage is incomplete and is not disguised with unrelated artwork. Source descriptions/difficulty have not been clinically reviewed. Missing difficulty is displayed as unrated. General safety cues are informational; no rehabilitation or medical validation is claimed.

The catalog covers strength, stretching, power/plyometric movements, functional/strongman and cardio. It does not yet offer a dedicated verified yoga/Pilates sequence library. Custom exercises support user-selected targets, equipment, category, notes and tracking modes.

Rebuild metadata: `python tools/build_offline_exercises.py`. Fetch pinned art: `python tools/fetch_exercise_art.py`. All asset Git blob checksums are verified during ingestion; instrumentation decodes every bundled SVG and asserts visible artwork. Source URLs/licenses and counts are in the manifest. Dataset/art licenses do not relicense unrelated application code or the Spotify SDK.

Public provenance copies: [food manifest](manifests/foods-manifest.json), [exercise manifest](manifests/exercises-manifest.json), [USDA notice](licenses/USDA-CC0-NOTICE.txt), [Everkinetic license](licenses/everkinetic-CC-BY-SA-4.0.txt), [metadata license](licenses/free-exercise-db-Unlicense.txt). Pinned upstream sources above provide the original datasets and SVG artwork.

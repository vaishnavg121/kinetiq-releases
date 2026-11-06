# Clearer food and exercise choices

Released in [KINETIQ 2.4.0-beta.2 / code 8](https://github.com/vaishnavg121/kinetiq-releases/releases/tag/v8-beta).

Food and exercise pickers open on Recent or Favorites. If there is no recent history, saved favorites appear first. With neither, a short empty state invites a search. Typing searches the full library; clearing restores the selected saved tab.

Selection tiles show a readable name, one short summary and a favorite star. Food summaries show calories and the reference portion; exercises show their primary target/equipment and existing offline illustration. Full nutrition, technique and source information stays on detail screens. Extra search filters and community tools are tucked away. Saved meal/workout contents expand on request.

Both signed APKs built successfully. The release regression passed 37 JVM cases and 28 emulator cases. Three isolated picker behavior tests also passed with Android text enlarged to 150%; the original setting was restored. Both lint variants report zero errors and 67 warnings. The publisher downloaded both hosted APKs and verified their hashes before publication.

[Reviewed screenshots](docs/assets/). These images use isolated local QA records; the London route is simulated. They contain no personal account or production fitness records. Detailed private-profile checks and production screenshots are kept local/private.

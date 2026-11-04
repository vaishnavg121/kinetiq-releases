# KINETIQ Android updates

Signed APKs and public update metadata only. Application source and signing keys are kept separately.

## Install on your phone

- [Production APK — com.vanta](https://github.com/vaishnavg121/kinetiq-releases/releases/latest/download/KINETIQ.apk)
- [Existing debug app upgrade — com.vanta.debug](https://github.com/vaishnavg121/kinetiq-releases/releases/latest/download/KINETIQ-debug.apk)
- [Release notes and previous versions](https://github.com/vaishnavg121/kinetiq-releases/releases)

If your existing app version ends in -debug, choose the debug APK to preserve that installation. The production and debug packages have separate journals. Never uninstall or clear data to upgrade. A legacy app without the updater needs this initial installation once; future updates download inside KINETIQ.

After installing, use Settings → About → Check for Updates. Stable receives Stable releases; Beta receives both channels. Android asks for permission and installation consent. KINETIQ verifies the APK checksum, package, newer version and installed signing certificate before opening the system installer.

No GitHub account is needed to download public releases. No subscription or paid update service is used. GitHub availability and public API rate limits apply.

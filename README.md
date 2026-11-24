# Played Store

Native Android app-store starter built with Kotlin and Jetpack Compose.

## Included
- F-Droid and IzzyOnDroid repository catalogue indexing.
- Duplicate package-name merging, choosing highest version and repository priority.
- HTTPS APK downloads with SHA-256 verification for F-Droid / IzzyOnDroid.
- Optional APKCube API connection using each user's own API key.
- APKCube lookup/download only for package IDs already present in the F-Droid / IzzyOnDroid catalogue.
- APKCube APK download checksum verification and Android installer handoff.
- Google Play listing links only; no anonymous direct Google Play APK API.

## APKCube notes
- Create and manage your own API key at APKCube. Do not share it in chat or commit it to source control.
- The key is held in app memory only and is not written to disk. Each user must supply their own key.
- The API's `/me` check is free. Looking up versions costs 1 credit. Downloading a build costs 10 more credits.
- Played Store does not automatically request a fetch, because that costs another 10 credits.
- This integration only downloads a single `.apk`. If APKCube's newest build is `.apks` or `.xapk`, this version reports that split-bundle installation is not yet supported.
- APKCube recommends a server-side proxy for public apps so API keys never ship in the client. For a shared/public release, add a controlled backend proxy rather than using a common key in the APK.

## Important limitations
- This source project is not itself a compiled APK.
- Google Play does not offer a public anonymous API for arbitrary app downloads.
- Repository signature verification is not implemented. SHA-256 comparison detects transfer/index mismatches but does not independently authenticate the repository index.
- APKCube's API and downloads are subject to its own terms, availability, and credit balance.
- Android may require enabling "Allow from this source" for Played Store.

## Build
The included GitHub Actions workflow builds a debug APK on pushes to `main` and on manual workflow dispatch. Download the `PlayedStore-debug-apk` artifact from the workflow run.

For local builds, open the project in Android Studio with Android SDK 35 and JDK 17, then select **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

## Repositories
- F-Droid: https://f-droid.org/repo/
- IzzyOnDroid: https://apt.izzysoft.de/fdroid/repo/
- APKCube API: https://apkcube.com/docs/api

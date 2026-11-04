# IMovie — Movie Android App

A native **Kotlin Android** movie and TV discovery application developed by [RedVelvet-Team](https://github.com/RedVelvet-Team/IMovie).

> This is an attributed portfolio fork. Ali Osama reports participating with teammates; specific personal features are not assigned here because the inspected history did not resolve them to this account. Project capabilities below describe the team codebase.

## Capabilities represented in the code

- Movie and TV browsing, multi-search and genre-based discovery.
- Movie, TV, season, episode and actor detail requests.
- Cast, images, recommendations and review retrieval.
- TMDB authentication/guest sessions and account details.
- Favorites, watchlists, ratings and custom-list integrations.
- Compose screens and ViewModels for search, details and library flows.

These capabilities are supported by service endpoints and presentation code. Live API behavior and every user flow have not been verified end to end. Review retrieval is present; this README does not claim review authoring, full-movie streaming or other unverified features.

## Stack and architecture

Kotlin, Jetpack Compose, Coroutines, Retrofit/OkHttp, Gson, Room, Hilt, DataStore, Paging and Firebase integrations.

| Module | Responsibility |
| --- | --- |
| `app` | Android entry point and dependency wiring |
| `ui` / `viewmodels` | Compose presentation and screen state |
| `usecase` / `entities` | Use cases, repository contracts and domain models |
| `repository` | Repository implementations, DTOs and data-source contracts |
| `remote` / `local` / `datastore` / `firebase` | Network, database, preferences and Firebase adapters |
| `buildSrc` | Shared build configuration |

The active modules are declared in `settings.gradle.kts`; other scaffold directories are not evidence of additional implemented layers.

## Setup

**Requirements:** Android Studio, JDK 17, Android SDK 33, and an Android 7.0+ device/emulator (minimum SDK 24).

```sh
git clone https://github.com/aliosama990/IMovie.git
cd IMovie
git checkout develop
```

Open the repository in Android Studio and let it create the SDK path in `local.properties`. Add the properties consumed by the Gradle scripts, retaining the quotes because their values become generated Java string literals:

```properties
apikey="YOUR_TMDB_API_KEY"
baseUrl="https://api.themoviedb.org/3/"
```

The property is **`apikey`**, not `api_key`. The interceptor sends it to TMDB as the `api_key` query parameter. Keep local configuration and credentials out of version control.

Sync Gradle, select the `app` run configuration and launch a device/emulator. Firebase-dependent flows may require compatible Firebase project configuration and services.

## Build and checks

```sh
./gradlew :app:assembleDebug
./gradlew test
```

Use `gradlew.bat` on Windows. Connected instrumentation tests require an emulator/device. These commands are documented entry points, not a claim of a successful build in this documentation environment.

## Attribution and license

Original project and history: [RedVelvet-Team/IMovie](https://github.com/RedVelvet-Team/IMovie). Original contributors retain credit.

The repository's [LICENSE](LICENSE) is **Apache License 2.0**. The former README's MIT badge conflicted with that file and has been corrected in this fork. The license file and application code remain unchanged.

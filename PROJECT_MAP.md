# PROJECT MAP

- Tech Stack: Kotlin 2.1.0, Jetpack Compose, Room 2.6.1, DataStore Preferences 1.1.1, Supabase 3.1.1 (Postgrest, Auth, Realtime), Ktor Client, Coroutines & Flow.
- Entry Point: app/src/main/java/com/example/anhpannt/MainActivity.kt

## 1. Modules
- app/build.gradle.kts : App build config, dependency declarations for Room, DataStore, Compose, Supabase.
- gradle/libs.versions.toml : Version catalog for dependencies and build plugins.
- app/src/main/AndroidManifest.xml : Android manifest file declaring INTERNET permission and MainActivity.
- app/src/main/java/com/example/anhpannt/MainActivity.kt : Application entry point with Compose scaffold.
- app/src/main/java/com/example/anhpannt/data/ : Package placeholder for database, datastore, models and sync logic.
- app/src/main/java/com/example/anhpannt/ui/ : Jetpack Compose UI components and theme setup.

## 2. Core Data/State Flow
- Room DB: Local single source of truth for offline note caching and CRUD operations.
- Supabase Client: Cloud sync target for backing up and fetching remote notes.
- Conflict Resolution: Timestamp-based (Last-Write-Wins) check between local updated_at and remote updated_at.
- DataStore Preferences: User preferences store for theme, sync switches, and last sync timestamp.
- ViewModel & StateFlow: Exposes reactive UI state to Compose screens.

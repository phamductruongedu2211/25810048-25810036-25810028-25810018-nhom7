# PROJECT MAP

- Tech Stack: Kotlin 2.1.0, Jetpack Compose, Navigation Compose 2.8.8, Room 2.7.0, DataStore Preferences 1.1.1, Supabase 3.1.1 (Postgrest, Auth, Realtime), Ktor Client, Coroutines & Flow.
- Entry Point: app/src/main/java/com/example/anhpannt/MainActivity.kt

## 1. Modules
- app/build.gradle.kts : App build config, dependency declarations for Room, DataStore, Compose, Supabase.
- gradle/libs.versions.toml : Version catalog for dependencies and build plugins.
- app/src/main/AndroidManifest.xml : Android manifest file declaring INTERNET permission and MainActivity.
- app/src/main/java/com/example/anhpannt/MainActivity.kt : Application entry point hosting AppNavHost with dynamic locale configuration.
- app/src/main/java/com/example/anhpannt/data/Note.kt : Unified Note model and Room SQLite entity.
- app/src/main/java/com/example/anhpannt/data/RemoteNote.kt : Serializable DTO mapping to Supabase public.notes table with user_id support.
- app/src/main/java/com/example/anhpannt/data/NoteDao.kt : DAO interface with reactive Flow and snapshot queries.
- app/src/main/java/com/example/anhpannt/data/AppDatabase.kt : Room database singleton instance.
- app/src/main/java/com/example/anhpannt/data/SupabaseProvider.kt : Supabase client singleton configured with Postgrest and Auth.
- app/src/main/java/com/example/anhpannt/data/NoteRepository.kt : Repository coordinating offline Room CRUD, Supabase Auth and user-scoped two-way sync.
- app/src/main/java/com/example/anhpannt/data/UserPreferences.kt : DataStore store for onboarding, user session, language, and auto-sync configuration.
- app/src/main/java/com/example/anhpannt/ui/NoteViewModel.kt : ViewModel exposing reactive StateFlows, Auth operations, and sync dispatches.
- app/src/main/java/com/example/anhpannt/ui/AppNavigation.kt : Route definitions and AppNavHost composable.
- app/src/main/java/com/example/anhpannt/ui/screens/ : Flat screen composables (OnboardingScreen, NoteListScreen, NoteEditScreen, SettingsScreen, AboutScreen, AuthDialog).
- app/src/main/java/com/example/anhpannt/ui/theme/ : Color, Type, and Theme definitions.

## 2. Core Data/State Flow
- Room DB: Local single source of truth for offline note caching and CRUD operations.
- Supabase Provider: Remote cloud backend with Auth (Email/Password) and public.notes storage.
- Two-way User-Scoped Sync: Last-Write-Wins comparison of updatedAt timestamps strictly for the authenticated user's notes.
- DataStore Preferences: User preferences store for onboarding completion, user session, language selection, and auto-sync toggle.
- ViewModel & StateFlow: Exposes reactive UI state to Compose screens with animated sync indication and login dialog triggers.

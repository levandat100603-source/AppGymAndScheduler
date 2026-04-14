# Project Guidelines

This workspace contains two projects:
- Flutter mobile app in `flutter_gym_scheduler/`
- Laravel backend in `gym-scheduler-backend/`

## Architecture

- Flutter app uses a layered flow: screens/widgets -> providers -> services -> models.
- Primary Flutter structure:
  - `flutter_gym_scheduler/lib/models/`
  - `flutter_gym_scheduler/lib/services/`
  - `flutter_gym_scheduler/lib/providers/`
  - `flutter_gym_scheduler/lib/screens/`
- Laravel backend follows standard Laravel boundaries:
  - API routes in `gym-scheduler-backend/routes/api.php`
  - Controllers in `gym-scheduler-backend/app/Http/Controllers/Api/`
  - Models in `gym-scheduler-backend/app/Models/`
  - Migrations in `gym-scheduler-backend/database/migrations/`

## Build and Test

Run commands from the correct project directory.

### Flutter (`flutter_gym_scheduler/`)

- Install deps: `flutter pub get`
- Static analysis: `flutter analyze`
- Tests: `flutter test`
- Run app (example): `flutter run -d android`

### Backend (`gym-scheduler-backend/`)

- Install PHP deps: `composer install`
- Install frontend deps: `npm install`
- Generate app key (first setup): `php artisan key:generate`
- Run migrations: `php artisan migrate`
- Backend tests: `php artisan test`
- Local full dev stack: `composer run dev`
- Frontend assets build: `npm run build`

## Conventions

- Keep changes scoped to the target project unless integration requires cross-project edits.
- Prefer existing patterns before introducing new architecture.
- For Flutter state changes, update providers/services instead of pushing business logic into screens.
- For backend API changes, keep route/controller/model alignment consistent with current folders.
- Use Vietnamese for user-facing copy and messages where existing code/docs already do so.

## Environment and Pitfalls

- Flutter requires Firebase native config files:
  - Android: `flutter_gym_scheduler/android/app/google-services.json`
  - iOS: `flutter_gym_scheduler/ios/Runner/GoogleService-Info.plist`
- Update API base URL in `flutter_gym_scheduler/lib/services/api_service.dart` when backend host changes.
- Ensure Stripe keys are configured before testing payments.
- Backend depends on environment values in `gym-scheduler-backend/.env` (copy from `.env.example` if needed).

## Documentation (Link First)

Prefer linking these docs instead of duplicating details:
- `flutter_gym_scheduler/README.md`
- `flutter_gym_scheduler/ARCHITECTURE.md`
- `flutter_gym_scheduler/DATABASE.md`
- `flutter_gym_scheduler/INSTALLATION_CHECKLIST.md`
- `flutter_gym_scheduler/PROJECT_SUMMARY.md`
- `flutter_gym_scheduler/SETUP_GUIDE.yaml`
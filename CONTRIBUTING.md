# Contributing to MediQueue Mobile

Thank you for contributing to MediQueue.

This project uses:

- Flutter
- MVVM architecture
- Riverpod
- Dio
- SignalR
- Git Flow branching strategy

To keep development smooth between three developers, please follow this guide.

---

## Project Architecture

This mobile application follows:

`Model -> View -> ViewModel (MVVM)`

Folder structure:

```text
lib/
  core/
  shared/
  features/
  main.dart
```

Each feature should contain:

```text
features/
  feature_name/
    models/
    views/
    viewmodels/
    services/
```

---

## Branch Strategy

Branches:

- `main`
- `develop`
- `feature/patient-ui`
- `feature/staff-ui`
- `feature/integration`

### Branch usage

- `main`: Stable, demo-ready code only.
- `develop`: Shared testing branch.
- `feature/patient-ui`: Patient app screens.
- `feature/staff-ui`: Staff dashboard screens.
- `feature/integration`: API services, models, and SignalR integration.

---

## Developer Responsibilities

- Developer 1: `feature/patient-ui`
- Developer 2: `feature/staff-ui`
- Developer 3: `feature/integration`

Only work in your assigned branch.

---

## Before You Start

Always pull the latest `develop` first:

```bash
git checkout develop
git pull origin develop
```

Then switch to your branch:

```bash
git checkout feature/your-branch
```

Merge latest `develop` into your branch:

```bash
git merge develop
```

---

## Coding Rules

### Views

Views should only contain UI.

Do **not**:

- call APIs directly
- write business logic
- parse JSON

Views should:

- display data
- call ViewModel methods
- react to state changes

### ViewModels

ViewModels should:

- manage state
- call services
- handle loading
- handle errors

ViewModels must **not** contain widget code.

### Services

Services should:

- call backend APIs
- handle SignalR
- parse responses

### Models

Models should:

- represent API data
- be immutable where possible

---

## Commit Message Format

Use prefixes like:

- `feat: add patient check-in screen`
- `fix: resolve queue refresh bug`
- `refactor: clean queue service`
- `ui: improve staff card layout`

Example:

```bash
git commit -m "feat: add queue position screen"
```

---

## Pull Request Process

1. Push your branch:

   ```bash
   git push origin feature/your-branch
   ```

2. Open a pull request into `develop`.
3. Another team member reviews.
4. Merge into `develop`.
5. Test in `develop`.
6. Merge `develop` into `main` before demo.

---

## Rules

- Never push directly to `main`.
- Never force-push shared branches.
- Keep commits small.
- Pull latest changes often.
- Test before pushing.
- Communicate major changes with the team.

---

## Handling Merge Conflicts

If conflicts happen:

```bash
git checkout your-branch
git pull origin develop
git merge develop
```

Resolve conflicts, then:

```bash
git add .
git commit
```

---

## Daily Workflow

Morning:

- Pull latest `develop`
- Review tasks
- Work on your branch

Mid-session:

- Push progress

End of session:

- Merge into `develop`
- Verify app still runs

---

## Important MVVM Rule

Correct flow:

`View -> ViewModel -> Service -> API`

Never:

`View -> API directly`

---

## Running the Project

Install dependencies:

```bash
flutter pub get
```

Run app:

```bash
flutter run
```

Generate files:

```bash
flutter pub run build_runner build --delete-conflicting-outputs
```

---

## Demo Safety Rule

- The `develop` branch should always compile.
- The `main` branch must always be demo-safe.

---

## Emergency Rule

If something breaks:

1. stop merging immediately
2. fix `develop` first
3. then continue

---

## Contact Team

If unsure, ask before merging.


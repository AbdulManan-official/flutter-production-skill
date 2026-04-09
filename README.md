# 🚀 Flutter Production Skill

> A comprehensive, production-grade reference skill for Flutter development — covering architecture, state management, security, CI/CD, monetization, and 40+ advanced topics.

---

## 📖 About

This skill is designed to guide AI assistants (and developers) toward writing **clean, scalable, ship-ready Flutter code** — not toy examples. Every pattern, snippet, and decision guide here reflects real-world production experience across Play Store and App Store deployments.

Whether you're building a solo utility app or a large-scale enterprise product, this skill enforces the right architecture, the right patterns, and the right tools from day one.

---

## 🎯 What This Skill Covers

This skill triggers on **any** Flutter question across all of these domains:

| Category | Topics |
|----------|--------|
| **Architecture** | Clean Architecture, MVVM, MVC, Feature-first |
| **State Management** | GetX, Riverpod, BLoC, Provider |
| **UI & Design** | Layouts, responsive design, theming, animations, Custom Painter |
| **Navigation** | GoRouter, deep linking, dynamic links |
| **Networking** | REST APIs, Dio, serialization, caching, rate limiting |
| **Backend** | Firebase, Supabase, real-time, MQTT, Socket.IO, SignalR |
| **Authentication** | OAuth, biometric (fingerprint/Face ID), FCM push notifications |
| **Storage** | Local storage, caching, offline support, Hive, SQLCipher, AES |
| **Security** | Code obfuscation, SSL pinning, `flutter_secure_storage` |
| **Performance** | Isolates, DevTools, list virtualization, startup time |
| **Monetization** | AdMob, Yandex Ads, in-app purchases, RevenueCat, Stripe, PayPal |
| **Localization** | ARB files, RTL support, multi-language |
| **Notifications** | FCM, local/scheduled, background, grouped, action buttons |
| **Testing** | Unit, widget, integration tests |
| **CI/CD** | GitHub Actions, Codemagic, Fastlane, app signing |
| **Deployment** | Play Store, App Store, ASO, app size, startup optimization |
| **Device Features** | Camera, GPS, platform channels, background services |
| **Observability** | Logging, Crashlytics, Sentry, Datadog, analytics |
| **Code Quality** | Linting, custom lint rules, metrics, naming conventions |
| **Dart 3** | Records, patterns, sealed classes, switch expressions |
| **UX Patterns** | Skeleton screens, empty states, error states, paywall strategy |
| **Onboarding** | Feature discovery, first-run flows |
| **Modularization** | Melos, internal packages, mono-repo setup |

---

## 📁 Repository Structure

```
flutter-production/
├── SKILL.md                  # Main skill entry point & decision guides
└── references/
    ├── architecture.md
    ├── architecture_advanced.md
    ├── ui.md
    ├── state.md
    ├── navigation.md
    ├── networking.md
    ├── networking_advanced.md
    ├── backend.md
    ├── auth_notifications.md
    ├── storage.md
    ├── security.md
    ├── performance.md
    ├── performance_advanced.md
    ├── monetization.md
    ├── localization.md
    ├── testing.md
    ├── cicd.md
    ├── cicd_advanced.md
    ├── device.md
    ├── observability.md
    ├── quality.md
    ├── quality_advanced.md
    ├── error_feedback.md
    ├── flavors.md
    ├── biometric.md
    ├── lifecycle.md
    ├── payments.md
    ├── file_sharing.md
    ├── local_notifications.md
    ├── notifications_advanced.md
    ├── accessibility.md
    ├── deeplinks.md
    ├── custom_painter.md
    ├── data_sync.md
    ├── analytics_advanced.md
    ├── modularization.md
    ├── ux_states.md
    ├── store_readiness.md
    ├── dart3.md
    ├── force_update.md
    ├── encrypted_storage.md
    ├── realtime_protocols.md
    ├── onboarding.md
    ├── crash_reporting_advanced.md
    └── http_caching.md
```

---

## 🗺️ Topic Reference Map

| Topic | File |
|-------|------|
| Architecture, Folder Structure, DI | `references/architecture.md` |
| Mappers, UseCase Base, Result/Either | `references/architecture_advanced.md` |
| UI, Layouts, Theming, Animations | `references/ui.md` |
| State Management (GetX / Riverpod / BLoC / Provider) | `references/state.md` |
| Navigation, Routing, Deep Linking | `references/navigation.md` |
| Networking, REST, Dio, Serialization | `references/networking.md` |
| Cancellation, Rate Limiting, Versioning | `references/networking_advanced.md` |
| Firebase & Supabase Integration | `references/backend.md` |
| Auth, Push Notifications, Real-time | `references/auth_notifications.md` |
| Local Storage, Caching, Offline | `references/storage.md` |
| Security (Obfuscation, SSL Pinning, Secure Storage) | `references/security.md` |
| Performance & Optimization | `references/performance.md` |
| Isolates, DevTools, List Virtualization | `references/performance_advanced.md` |
| Ads & Monetization (AdMob, IAP, RevenueCat) | `references/monetization.md` |
| Localization, ARB, RTL | `references/localization.md` |
| Testing (Unit / Widget / Integration) | `references/testing.md` |
| CI/CD, Deployment, App Signing | `references/cicd.md` |
| Fastlane, Store Readiness, App Size | `references/cicd_advanced.md` |
| Device Features, Platform Channels, Background | `references/device.md` |
| Logging, Crash Reporting, Analytics | `references/observability.md` |
| Code Quality, Linting, Packages | `references/quality.md` |
| Custom Lint, Metrics, Naming | `references/quality_advanced.md` |
| Error Handling & User Feedback | `references/error_feedback.md` |
| App Flavors & Environments | `references/flavors.md` |
| Biometric Auth (Fingerprint, Face ID) | `references/biometric.md` |
| App Lifecycle & Background Handling | `references/lifecycle.md` |
| Payment Gateways (Stripe, PayPal) | `references/payments.md` |
| File Sharing & Export (PDF, Excel) | `references/file_sharing.md` |
| Local & Scheduled Notifications | `references/local_notifications.md` |
| Notification Actions, Background, Grouping | `references/notifications_advanced.md` |
| Accessibility (Semantics, Contrast, RTL) | `references/accessibility.md` |
| Deep Links & Dynamic Links | `references/deeplinks.md` |
| Custom Painter & Canvas | `references/custom_painter.md` |
| Data Sync, Conflict Resolution, DB Migration | `references/data_sync.md` |
| Remote Config, Feature Flags, A/B Testing | `references/analytics_advanced.md` |
| Modularization, Melos, Internal Packages | `references/modularization.md` |
| UX States — Skeleton, Empty, Error, Paywall | `references/ux_states.md` |
| Store Readiness — App Size, Startup, ASO | `references/store_readiness.md` |
| Dart 3 — Records, Patterns, Sealed Classes | `references/dart3.md` |
| Force Update & In-App Update | `references/force_update.md` |
| Encrypted Local Storage (Hive, AES, SQLCipher) | `references/encrypted_storage.md` |
| Realtime Protocols — MQTT, Socket.IO, SignalR | `references/realtime_protocols.md` |
| Onboarding & First-Run Flows | `references/onboarding.md` |
| Sentry & Datadog Crash Reporting | `references/crash_reporting_advanced.md` |
| HTTP Response Caching — dio_cache_interceptor | `references/http_caching.md` |

---

## ⚙️ Core Principles

Every response guided by this skill follows these non-negotiable rules:

1. **Architecture first** — Layer boundaries are strict. UI never touches business logic.
2. **State management consistency** — Riverpod (default), GetX (utility apps), BLoC (enterprise).
3. **Null safety** — All code is fully null-safe. No suppressions.
4. **No magic strings** — Constants, enums, and code generation everywhere.
5. **Separation of concerns** — UI renders. Controllers manage state. Repositories fetch data.
6. **Error handling** — Every async call uses `Either<Failure, T>` or `Result<T>`.
7. **Security by default** — No secrets in code. `flutter_secure_storage`. SSL pinning on prod.
8. **Performance by default** — `const` constructors everywhere. Profile before optimizing.
9. **Production logging** — Structured logging via `logger`. No `print()` in production.
10. **Testability** — Dependencies are injected. Nothing is instantiated inside widgets.

---

## 🧭 Quick Decision Guide

### Architecture
| Scenario | Choice |
|----------|--------|
| Complex app, team, multiple data sources | Clean Architecture |
| Medium app, solo dev, GetX or Riverpod | MVVM |
| Simple prototype | MVC |
| Large app, independent features | Feature-first + Clean ✅ Recommended |

### State Management
| Scenario | Choice |
|----------|--------|
| New project, testability matters | Riverpod ✅ |
| VPN / utility / solo app | GetX |
| Enterprise, strict event flow | BLoC |
| Simple / legacy migration | Provider |

---

## 🗂️ Recommended Folder Structure

```
lib/
├── core/
│   ├── constants/         # AppColors, AppSizes, AppStrings, AppRoutes
│   ├── errors/            # Failures, Exceptions
│   ├── network/           # DioClient, NetworkInfo, Interceptors
│   ├── services/          # SecureStorageService, AnalyticsService, etc.
│   ├── theme/             # AppTheme, dark/light ThemeData
│   ├── utils/             # Extensions, Helpers, Validators
│   └── di/                # Dependency injection setup
├── features/
│   └── [feature_name]/
│       ├── data/
│       │   ├── datasources/   # Remote & Local data sources
│       │   ├── models/        # DTO models with fromJson/toJson
│       │   └── repositories/  # Repository implementations
│       ├── domain/
│       │   ├── entities/      # Pure Dart entities
│       │   ├── repositories/  # Abstract repository interfaces
│       │   └── usecases/      # Single-responsibility use cases
│       └── presentation/
│           ├── screens/       # Full screen widgets
│           ├── widgets/       # Reusable UI components
│           ├── controllers/   # GetX controllers / Notifiers / Cubits
│           └── bindings/      # GetX bindings (if using GetX)
├── l10n/                  # ARB localization files
├── generated/             # build_runner output (freezed, json, l10n)
└── main.dart
```

---

## 📌 How to Use This Skill

| Situation | Action |
|-----------|--------|
| Writing **any** code | Read the relevant reference file first |
| Choosing packages | Check `references/quality.md` for recommended pub.dev packages |
| Security question | Always read `references/security.md` **fully** |
| Performance issue | Read `references/performance.md` before suggesting solutions |
| Multiple topics in one request | Read **all** relevant reference files |

---

## 🏷️ Suggested Repo Details

| Field | Value |
|-------|-------|
| **Name** | `flutter-production-skill` |
| **Description** | Production-grade Flutter skill with 40+ reference guides covering architecture, state, security, CI/CD, and more |
| **Topics / Tags** | `flutter`, `dart`, `clean-architecture`, `riverpod`, `getx`, `bloc`, `firebase`, `production`, `mobile`, `skill` |

---

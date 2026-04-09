# 🚀 flutter-production.skill

> The most complete Flutter production skill for Claude AI — 45 reference files covering every aspect of building, shipping, and maintaining real-world Flutter apps.

Built by **Abdul** — Flutter Developer at Technosofts, Sialkot 🇵🇰

---

## ⚡ Install in 3 Steps

1. Download [`flutter-production.skill`](../../releases/latest/download/flutter-production.skill)
2. Go to **Claude.ai → Settings → Skills → Upload Skill**
3. Done — Claude now answers every Flutter question at production level

---

## 🧠 What This Skill Does

Once installed, Claude automatically reads the relevant reference file(s) before answering your Flutter questions — giving you **production-grade code**, not toy examples.

**Before this skill:** Generic code snippets, missing error handling, no architecture patterns.

**After this skill:** Clean Architecture, proper DI, null-safe, tested, secure, optimized code — ready to ship.

---

## 📚 45 Topics Covered

### 🏗️ Architecture
| Topic | File |
|-------|------|
| Clean Architecture, MVVM, MVC, Repository, Use Cases, DI | `architecture.md` |
| DTO↔Entity Mappers, UseCase Base Classes, Result/Either | `architecture_advanced.md` |
| Modularization, Melos Monorepo, Internal Packages | `modularization.md` |

### 🎛️ State Management
| Topic | File |
|-------|------|
| GetX (Rx, Workers, Bindings), Riverpod (AsyncNotifier, StreamNotifier), BLoC (Sealed Events, Freezed States), Provider | `state.md` |

### 🎨 UI / UX
| Topic | File |
|-------|------|
| Responsive Design, Light/Dark Theming, Custom Widgets, Animations, Page Transitions | `ui.md` |
| Skeleton Loading, Empty States, Error UX, Paywall Strategies | `ux_states.md` |
| Custom Painter — Arc Gauges, Line Charts, Dashed Borders | `custom_painter.md` |
| Accessibility — Semantics, Contrast, Screen Readers, Reduced Motion | `accessibility.md` |
| Onboarding, Feature Discovery, What's New Dialog | `onboarding.md` |

### 🧭 Navigation
| Topic | File |
|-------|------|
| GoRouter, GetX Routing, Deep Links, Bottom Nav State | `navigation.md` |
| App Links, Universal Links, Branch.io, Dynamic Links | `deeplinks.md` |

### 🌐 Networking
| Topic | File |
|-------|------|
| Dio Production Setup, Retry, Error Handling, JSON Serialization | `networking.md` |
| Request Cancellation, Rate Limiting, API Versioning | `networking_advanced.md` |
| HTTP Response Caching — dio_cache_interceptor, Stale-While-Revalidate | `http_caching.md` |

### 🔥 Backend Integration
| Topic | File |
|-------|------|
| Firebase (Firestore, Storage, Batch), Supabase (Auth, Realtime, RPC) | `backend.md` |
| Email/Google/Phone Auth, FCM Push (all 3 app states), WebSockets, Supabase Realtime | `auth_notifications.md` |
| MQTT, Socket.IO, SignalR, Raw WebSocket with Heartbeat & Reconnect | `realtime_protocols.md` |

### 💾 Storage & Data
| Topic | File |
|-------|------|
| SharedPreferences, Hive, SQLite, Cache-First Strategy, Offline Support | `storage.md` |
| Encrypted Hive, AES-256-at-Rest, SQLCipher, Key Rotation | `encrypted_storage.md` |
| Offline-First Sync, Conflict Resolution, SQLite DB Migrations | `data_sync.md` |

### 🔐 Security
| Topic | File |
|-------|------|
| Obfuscation, flutter_secure_storage, SSL Pinning, API Key Protection, Root Detection | `security.md` |
| Biometric Auth — Fingerprint, Face ID, Auto-Lock, Settings Toggle | `biometric.md` |

### ⚡ Performance
| Topic | File |
|-------|------|
| const, ListView.builder, RepaintBoundary, compute(), Image Caching | `performance.md` |
| Isolates, DevTools Profiling, List Virtualization, Pagination | `performance_advanced.md` |

### 💰 Monetization
| Topic | File |
|-------|------|
| AdMob + Yandex Unified Manager, Banner/Interstitial/Rewarded, GDPR | `monetization.md` |
| Stripe PaymentSheet, Google Pay, Apple Pay, PayPal | `payments.md` |

### 🔔 Notifications
| Topic | File |
|-------|------|
| Full Local Notification Setup, Daily/Weekly Scheduled, In-App Banner | `local_notifications.md` |
| Action Buttons, Background FCM Isolate, Notification Grouping, Rich Notifications | `notifications_advanced.md` |

### 🌍 Localization
| Topic | File |
|-------|------|
| ARB Files, 10 Languages, RTL Support, Locale Persistence | `localization.md` |

### 🧪 Testing
| Topic | File |
|-------|------|
| Unit Tests (mocktail, BLoC test, Riverpod container), Widget Tests, Golden Tests, Integration Tests | `testing.md` |

### 🚀 CI/CD & Deployment
| Topic | File |
|-------|------|
| GitHub Actions (test→build Android→build iOS→deploy), App Signing, ProGuard | `cicd.md` |
| Fastlane, Automated Testing Pipeline, Flavor Builds, Store Automation | `cicd_advanced.md` |

### 📊 Analytics & Observability
| Topic | File |
|-------|------|
| Structured Logger, Firebase Crashlytics, Firebase Analytics, Screen Tracking | `observability.md` |
| Remote Config, Feature Flags, A/B Testing, Funnel Tracking | `analytics_advanced.md` |
| Sentry, Datadog — Non-Firebase Crash Reporting, RUM, Performance Monitoring | `crash_reporting_advanced.md` |

### 📱 Device & Platform
| Topic | File |
|-------|------|
| Camera, GPS, Platform Channels (Flutter↔Kotlin), WorkManager, Background Services, Sensors | `device.md` |
| App Lifecycle, Privacy Overlay, Wakelock, Battery State, Network Reaction | `lifecycle.md` |

### 📦 Configuration & Flavors
| Topic | File |
|-------|------|
| dev/staging/prod AppConfig, Firebase per Flavor, VS Code Launch Configs | `flavors.md` |
| Force Update Gate, In-App Update (Play Store API), Remote Config Versioning | `force_update.md` |

### 🧹 Code Quality
| Topic | File |
|-------|------|
| analysis_options.yaml, Flutter Lints, Formatting, Build Runner | `quality.md` |
| Strict Analysis, Custom Lint Rules, dart_code_metrics, Naming Conventions | `quality_advanced.md` |

### 🧩 UI Components & Patterns
| Topic | File |
|-------|------|
| Error Boundary, FeedbackService (Snackbars/Dialogs/Loading Overlay), Empty/Error Widgets | `error_feedback.md` |
| File Sharing, PDF Generation, Excel Export, Native File Open | `file_sharing.md` |

### 🏪 Store Readiness
| Topic | File |
|-------|------|
| App Size Analysis, Startup Optimization, ASO, Screenshots, In-App Review | `store_readiness.md` |

### 🎯 Dart 3
| Topic | File |
|-------|------|
| Records, Pattern Matching, Sealed Classes, Switch Expressions, Class Modifiers | `dart3.md` |

---

## 💡 Example Prompts After Installing

```
"Show me a production GetX controller for VPN connection with error handling"
"Set up Riverpod with Clean Architecture for a server list screen"
"How do I implement SSL pinning with Dio in Flutter?"
"Create a full Firebase Auth service with Google Sign-In and token refresh"
"Show me how to set up GitHub Actions CI for Flutter with Play Store deployment"
"Build an encrypted Hive service for storing user session data"
"How do I add notification action buttons in Flutter?"
"Set up Dart 3 sealed classes for auth states"
"Create a paywall screen with RevenueCat in Flutter"
"How do I implement stale-while-revalidate caching with Dio?"
```

---

## 🔧 Requirements

- Claude.ai Pro, Team, or Enterprise plan (Skills feature)
- Flutter 3.16+ (Dart 3.0+ for full feature coverage)

---

## 📁 Repository Structure

```
flutter-production-skill/
├── README.md
├── flutter-production.skill       ← Install this in Claude
└── flutter-production/            ← Source (for transparency / contributions)
    ├── SKILL.md                   ← Master guide & routing table
    └── references/
        ├── architecture.md
        ├── architecture_advanced.md
        ├── state.md
        ├── ui.md
        ├── ux_states.md
        ├── ... (45 files total)
        └── dart3.md
```

---

## 🤝 Contributing

Found a gap? Open a PR adding a new reference file or improving an existing one.

Format: follow the existing reference file structure — code-first, production patterns only, no toy examples.

---

## 📄 License

MIT — use freely, credit appreciated.

---

*Built with Claude Sonnet — using Claude to build better Claude skills* 🤖

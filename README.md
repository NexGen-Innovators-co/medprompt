# MedPrompt 💊

A Flutter-based medication adherence app designed to help patients stay consistent with their medication schedules through personalized plans, smart reminders, and motivational systems.

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-039BE5?style=for-the-badge&logo=Firebase&logoColor=white)

## 📋 Table of Contents

- [About](#about)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Development Guidelines](#development-guidelines)
- [Contributing](#contributing)
- [Team](#team)
- [License](#license)

## 🎯 About

MedPrompt addresses the critical issue where 50% of patients don't take their medications as prescribed (WHO). Our app provides:

- **Personalized medication plans** tailored to individual schedules
- **Smart reminder system** with customizable alerts
- **Motivational features** including streaks, points, and rewards
- **Comprehensive tracking** with visual analytics
- **Caregiver support** for family and healthcare providers

## ✨ Features

### Core Features
- 📅 **Personalized Medication Plans**: Custom schedules based on prescriptions
- ⏰ **Smart Reminders**: Intelligent notifications with behavior-based timing
- 🎯 **Medication Tracking**: Visual progress with calendars and graphs
- 🏆 **Motivational System**: Points, streaks, badges, and social sharing
- 👥 **Caregiver Dashboard**: Family/professional monitoring support

### Technical Features
- 📱 Cross-platform (Android, iOS, Desktop)
- 🔄 Real-time data synchronization
- 📊 Advanced analytics and reporting
- 🎨 Dual UI modes (standard & simplified)
- 🔔 Local and push notifications

## 🛠 Prerequisites

Before you begin, ensure you have the following installed:

### Required Software
- **Flutter SDK** (3.16.0 or higher)
  - [Install Flutter](https://flutter.dev/docs/get-started/install)
- **Dart SDK** (3.2.0 or higher) - comes with Flutter
- **Git** for version control
- **VS Code** or **Android Studio** (recommended IDEs)

### Platform-Specific Requirements

#### For Android Development:
- **Android Studio** or **Android SDK**
- **Java JDK** (8 or higher)
- **Android device** or **emulator**

#### For iOS Development (macOS only):
- **Xcode** (latest version)
- **iOS Simulator** or **physical iOS device**
- **CocoaPods** - Install with: `sudo gem install cocoapods`

#### For Desktop Development:
- **Visual Studio** (Windows)
- **Xcode** (macOS)
- **Linux development tools** (Linux)

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/medprompt.git
cd medprompt
```

### 2. Verify Flutter Installation

```bash
flutter doctor
```

Ensure all checkmarks are green. If not, follow the suggestions provided.

### 3. Install Dependencies

```bash
flutter pub get
```

### 4. Firebase Setup

1. Create a new Firebase project at [Firebase Console](https://console.firebase.google.com/)
2. Enable the following services:
   - Authentication
   - Cloud Firestore
   - Cloud Messaging
   - Analytics

3. Download configuration files:
   - **Android**: Download `google-services.json` → place in `android/app/`
   - **iOS**: Download `GoogleService-Info.plist` → place in `ios/Runner/`

4. Follow the [FlutterFire installation guide](https://firebase.flutter.dev/docs/overview)

### 5. Environment Configuration

Create a `.env` file in the root directory:

```env
# Firebase Configuration
FIREBASE_API_KEY=your_api_key_here
FIREBASE_PROJECT_ID=your_project_id_here
FIREBASE_MESSAGING_SENDER_ID=your_sender_id_here
FIREBASE_APP_ID=your_app_id_here

# App Configuration
APP_NAME=MedPrompt
APP_VERSION=1.0.0
DEBUG_MODE=true
```

### 6. Run the App

```bash
# For debugging
flutter run

# For specific platforms
flutter run -d android
flutter run -d ios
flutter run -d windows
flutter run -d macos
flutter run -d linux
```

### 7. Build for Production

```bash
# Android APK
flutter build apk --release

# Android App Bundle
flutter build appbundle --release

# iOS
flutter build ipa --release

# Desktop
flutter build windows --release
flutter build macos --release
flutter build linux --release
```

## 📁 Project Structure

```
medprompt/
├── lib/
│   ├── core/
│   │   ├── constants/
│   │   ├── errors/
│   │   ├── network/
│   │   └── utils/
│   ├── data/
│   │   ├── datasources/
│   │   ├── models/
│   │   └── repositories/
│   ├── domain/
│   │   ├── entities/
│   │   ├── repositories/
│   │   └── usecases/
│   ├── presentation/
│   │   ├── pages/
│   │   ├── widgets/
│   │   ├── providers/
│   │   └── themes/
│   └── main.dart
├── test/
├── android/
├── ios/
├── web/
├── windows/
├── macos/
├── linux/
├── assets/
│   ├── images/
│   ├── icons/
│   └── fonts/
├── docs/
└── README.md
```

### Directory Explanations

- **`lib/core/`**: Shared utilities, constants, and configurations
- **`lib/data/`**: Data layer with models, repositories, and data sources
- **`lib/domain/`**: Business logic layer with entities and use cases
- **`lib/presentation/`**: UI layer with pages, widgets, and state management
- **`assets/`**: Images, icons, fonts, and other static resources
- **`test/`**: Unit tests, widget tests, and integration tests

## 👨‍💻 Development Guidelines

### Code Style
We follow the [Dart Style Guide](https://dart.dev/guides/language/effective-dart/style). Use these commands:

```bash
# Format code
dart format .

# Analyze code
flutter analyze

# Run tests
flutter test
```

### Git Workflow

1. **Branch Naming Convention**:
   - Feature branches: `feature/medication-reminders`
   - Bug fixes: `bugfix/notification-issue`
   - Hotfixes: `hotfix/critical-crash`

2. **Commit Message Format**:
   ```
   type(scope): description
   
   [optional body]
   [optional footer]
   ```
   
   Examples:
   - `feat(reminders): add smart notification system`
   - `fix(auth): resolve login validation issue`
   - `docs(readme): update installation instructions`

3. **Pull Request Process**:
   - Create feature branch from `develop`
   - Make changes and test thoroughly
   - Create PR with detailed description
   - Request review from at least one team member
   - Merge after approval

### State Management
We use **Provider** for state management. Follow these patterns:

```dart
// providers/medication_provider.dart
class MedicationProvider extends ChangeNotifier {
  // Implementation
}

// Usage in widgets
Consumer<MedicationProvider>(
  builder: (context, provider, child) {
    return YourWidget();
  },
)
```

### Testing
Write tests for all features:

```bash
# Run all tests
flutter test

# Run tests with coverage
flutter test --coverage

# Run integration tests
flutter drive --target=test_driver/app.dart
```

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork the repository**
2. **Create your feature branch** (`git checkout -b feature/amazing-feature`)
3. **Make your changes** following our guidelines
4. **Add tests** for new functionality
5. **Commit your changes** (`git commit -m 'feat: add amazing feature'`)
6. **Push to the branch** (`git push origin feature/amazing-feature`)
7. **Open a Pull Request**

### Development Setup for Contributors

1. Follow the [Getting Started](#getting-started) guide
2. Create a new branch for your feature
3. Set up your IDE with Flutter extensions
4. Configure code formatting and linting
5. Run tests before submitting PRs

### Issue Reporting

When reporting issues, please include:
- Flutter version (`flutter --version`)
- Device/OS information
- Steps to reproduce
- Expected vs actual behavior
- Screenshots (if applicable)

## 👥 Team

| Role | Responsibility | GitHub |
|------|----------------|---------|
| Project Manager | Coordination, Planning | [@username1](https://github.com/username1) |
| Lead Flutter Developer | Architecture, Core Features | [@username2](https://github.com/username2) |
| UI/UX Designer | Design, Frontend | [@username3](https://github.com/username3) |
| Backend Developer | Database, APIs | [@username4](https://github.com/username4) |
| Mobile Developer & QA | Features, Testing | [@username5](https://github.com/username5) |

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: Check our [Wiki](https://github.com/your-username/medprompt/wiki)
- **Issues**: [GitHub Issues](https://github.com/your-username/medprompt/issues)
- **Discussions**: [GitHub Discussions](https://github.com/your-username/medprompt/discussions)

## 🔗 Useful Links

- [Flutter Documentation](https://flutter.dev/docs)
- [Firebase Documentation](https://firebase.google.com/docs)
- [Material Design Guidelines](https://material.io/design)
- [Provider Documentation](https://pub.dev/packages/provider)

---

**Made with ❤️ by the MedPrompt Team**
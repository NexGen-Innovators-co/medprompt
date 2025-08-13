# Contributing to MedPrompt 🤝

Welcome to the MedPrompt project! We're excited to have you contribute to helping patients improve their medication adherence. This guide will help you get started with contributing to our Flutter application.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Process](#development-process)
- [Coding Standards](#coding-standards)
- [Pull Request Process](#pull-request-process)
- [Issue Guidelines](#issue-guidelines)
- [Testing Requirements](#testing-requirements)
- [Documentation](#documentation)

## 🤝 Code of Conduct

### Our Standards
- Be respectful and inclusive
- Focus on what's best for the community and users
- Show empathy towards other contributors
- Accept constructive criticism gracefully
- Help others learn and grow

### Unacceptable Behavior
- Harassment, trolling, or derogatory comments
- Publishing private information without permission
- Any conduct that would be inappropriate in a professional setting

## 🚀 Getting Started

### Prerequisites
Before contributing, make sure you have:
- Flutter SDK (3.16.0+) installed
- Git configured with your name and email
- A GitHub account
- Read our [README.md](README.md) thoroughly

### First-Time Setup
1. Fork the repository on GitHub
2. Clone your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/medprompt.git
   cd medprompt
   ```
3. Add the original repository as upstream:
   ```bash
   git remote add upstream https://github.com/ORIGINAL_USERNAME/medprompt.git
   ```
4. Install dependencies:
   ```bash
   flutter pub get
   ```
5. Run the app to ensure everything works:
   ```bash
   flutter run
   ```

## 🔄 Development Process

### Branch Strategy
We use **Git Flow** with these branches:
- `main`: Production-ready code
- `develop`: Integration branch for features
- `feature/*`: New features
- `bugfix/*`: Bug fixes
- `hotfix/*`: Critical production fixes

### Workflow
1. **Create a branch** from `develop`:
   ```bash
   git checkout develop
   git pull upstream develop
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** following our coding standards

3. **Test your changes** thoroughly:
   ```bash
   flutter test
   flutter analyze
   dart format .
   ```

4. **Commit your changes** with clear messages:
   ```bash
   git add .
   git commit -m "feat(reminders): add smart notification system"
   ```

5. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

6. **Create a Pull Request** against the `develop` branch

## 💻 Coding Standards

### Dart/Flutter Guidelines
- Follow [Effective Dart](https://dart.dev/guides/language/effective-dart) principles
- Use meaningful variable and function names
- Keep functions small and focused (max 20-30 lines)
- Add comments for complex logic
- Use const constructors where possible

### Code Formatting
```bash
# Format your code before committing
dart format .

# Analyze for issues
flutter analyze

# Fix common issues automatically
dart fix --apply
```

### Naming Conventions
```dart
// Classes: PascalCase
class MedicationProvider extends ChangeNotifier {}

// Variables/Functions: camelCase
String medicationName = 'Aspirin';
void scheduleMedication() {}

// Constants: SCREAMING_SNAKE_CASE
static const String API_BASE_URL = 'https://api.medprompt.com';

// Files: snake_case
medication_provider.dart
add_medication_page.dart
```

### State Management
We use **Provider** pattern:
```dart
// Good: Use Consumer for rebuilds
Consumer<MedicationProvider>(
  builder: (context, provider, child) => Text(provider.medicationCount),
)

// Good: Use context.read() for actions
context.read<MedicationProvider>().addMedication(medication);

// Bad: Don't use Provider.of with listen: true in build methods
Provider.of<MedicationProvider>(context).medicationCount; // ❌
```

### File Organization
```dart
// Order imports: Dart SDK → Flutter → Third-party → Local
import 'dart:async';
import 'dart:convert';

import 'package:flutter/material.dart';
import 'package:flutter/services.dart';

import 'package:provider/provider.dart';
import 'package:firebase_auth/firebase_auth.dart';

import '../models/medication.dart';
import '../providers/medication_provider.dart';
```

## 🔍 Pull Request Process

### Before Creating a PR
- [ ] Code follows our style guidelines
- [ ] Self-review completed
- [ ] Tests added for new functionality
- [ ] All tests pass
- [ ] Documentation updated
- [ ] No merge conflicts with develop branch

### PR Description Template
Use our [pull request template](.github/pull_request_template.md) and include:
- **What**: Brief description of changes
- **Why**: Reason for the changes
- **How**: Technical approach taken
- **Testing**: How you tested the changes
- **Screenshots**: For UI changes

### Review Process
1. **Automatic checks** must pass (linting, tests)
2. **Code review** by at least one team member
3. **QA testing** for significant changes
4. **Approval** from code owner before merge

### Review Checklist for Reviewers
- [ ] Code follows project standards
- [ ] Logic is sound and efficient
- [ ] Tests are comprehensive
- [ ] Documentation is updated
- [ ] UI/UX matches design requirements
- [ ] No security vulnerabilities
- [ ] Performance considerations addressed

## 🐛 Issue Guidelines

### Before Creating an Issue
1. Check if a similar issue already exists
2. Try to reproduce the problem
3. Gather relevant information (device, OS, Flutter version)

### Issue Types
- **🐛 Bug Report**: Something isn't working correctly
- **✨ Feature Request**: Suggest new functionality
- **📚 Documentation**: Improve or add documentation
- **🔧 Maintenance**: Code refactoring, dependencies update
- **❓ Question**: General questions about the project

### Bug Report Template
```markdown
**Describe the Bug**
A clear description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Tap on '....'
3. See error

**Expected Behavior**
What you expected to happen.

**Screenshots**
Add screenshots if applicable.

**Environment**
- Device: [e.g. iPhone 12, Pixel 5]
- OS: [e.g. iOS 15.1, Android 12]
- App Version: [e.g. 1.0.0]
- Flutter Version: [e.g. 3.16.0]
```

## 🧪 Testing Requirements

### Test Coverage
- **Unit Tests**: Business logic, utilities, models
- **Widget Tests**: UI components, user interactions
- **Integration Tests**: Complete user flows

### Running Tests
```bash
# Run all tests
flutter test

# Run tests with coverage
flutter test --coverage

# Run specific test file
flutter test test/unit/medication_provider_test.dart

# Run integration tests
flutter drive --target=test_driver/app.dart
```

### Test Structure
```dart
// test/unit/medication_provider_test.dart
import 'package:flutter_test/flutter_test.dart';
import 'package:medprompt/providers/medication_provider.dart';

void main() {
  group('MedicationProvider Tests', () {
    late MedicationProvider provider;

    setUp(() {
      provider = MedicationProvider();
    });

    test('should add medication correctly', () {
      // Arrange
      final medication = Medication(name: 'Aspirin');
      
      // Act
      provider.addMedication(medication);
      
      // Assert
      expect(provider.medications.length, equals(1));
      expect(provider.medications.first.name, equals('Aspirin'));
    });
  });
}
```

## 📖 Documentation

### Code Documentation
```dart
/// Manages medication data and provides methods for CRUD operations.
/// 
/// This provider handles:
/// - Adding and removing medications
/// - Scheduling reminders
/// - Tracking adherence
class MedicationProvider extends ChangeNotifier {
  /// Adds a new medication to the user's list.
  /// 
  /// Throws [ArgumentError] if medication name is empty.
  /// Returns true if medication was added successfully.
  bool addMedication(Medication medication) {
    // Implementation...
  }
}
```

### README Updates
When adding new features:
- Update the feature list
- Add new setup instructions if needed
- Update screenshots
- Document any new environment variables

## 🚀 Release Process

### Version Numbering
We follow [Semantic Versioning](https://semver.org/):
- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes (backward compatible)

### Changelog
Update `CHANGELOG.md` with:
- New features added
- Bug fixes
- Breaking changes
- Migration notes

## 💡 Tips for Success

### For New Contributors
- Start with small issues labeled "good first issue"
- Ask questions in discussions or issues
- Read existing code to understand patterns
- Don't be afraid to make mistakes - we all learn together

### For Experienced Contributors
- Help review PRs from newer contributors
- Suggest improvements to our processes
- Share knowledge in team discussions
- Mentor other team members

## 📞 Getting Help

- **General Questions**: Use [GitHub Discussions](https://github.com/your-username/medprompt/discussions)
- **Bug Reports**: Create an [Issue](https://github.com/your-username/medprompt/issues)
- **Team Chat**: Join our WhatsApp/Discord group
- **Documentation**: Check our [Wiki](https://github.com/your-username/medprompt/wiki)

## 🏆 Recognition

We appreciate all contributions! Contributors will be:
- Added to our contributors list
- Mentioned in release notes for significant contributions
- Eligible for team swag and recognition

---

Thank you for contributing to MedPrompt! Together, we're helping patients improve their health outcomes through better medication adherence. 💊❤️
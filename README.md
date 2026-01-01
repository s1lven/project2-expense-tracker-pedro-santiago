# Expense Tracker

A comprehensive expense tracking application built with Flutter and Firebase, featuring receipt photo storage, location tracking, budget management, and multi-currency support.

## Video demo

https://youtu.be/tyE11iAo5o0

## Features

### Core Features
- **User Authentication**: Email/password and Google Sign-In
- **Expense Management**: Add, edit, and delete expenses
- **Receipt Photos**: Attach receipt images to expenses
- **Location Tracking**: Auto-tag expense location with GPS
- **Budget Categories**: Set category budgets with alerts
- **Recurring Expenses**: Auto-create monthly bills
- **Export Reports**: Generate PDF/CSV expense reports
- **Currency Conversion**: Multi-currency support with real-time rates

### Bonus Features
- **Dark Mode**: System theme detection and manual toggle
- **Advanced Search**: Full-text search across expenses

## Technical Implementation

### 1. Receipt Photos
- Uses `image_picker` for camera/gallery access
- Firebase Storage for image uploads
- User-specific directory structure: `users/{userId}/expense_images/`
- Image compression before upload
- Note: Firebase Storage requires paid plan for full testing

### 2. Location Tracking
- GPS integration using `geolocator` package
- Address geocoding with `geocoding` package
- Auto-tagging of expense locations
- **Performance Note**: Adding geolocation increases expense creation time due to GPS lookup

### 3. Budget Categories
- Category-specific budget limits
- Real-time budget tracking
- Push notifications when limits exceeded
- Monthly budget periods

### 4. Recurring Expenses
- Automatic monthly expense creation
- Configurable recurring patterns
- Background service for expense generation

### 5. Export Reports
- PDF report generation
- CSV export functionality
- Date range filtering
- Category-based reporting

### 6. Currency API Integration
- Frankfurter API for exchange rates
- 16 supported currencies with flags
- Real-time rate updates
- Historical exchange rate charts
- Local caching for offline access

## Architecture

### Clean Architecture Structure
```
lib/
├── main.dart
├── models/           # Data models
├── services/         # External services (Firebase, API)
├── providers/        # State management (Provider)
├── repositories/     # Data abstraction layer
├── screens/          # UI screens (auth, home, profile)
├── widgets/          # Reusable UI components
└── utils/           # Helper functions and constants
```

### Firebase Integration
- **Authentication**: Firebase Auth
- **Database**: Firestore (user-specific data)
- **Storage**: Firebase Storage (receipt images)
- **Structure**: `users/{userId}/expenses/{expenseId}/`

## State Management
- **Provider** for app-wide state management
- **AuthProvider**: Authentication state
- **DataProvider**: Expenses and budgets
- **SettingsProvider**: User preferences and theme

## Native Features
- **Camera**: Receipt photo capture
- **GPS**: Location tagging
- **Notifications**: Budget alerts

## Getting Started

### Prerequisites
- Flutter SDK
- Firebase project setup
- Android/iOS development environment

### Installation
1. Clone the repository
2. Run `flutter pub get`
3. Configure Firebase (add `google-services.json` for Android)
4. Run `flutter run`

### Firebase Configuration
- Enable Authentication (Email/Password, Google)
- Set up Firestore database
- Configure Storage for images
- Update `firebase_options.dart` with your project config

## Performance Considerations
- Location tracking adds ~2-3 seconds to expense creation
- Image uploads depend on network speed and Firebase Storage plan
- Currency API responses cached locally for offline access

## Known Limitations
- Firebase Storage requires paid plan for production image uploads
- GPS accuracy depends on device and environment
- Currency API has rate limits (handled with caching)

## Technologies Used
- **Flutter**: Cross-platform UI framework
- **Firebase**: Backend services
- **Provider**: State management
- **Frankfurter API**: Currency exchange rates
- **Image Picker**: Camera/gallery access
- **Geolocator**: GPS location services

## Developer Notes
This project demonstrates professional Flutter development with clean architecture, comprehensive Firebase integration, and native device features. The codebase is optimized for maintainability and follows modern development practices.

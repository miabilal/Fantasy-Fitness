# 🏃‍♂️ FantasyFitness — Turn Your Steps Into Stats!

**FantasyFitness** is a gamified health and fitness app where your real-world activity powers a fantasy-style leveling system. Run, walk, or jog to upgrade your attributes, earn FF points, and climb the ranks — solo or with friends.

## 🚀 Features

### Core Functionality
- 🎮 **Fantasy Score System** - Earn FF points for every meter moved with speed-based multipliers
- 🧬 **RPG-Style Stats** - Build your athlete profile with level progression
- 🏆 **Live Challenges** - Team-based competitions with real-time scoring
- 🫂 **Social Features** - Friend activity feeds and leaderboards
- 👟 **HealthKit Integration** - Automatic sync of walking/running data
- 📊 **Activity History** - Detailed breakdowns of your fitness sessions
- 🔔 **Push Notifications** - Challenge updates and achievements via OneSignal
- 📱 **iOS Widgets** - Home screen widgets showing progress and challenges

### Advanced Features
- 🎯 **Background Health Sync** - Automatic data collection in background
- 🔄 **Real-time Updates** - Live challenge scores and team standings
- 🏅 **Team Competitions** - Join teams and compete for group goals
- 📈 **Progress Tracking** - Visual progress bars and historical data
- 🎨 **Modern UI** - SwiftUI with custom animations and glass morphism effects

## 🏗️ Architecture

### App Structure
```
FantasyFitness/
├── FantasyFitness/           # Main app target
│   ├── Models/              # Data models (User, Health, Challenge)
│   ├── Views/               # SwiftUI views and UI components
│   ├── Managers/            # HealthManager, Supabase client
│   └── Extensions/          # Swift extensions and utilities
├── FantasyFitnessWidget/    # iOS Widget extension
├── OneSignalNotificationServiceExtension/  # Push notification handling
└── Tests/                   # Unit and UI tests
```

### Key Components

#### **HealthManager.swift**
- Handles HealthKit integration and data synchronization
- Background health data collection with observers
- FF Score calculation based on distance and speed
- Real-time challenge score updates

#### **User Authentication**
- Apple Sign-In integration with Supabase Auth
- User profile management with avatar selection
- Session persistence and automatic login

#### **Challenge System**
- Team-based competitions with configurable goals
- Real-time scoring and leaderboard updates
- Push notifications for challenge events
- Widget integration for quick progress viewing

#### **Data Models**
- `FFUser`: User profile and statistics
- `HealthSample`: Individual health data points
- `HealthSession`: Aggregated workout sessions
- `Challenge`: Competition structure and rules

## 🧠 Tech Stack

| Technology | Purpose | Version |
|------------|---------|---------|
| **SwiftUI** | Modern declarative UI framework | iOS 17+ |
| **HealthKit** | Health data integration and background sync | iOS 17+ |
| **Supabase** | Backend-as-a-Service (Auth, Database, Real-time) | 2.5.1+ |
| **OneSignal** | Push notifications and in-app messaging | 5.2.14+ |
| **WidgetKit** | iOS home screen widgets | iOS 17+ |
| **Swift Concurrency** | async/await for modern asynchronous programming | Swift 5.5+ |
| **SwiftData** | Local data persistence (preview/testing) | iOS 17+ |

### Dependencies
- **Supabase Swift SDK** - Authentication, database, and real-time features
- **OneSignal iOS SDK** - Push notifications and user engagement
- **PostgREST** - Type-safe database queries

## 🔧 Setup & Installation

### Prerequisites
- Xcode 15.0+
- iOS 17.0+ deployment target
- macOS 14.0+ for development
- Apple Developer Account (for HealthKit and Push Notifications)

### Configuration

1. **Clone the repository**
   ```bash
   git clone https://github.com/miabilal/Fantasy-Fitness.git
   cd Fantasy-Fitness
   ```

2. **Configure Supabase**
   - Update `Supabase.swift` with your project URL and API key
   - Set up your database schema (users, health_data, challenges tables)

3. **Configure OneSignal**
   - Replace the OneSignal App ID in `FantasyFitnessApp.swift`
   - Set up push notification certificates in Apple Developer Console

4. **Configure HealthKit**
   - Enable HealthKit capability in Xcode
   - Update entitlements file with required HealthKit permissions

5. **Build and Run**
   ```bash
   open FantasyFitness.xcodeproj
   ```

### Environment Setup
- **Development Team**: Update with your Apple Developer Team ID
- **Bundle Identifier**: Change from `com.Jawwaad.FantasyFitness`
- **HealthKit Permissions**: Configure in `Info.plist` and entitlements

## 📱 App Flow

1. **Onboarding** - Apple Sign-In authentication
2. **Health Permission** - Request HealthKit access
3. **Main App** - Home screen with FF score and active challenges
4. **Challenges** - Browse and join team competitions
5. **Activity** - View leaderboards and friend activity
6. **Profile** - Manage user settings and avatar

## 🎯 Key Features Deep Dive

### FF Score Calculation
```swift
// Base score from distance (meters/100)
let base = distanceMeters / 100

// Speed-based multipliers
switch speed {
    case ..<1.5: multiplier = 1.0    // Walking
    case ..<2.5: multiplier = 1.25   // Brisk walking
    case ..<3.5: multiplier = 1.5    // Jogging
    case ..<4.5: multiplier = 2.0    // Running
    default:     multiplier = 2.5    // Sprinting
}

return base * multiplier
```

### Challenge System
- **Team-based competitions** with configurable goals
- **Real-time scoring** with automatic team updates
- **Push notifications** for challenge events and completions
- **Widget integration** for quick progress viewing

### Background Sync
- **HealthKit observers** for automatic data collection
- **Background app refresh** for continuous sync
- **Widget timeline updates** via silent push notifications

## 🧪 Development Notes

### Architecture Patterns
- **MVVM with SwiftUI** - Clean separation of concerns
- **Environment Objects** - Shared state management
- **Async/Await** - Modern concurrency throughout
- **Modular Views** - Reusable SwiftUI components

### Testing
- Unit tests for business logic
- UI tests for critical user flows
- Preview providers for SwiftUI development

### Performance Optimizations
- Efficient HealthKit queries with date filtering
- Background processing for health data sync
- Optimized SwiftUI views with proper state management

## 📈 Future Roadmap

- 🥇 **Enhanced Leaderboards** - Global and friend-based rankings
- 🔔 **Smart Notifications** - Personalized daily goals and reminders
- 💬 **Social Features** - In-app messaging and friend invites
- 👾 **Avatar System** - Customizable character progression
- 🛍 **Cosmetics Shop** - Non-monetized reward system
- 📊 **Analytics Dashboard** - Detailed fitness insights
- 🏃‍♀️ **Workout Plans** - Guided training programs

## 🤝 Contributing

This project demonstrates modern iOS development practices including:
- SwiftUI best practices
- HealthKit integration
- Real-time backend integration
- Push notification handling
- Widget development
- Modern Swift concurrency

## 📄 License

This project is for demonstration purposes and showcases iOS development skills.

---

### ⚡ Built by Jawwaad Sabree  
FantasyFitness is an indie passion project designed to make fitness more fun and engaging through gamification.  
Follow along on [Twitter](https://twitter.com/jawwaadsabree) or check out more work at [jawwaadsabree.dev](https://jawwaadsabree.dev)  

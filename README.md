# MeetAppUpdateManager
One file for App update in Swift using firebase config
# 🔄 Force Update iOS App with Firebase Remote Config

This implementation helps your iOS app detect and prompt for **force** or **soft updates** using Firebase Remote Config. It checks the app version remotely and decides whether the user must update the app immediately or optionally.

---

## 📦 Features

- ✅ Checks for app version compatibility with Firebase Remote Config
- ⚠️ Shows a force update alert (no cancel) if the current version is below `minimum_version`
- 🔔 Shows a soft update alert (optional cancel) if the current version is below `current_version` but above `minimum_version`
- 📲 Redirects user to App Store for updates
- 🧩 Written in Swift using UIKit

---

## 🧱 Components

### 🔹 `ForceUpdateChecker.swift`

This class contains the logic for:

- Fetching and activating Remote Config
- Comparing app version with `minimum_version` and `current_version`
- Displaying update alerts
- Redirecting to the App Store

---

## 🔧 Firebase Remote Config Keys

Ensure the following keys are defined in your Firebase Remote Config project:

| Key               | Type   | Description                            | Example             |
|------------------|--------|----------------------------------------|---------------------|
| `minimum_version`| String | Version that enforces a force update   | `1.0.0`             |
| `current_version`| String | Version that suggests a soft update    | `1.2.0`             |
| `store_url`      | String | URL to the app on the App Store        | `https://itunes.apple.com/app/id1234567` |

---

## 💡 How It Works

1. `setUpRemoteConfig()` sets default values and fetches remote config.
2. `check()` compares the app's current build version with the values from Remote Config:
   - If build < `minimum_version`: 🔴 Force Update
   - If build < `current_version`: 🟡 Soft Update
   - Else: ✅ No Update
3. `verifyVersion()` presents an alert accordingly with an **Update** button (and **Cancel** if soft update).

---

## 🧪 Usage

Call this in your `AppDelegate` or launch controller:

```swift
ForceUpdateChecker.shared.verifyVersion()



Built with 💙 by Manpreet Singh(iOS Developer)

# Moneyflow — Complete Android APK Source Project (iOS 27 Liquid Glass Edition)

This archive contains a complete, ready-to-compile **Android Studio / Gradle APK project** wrapping the **Moneyflow** personal expense tracker & wealth mobile application with native Android edge-to-edge rendering, offline local persistence, haptic feedback, native file sharing/export (CSV & JSON), and scheduled bill push notifications.

## Project Structure

```text
Moneyflow-Android-APK/
├── build.gradle                     # Root Gradle configuration
├── settings.gradle                  # Module includes (:app)
├── gradle.properties                # AndroidX & JVM build flags
├── capacitor.config.json            # Optional Capacitor CLI metadata
├── README.md                        # Build, signing & ADB install guide
└── app/
    ├── build.gradle                 # Android APK build config (com.moneyflow.app, minSdk 24, targetSdk 35)
    ├── proguard-rules.pro           # ProGuard / R8 rules
    └── src/main/
        ├── AndroidManifest.xml      # Permissions (POST_NOTIFICATIONS, SCHEDULE_EXACT_ALARM, VIBRATE) & FileProvider
        ├── assets/www/
        │   └── index.html           # Complete Moneyflow iOS 27 Liquid Glass web app + AndroidBridge
        ├── java/com/moneyflow/app/
        │   ├── MainActivity.java    # Edge-to-edge WebView host + JS-to-Native Haptic, Notification & File Share bridge
        │   └── ReminderReceiver.java# BroadcastReceiver for scheduled recurring bill notifications
        └── res/
            ├── drawable/            # Adaptive icon background & Moneyflow dual-tone wallet foreground
            ├── mipmap-anydpi-v26/   # Adaptive launcher icon XMLs
            ├── values/              # strings.xml & edge-to-edge Theme.Moneyflow
            └── xml/                 # Android 12+ backup rules & FileProvider paths
```

## How to Build the `.apk` File

### Option A: Using Android Studio (Recommended)
1. Extract `Moneyflow-Android-APK-Source.zip`.
2. Open **Android Studio** -> **Open** -> select the `Moneyflow-Android-APK` folder.
3. Wait for Gradle Sync to complete automatically.
4. From the top menu bar, select **Build** -> **Build Bundle(s) / APK(s)** -> **Build APK(s)**.
5. Once finished, click **locate** in the notification popup to obtain your installable APK at:
   `app/build/outputs/apk/debug/app-debug.apk`

### Option B: Using Command Line (Gradle)
```bash
cd Moneyflow-Android-APK
gradle assembleDebug
# Output APK: app/build/outputs/apk/debug/app-debug.apk
```

### Installing on Your Android Phone
1. Transfer `app-debug.apk` to your Android device (or connect via USB with USB Debugging enabled and run `adb install -r app/build/outputs/apk/debug/app-debug.apk`).
2. Allow **Install unknown apps** if prompted, launch **Moneyflow**, and optionally grant **Notifications** permission for recurring bill alerts.

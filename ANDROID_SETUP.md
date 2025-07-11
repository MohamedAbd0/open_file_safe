# Android Setup Guide for open_file_safe

## Android SDK Compatibility

This plugin has been updated to be compatible with Android SDK 33 and newer Android Gradle Plugin versions.

### Requirements

- Android Gradle Plugin 7.4.2 or higher
- Compile SDK Version 33 or higher
- Target SDK Version 33 or higher

### If you encounter the error: `android:attr/lStar not found`

This error occurs when your project is using an older Android SDK version that doesn't include the `lStar` attribute (introduced in API level 31).

### Solution 1: Update your app's build.gradle

In your app's `android/app/build.gradle` file, ensure you have:

```gradle
android {
    compileSdkVersion 33  // or higher

    defaultConfig {
        targetSdkVersion 33  // or higher
        // ... other configurations
    }
}
```

### Solution 2: Update your project's Android Gradle Plugin

In your project's `android/build.gradle` file:

```gradle
buildscript {
    dependencies {
        classpath 'com.android.tools.build:gradle:7.4.2'  // or higher
    }
}
```

### Solution 3: Update repositories

Make sure you're using `mavenCentral()` instead of the deprecated `jcenter()`:

```gradle
buildscript {
    repositories {
        google()
        mavenCentral()  // instead of jcenter()
    }
}

allprojects {
    repositories {
        google()
        mavenCentral()  // instead of jcenter()
    }
}
```

### Additional Notes

If you're still experiencing issues, try:

1. Run `flutter clean`
2. Delete the `build` folder in your Android project
3. Run `flutter pub get`
4. Try building again

### Compatibility

This plugin is compatible with:

- Flutter SDK: >=2.12.0 <3.0.0
- Android API Level: 16+ (minSdkVersion)
- Compile SDK: 33+ (compileSdkVersion)

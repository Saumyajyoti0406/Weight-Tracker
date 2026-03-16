<div align="center">

<img src="app/src/main/res/mipmap-xxxhdpi/ic_launcher_round.png" width="120" alt="Weight Tracker Icon" />

# Weight Tracker

**A personal weight tracking app for Android — built with a WebView-wrapped HTML/JS frontend.**

![Android](https://img.shields.io/badge/Platform-Android-3DDC84?style=flat-square&logo=android&logoColor=white)
![Min SDK](https://img.shields.io/badge/Min%20SDK-API%2024-blue?style=flat-square)
![Language](https://img.shields.io/badge/Language-Kotlin%20%2B%20HTML-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-purple?style=flat-square)

</div>

---

## Overview

Weight Tracker is a minimalistic yet feature-rich personal health app designed to make daily weight logging effortless. It features a clean dark/light interface with neon-styled text, interactive charts, BMI tracking, weekly averages, goal setting, and Excel export — all packaged as a native Android APK.

---

## Features

### Core Tracking
- **Daily weight logging** — log weight in kg or lb for any past date
- **Future date lock** — prevents logging entries for dates that haven't arrived yet
- **Editable entries** — delete any entry from the log at any time

### Visualisation
- **Monthly chart** — line graph of daily weights for the selected month, with a start line and optional target line
- **Weekly averages chart** — bar chart showing week-by-week average weight trends, displayed directly below the monthly chart
- **Month navigation** — browse previous months using arrow buttons or the history tab selector

### Goal & Progress
- **Target weight** — set a goal weight that appears as a dashed line on all charts
- **Progress bar** — visual fill bar showing how far you've come from start to goal
- **Delta cards** — always-visible "vs previous" and "vs start" numbers on the home screen

### BMI Tracker
- **Saved height** — enter your height once and it's remembered permanently
- **Live BMI calculation** — updates automatically as you log new weights
- **Category scale** — visual sliding scale showing Underweight / Normal / Overweight / Obese with a marker at your current BMI
- **BMI history table** — last 10 entries with BMI and category

### Weekly Averages
- Dedicated tab with a full bar chart and sortable table
- Shows entries per week and change vs previous week

### Export
- **Excel export (.xlsx)** — one-tap download with 5 sheets:
  - Daily Log
  - Weekly Averages
  - Monthly Summary
  - BMI History *(if height is set)*
  - Target Summary *(if goal is set)*

### Onboarding
- **First-launch setup screen** — 3-step flow collecting name, height, and target weight
- Skippable steps — only name is required
- Re-accessible anytime via the **profile** button in the header

### UI / UX
- **Dark & Light mode** toggle — persistent across sessions
- **Neon-styled text** — glowing accents on key numbers and labels
- **Editable name** — click your name in the header to rename
- **Mobile-first layout** — responsive design optimised for phone screens

---

## Screenshots

> Add your own screenshots here after building the APK.

| Onboarding | Home | Chart |
|:---:|:---:|:---:|
| *(screenshot)* | *(screenshot)* | *(screenshot)* |

| BMI | Weekly | Export |
|:---:|:---:|:---:|
| *(screenshot)* | *(screenshot)* | *(screenshot)* |

---

## Tech Stack

| Layer | Technology |
|---|---|
| Android shell | Kotlin + `AppCompatActivity` |
| UI rendering | Android `WebView` |
| Frontend | Vanilla HTML / CSS / JavaScript |
| Charts | [Chart.js 4.4.1](https://www.chartjs.org/) |
| Excel export | [SheetJS (xlsx) 0.18.5](https://sheetjs.com/) |
| Data persistence | `localStorage` (via WebView DOM storage) |
| Build system | Gradle 8.4 |
| Min SDK | API 24 (Android 7.0) |
| Target SDK | API 34 (Android 14) |

---

## Project Structure

```
WeightTracker/
├── app/
│   ├── src/main/
│   │   ├── assets/
│   │   │   └── index.html          ← Entire frontend (HTML + CSS + JS)
│   │   ├── java/com/saumyajyoti/weighttracker/
│   │   │   └── MainActivity.kt     ← WebView setup + back navigation
│   │   ├── res/
│   │   │   ├── layout/
│   │   │   │   └── activity_main.xml
│   │   │   ├── mipmap-*/           ← App icons (all densities)
│   │   │   └── values/
│   │   │       ├── themes.xml      ← Light theme
│   │   │       └── strings.xml
│   │   │   └── values-night/
│   │   │       └── themes.xml      ← Dark theme
│   │   └── AndroidManifest.xml
│   └── build.gradle
├── gradle/wrapper/
│   └── gradle-wrapper.properties
├── build.gradle
├── settings.gradle
└── gradle.properties
```

---

## Building the APK

### Prerequisites
- [Android Studio](https://developer.android.com/studio) (Hedgehog or newer recommended)
- JDK 8 or higher
- Android SDK with API 24–34

### Steps

1. **Clone the repo**
   ```bash
   git clone https://github.com/yourusername/WeightTracker.git
   cd WeightTracker
   ```

2. **Open in Android Studio**
   ```
   File → Open → select the WeightTracker folder → OK
   ```
   Wait for Gradle sync to complete (requires internet on first run).

3. **Build the debug APK**
   ```
   Build → Build Bundle(s) / APK(s) → Build APK(s)
   ```
   Output: `app/build/outputs/apk/debug/app-debug.apk`

4. **Run on a connected device**
   - Enable **Developer Options** and **USB Debugging** on your Android phone
   - Connect via USB
   - Press the **▶ Run** button in Android Studio

### Install on any Android phone (sideload)
1. Copy `app-debug.apk` to your phone
2. On the phone: **Settings → Security → Install unknown apps** → enable for your file manager
3. Tap the APK file to install

---

## Data Storage

All user data is stored locally on the device using the browser's `localStorage` API via Android WebView's DOM storage. No data is sent to any server. No internet connection is required after the first build.

Data stored:
| Key | Contents |
|---|---|
| `wt_v7_entries` | All weight log entries (JSON array) |
| `wt_v7_name` | User's display name |
| `wt_v7_target` | Target weight (kg) |
| `wt_v7_height` | Height (cm) for BMI calculation |
| `wt_ob_done` | Onboarding completion flag |

---

## Customisation

The entire UI lives in a single file: `app/src/main/assets/index.html`. You can edit it directly to:

- Change colour scheme (CSS variables at the top of the `<style>` block)
- Add new tabs or features
- Modify the chart appearance (Chart.js config in the JS section)
- Adjust the onboarding flow

After editing, rebuild the APK in Android Studio.

---

## Contributing

Pull requests are welcome! If you'd like to suggest a feature or report a bug, please open an issue first.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

<div align="center">

Built with ❤️ by **Saumyajyoti**

</div>

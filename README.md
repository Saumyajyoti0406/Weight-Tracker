# ⚡ Weight Tracker — Personal Android App

<div align="center">

![Weight Tracker](https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Language](https://img.shields.io/badge/Language-Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![WebView](https://img.shields.io/badge/UI-WebView%20%2B%20HTML%2FJS-00FFE0?style=for-the-badge)
![Min SDK](https://img.shields.io/badge/Min%20SDK-24%20(Android%207)-blue?style=for-the-badge)

**A personal weight tracking Android app with a neon dark aesthetic, BMI calculator, goal tracking, monthly/weekly charts, and local Excel export.**

</div>

---

## 📱 Screenshots

> *Dark neon aesthetic with animated geometric background*

| Onboarding | Dashboard | Charts | Export |
|:---:|:---:|:---:|:---:|
| First launch profile setup | BMI + Goal + Stats | Monthly & Weekly | Downloads to device |

---

## ✨ Features

### 🏁 First Launch Onboarding
- One-time profile setup — name, height, and goal weight
- Your name appears as a giant ghost text behind the setup card
- Data persists forever after setup

### ⚖️ Weight Logging
- Log weight by date — today or any past date
- Future dates are locked automatically
- Edit existing entries by re-logging the same date
- Delete any entry with one tap

### 📊 BMI Tracker
- Auto-calculated from your logged weight + height
- Colour-coded categories: Underweight / Normal / Overweight / Obese
- BMI shown on every entry in the log

### 🎯 Goal Weight
- Set a target weight
- Neon progress bar showing how far you've come
- Shows percentage complete and kg remaining
- Red dashed goal line overlaid on the monthly chart

### 📈 Charts Tab
- **Monthly Progress** — line chart with goal line overlay
- **Weekly Averages** — bar chart grouped by week
- Navigate between months with arrow buttons
- LIVE button to jump back to current month

### 📋 Log Tab
- All entries sorted by most recent
- Month pills to filter by any month
- Daily change indicator (↑ red / ↓ cyan)
- BMI shown per entry

### ⬇️ Export Tab
- Export **all data** or **current month only**
- Saves as `.csv` directly to phone's **Downloads** folder
- Opens in Microsoft Excel or Google Sheets
- Includes: date, weight, BMI, category, daily change, change from start, weekly averages, and a full summary section

### 🎨 Design
- Animated neon geometric background (hexagons, triangles, rings, particles)
- Dual-layer neon grid with cyan scan line effect
- Neon colour palette: cyan `#00ffe0`, violet `#7b5cfa`, hot pink `#ff4d6d`
- Fully dark — `#050508` background

---

## 🏗️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Android wrapper | Java (Native Android Activity) |
| UI | HTML5 + CSS3 + Vanilla JavaScript |
| Charts | Chart.js 4.4.1 |
| Data storage | Android WebView `localStorage` |
| File export | Android `MediaStore` API (Android 10+) |
| Fonts | Google Fonts — Syne + Space Mono |

---

## 🚀 Build Instructions

### Prerequisites
- [Android Studio](https://developer.android.com/studio) (any recent version)
- Java installed (comes with Android Studio)
- Internet connection (first build only — to download Gradle + dependencies)

### Steps

1. **Clone or download** this repository

2. **Open in Android Studio**
   - File → Open → select the `WeightTrackerAPK` folder

3. **Wait for Gradle sync** (~1-2 min on first run)

4. **Build the APK**
   ```
   Build → Build Bundle(s)/APK(s) → Build APK(s)
   ```

5. **Find your APK at:**
   ```
   app/build/outputs/apk/debug/app-debug.apk
   ```

### Install on Android Phone
1. Transfer the APK to your phone (USB, WhatsApp, Google Drive, etc.)
2. On your phone: **Settings → Security → Install unknown apps** → enable
3. Tap the APK file → Install

---

## 📁 Project Structure

```
WeightTrackerAPK/
├── app/
│   └── src/main/
│       ├── assets/
│       │   └── index.html          # Full app UI (HTML + CSS + JS)
│       ├── java/com/saumyajyoti/weighttracker/
│       │   └── MainActivity.java   # Android WebView wrapper + file export bridge
│       ├── res/
│       │   ├── mipmap-*/           # App icons (all densities)
│       │   └── values/styles.xml   # Dark theme
│       └── AndroidManifest.xml
├── app/build.gradle                # Dependencies + Kotlin conflict fix
├── gradle.properties               # AndroidX + Kotlin stdlib fix
└── build.gradle
```

---

## 📊 Export Format

The exported `.csv` file includes:

```
Weight Tracker Export
Name: [Your Name]
Height: [height] cm
Goal Weight: [goal] kg
Exported: [date]

Date, Weight (kg), BMI, Category, Change from Previous (kg), Change from Start (kg), Weekly Avg (kg)
2026-03-01, 104.0, 32.1, Obese, , 0.0, 104.0
2026-03-02, 103.5, 31.9, Obese, -0.5, -0.5, 103.8
...

SUMMARY
Starting Weight, 104.0 kg
Latest Weight, 103.5 kg
Lowest Weight, 103.5 kg
...
```

---

## 🔧 Known Fixes Applied

| Issue | Fix |
|-------|-----|
| Kotlin stdlib duplicate class conflict | `resolutionStrategy` in `app/build.gradle` + `kotlin.stdlib.default.dependency=false` in `gradle.properties` |
| Charts not loading | Chart.js loaded via CDN `<script src>` tag |
| Data not updating after entry | `loadData()` called at start of every `render()` |
| Future dates accessible | HTML `input[max]` + JS double-check on submit |

---

## 📦 Data Storage

All weight entries are stored in the WebView's `localStorage` on-device. Data is:
- **Private** to the app
- **Persists** between app restarts
- **Lost only** if the app is uninstalled
- **Exportable** anytime via the Export tab

---

## 👤 Author

**Saumyajyoti** — personal project for tracking weight progress

---

## 📄 License

This is a personal project. Feel free to fork and customize for your own use.

---

<div align="center">
Built with 💚 and a lot of neon
</div>

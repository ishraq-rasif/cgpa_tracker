# CGPA Tracker

![Build APK](https://github.com/YOUR-USERNAME/cgpa-tracker/actions/workflows/build-apk.yml/badge.svg)
![Platform](https://img.shields.io/badge/platform-Android-3ddc84)
![License](https://img.shields.io/badge/license-MIT-blue)

A small, offline-first Android app for tracking semester GPA and cumulative CGPA on the 4.00 scale, and for predicting next semester's result subject by subject.

<!-- Add screenshots here: create a /screenshots folder, then use
![Dashboard](screenshots/dashboard.png) -->

## Features

- **Semester results:** record courses with credit hours and letter grades. Semester GPA and overall CGPA update instantly.
- **CGPA to 4 decimals:** the overall figure is shown as 3.9094, not rounded to 2 places.
- **Locked results:** completed semesters are read-only. An explicit, confirmed "Unlock" is there for correcting typos.
- **Next-semester prediction:** add each subject with its credits and expected grade to see the predicted semester GPA and the resulting CGPA.
- **Target planner:** enter a target CGPA and see the GPA you need next semester, or whether the target is out of reach.
- **Trend chart:** semester GPA and running CGPA side by side, with the prediction drawn as a dashed bar.
- **Private by design:** no account, no server. Data is stored on the device.

## Grading scale

| Grade | Points | Grade | Points |
|-------|--------|-------|--------|
| A+ | 4.00 | C+ | 2.50 |
| A | 3.75 | C | 2.25 |
| A- | 3.50 | D | 2.00 |
| B+ | 3.25 | F | 0.00 |
| B | 3.00 | | |
| B- | 2.75 | | |

Semester GPA = Σ(grade point × credits) ÷ Σ credits. CGPA applies the same formula across all graded courses. Courses with no grade selected are ignored.

## Install

1. Open the [latest release]((https://github.com/ishraq-rasif/cgpa_tracker/blob/main/cgpa_tracker.apk)) on your phone.
2. Download `app-debug.apk`.
3. Open the file and allow installation from unknown sources if Android asks.

## Build from source

The app is a single HTML page (`www/index.html`) wrapped for Android with [Capacitor](https://capacitorjs.com/).

### With GitHub Actions (no local setup)

Every push runs the **Build APK** workflow. When it finishes, download `cgpa-tracker-apk` from the run's **Artifacts** section.

### Locally

Requires Node 18+, JDK 17 and the Android SDK (Android Studio installs it).

```bash
npm install
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
```

The APK is written to `android/app/build/outputs/apk/debug/app-debug.apk`.

## Project structure

```
.
├── www/index.html            # the whole app: UI, logic and styles
├── capacitor.config.json     # app id and name
├── package.json              # Capacitor dependencies
└── .github/workflows/
    └── build-apk.yml         # CI build that produces the APK
```

## Data and privacy

Grades are saved in the app's local storage on your device. Nothing is uploaded. Uninstalling the app or clearing its storage deletes the data. Fonts are fetched from Google Fonts when online and fall back to system fonts offline.

## Customising

- **Grade scale:** edit the `G` object at the top of the script in `www/index.html`.
- **Starting data:** edit the `seed()` function in the same file.
- **App name or id:** edit `capacitor.config.json`.

## License

Released under the [MIT License](LICENSE).

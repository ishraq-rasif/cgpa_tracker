# CGPA Tracker – APK project

## Easiest: build the APK online (no installs)
1. Create a free account at github.com and make a new empty repository.
2. Upload every file and folder from this zip (keep the `.github` folder). Use "Add file > Upload files" and drag everything in.
3. Open the repository's **Actions** tab. The "Build APK" run starts by itself (about 3–5 minutes).
4. Open the finished run, download **cgpa-tracker-apk** from Artifacts, unzip it and copy `app-debug.apk` to your phone.
5. On the phone, open the file and allow "Install unknown apps" when asked.

## Or build locally
Needs Node 18+, JDK 17 and Android Studio.
    npm install
    npx cap sync android
    cd android && ./gradlew assembleDebug
APK: android/app/build/outputs/apk/debug/app-debug.apk

## Updating the app
Replace `www/index.html`, then build again. Your saved grades live inside the installed app, so uninstalling it erases them.

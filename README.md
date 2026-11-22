# Expense Tracker

A simple, offline expense tracker: add / edit / delete expenses, browse them month by month,
search, filter and sort, and see a category pie chart. Data is stored on-device (localStorage).
Works in any browser and as an Android app.

## Download (Android)

1. Open the [**Releases**](../../releases/latest) page.
2. Download `ExpenseTracker-vX.Y.Z.apk` onto your phone.
3. Open the file. If Android blocks it, tap **Settings** and allow **Install unknown apps**
   for your browser / file manager, then go back and tap **Install**.
4. Open **Expense Tracker**.

Requires Android 7.0 (API 24) or newer. Updates install over the previous version and keep your data.
Uninstalling the app deletes its saved expenses.

## Use in a browser

Open `www/index.html` in any browser. No build step needed.

## Build the APK yourself

**Automatically (GitHub Actions):** push a tag like `v1.0.0` and the workflow in
`.github/workflows/build-apk.yml` builds the APK and attaches it to a Release.

**Locally:** install Node 22+, JDK 21 and Android Studio (for the Android SDK), then:

```bash
npm install
npx cap sync android
cd android && ./gradlew assembleDebug
# APK: android/app/build/outputs/apk/debug/app-debug.apk
```

## Project layout

| Path | What it is |
|------|------------|
| `www/` | The web app (`index.html`, bundled Chart.js) |
| `android/` | Capacitor Android project |
| `capacitor.config.json` | App id and name |
| `.github/workflows/build-apk.yml` | CI that builds the APK |

## Notes

- The APK is signed with a public debug key so every build has the same signature. It is fine
  for sideloading, but not for Google Play (see Capacitor's docs on release signing).
- Chart.js (MIT) is bundled in `www/` so the app works without internet.

## License

MIT, see [LICENSE](LICENSE).

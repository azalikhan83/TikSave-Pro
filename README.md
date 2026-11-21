# TikSave Pro (Android starter)

A functional, dark-themed downloader for **authorized direct video files**, supporting multiple URLs, Select All, individual downloads, and ZIP export. This project does **not** scrape TikTok, remove watermarks, bypass TikTok restrictions, or claim that TikTok profile URLs expose downloadable originals.

## Build on a computer (recommended)

Requires Node.js 20+, JDK 17, Android Studio and Android SDK.

```bash
npm install
npm run build
npx cap add android
npx cap sync android
npx cap open android
```

In Android Studio: Build > Build Bundle(s) / APK(s) > Build APK(s). For a signed release use Build > Generate Signed Bundle / APK.

Android command-line alternative after SDK configuration:

```bash
cd android
./gradlew assembleDebug
```

Debug APK: `android/app/build/outputs/apk/debug/app-debug.apk`.

## Android phone only

Use a remote Linux build environment or GitHub Actions Android build runner. GitHub Actions can install Node 22 and Java 17, build Vite, run `npx cap add android && npx cap sync android`, and build `./gradlew assembleDebug` (see included workflow). This avoids needing Android Studio on the phone. Download the build artifact from the Actions run.

## Limitations

- Input URLs must point directly to authorized `.mp4`, `.webm`, or `.mov` files. TikTok watch/share links are not direct video file URLs.
- Remote hosts must permit cross-origin downloads in WebView; some hosts block these. A secure server-side proxy for allowlisted authorized origins can be added later.
- Files are shared from app cache using Android's Share sheet. Choose Files or another storage app to persist them.
- ZIP generation uses device memory; for hundreds of HD videos, implement streaming native ZIP processing or a server-side job.
- TikTok Login Kit + Display API require an approved developer app, OAuth redirect, user consent and server-side token handling. Public video metadata is not a license or a downloadable original media file. No OAuth backend is bundled.
- Download quality is the source quality; no upscaling or watermark removal is performed.

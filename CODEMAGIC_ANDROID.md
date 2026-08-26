# Build ROMA FLOW AI APK from a phone

This repository is prepared for Codemagic. It creates the native Android project in the cloud, so you do not need Android Studio on your phone.

## 1. Upload to GitHub
Create a GitHub repository and upload the contents of this folder (the files `package.json`, `capacitor.config.json`, `codemagic.yaml`, `web/`, etc. should be at the repository root).

## 2. Add the repository to Codemagic
Codemagic → Add application → GitHub → select `roma-flow-ai` → use the `codemagic.yaml` configuration.

Codemagic's current documentation supports `codemagic.yaml` at the repository root and Android Gradle builds; `assembleDebug` produces an installable APK artifact. See the official Android and Capacitor guides.

## 3. First build — Demo APK
Leave `API_BASE_URL` empty. The app will run in **Demo Mode** with the synthetic Trevi scenario included in the existing ROMA FLOW v1.2 prototype. This is useful for verifying the Android UI and navigation.

## 4. Connect the real backend later
Set `API_BASE_URL` to your HTTPS API, for example:

`https://api.example.com`

The web client will then request:

`/api/v1/city-status`
`/api/v1/recommendations`

## 5. Download the APK
After the build completes, download the `app-debug.apk` artifact from Codemagic and open it on Android to install.

## Important
Do not commit a keystore or production passwords to GitHub. For a production release, use Codemagic Android signing and build `assembleRelease`. Codemagic's official documentation requires the signing setup for public distribution.

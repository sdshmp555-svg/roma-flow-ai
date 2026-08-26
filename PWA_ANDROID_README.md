# ROMA FLOW AI — Android/PWA Build

This package adds an installable Progressive Web App layer to the Pilot-Ready v1.2 backend.

## What was added
- `web/manifest.webmanifest`
- `web/sw.js` service worker with offline shell caching
- `web/static/icons/icon-192.png`
- `web/static/icons/icon-512.png`
- Mobile-responsive dashboard improvements
- FastAPI static asset mounting
- Manifest + service-worker endpoints

## Run on a computer
```bash
python -m venv .venv
# activate the venv
pip install -r requirements.txt
uvicorn app.main:app --host 0.0.0.0 --port 8000
```
Open `http://localhost:8000`.

## Install on Android
For Chrome to offer "Install app", the site should be served from a secure origin (HTTPS) in normal deployment. A local HTTP origin may not expose the install prompt on a phone.

Recommended next deployment path:
1. Deploy the same container to an HTTPS host.
2. Open the URL in Chrome on Android.
3. Choose **Install app / Add to Home screen**.
4. The installed PWA runs as a standalone mobile app shell while the same ROMA FLOW backend provides AI, forecast and recommendation APIs.

## Important
This is a PWA package, not a signed native Android APK. The backend and AI engine are unchanged.

## Capacitor / Codemagic
This package is now Capacitor-ready for Android cloud builds. See `CODEMAGIC_ANDROID.md` and `codemagic.yaml`.

# Privacy HQ

A data-protection and cybersecurity simulation game. Run a company, install protections, handle privacy incidents, and reach **100% Customer Trust** to finish a level. Level 2 starts with 250 coins and 0% trust.

Designed for **phones in portrait** (HQ view opens at 175% zoom). Runs as a **web game (GitHub Pages)** and as an **Android app (APK built by GitHub Actions)** from the same code in `www/`.

## 1. Put it on GitHub

```bash
git init
git add .
git commit -m "Privacy HQ"
git branch -M main
git remote add origin https://github.com/<you>/<repo>.git
git push -u origin main
```

## 2. Play in the browser (GitHub Pages)

1. In the repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
2. Push to `main` (or run **Actions → Deploy web version → Run workflow**).
3. The game is live at `https://<you>.github.io/<repo>/`. It is also an installable PWA (works offline).

## 3. Get the Android APK

1. Push to `main`, or run **Actions → Build Android APK → Run workflow**.
2. When the run finishes, open it and download **privacy-hq-apk** from *Artifacts*.
3. Copy `privacy-hq.apk` to your phone and install it (allow "Install unknown apps" for your browser or file manager when prompted).

For a downloadable release, push a tag: `git tag v1.0.0 && git push --tags`. The APK is attached to the release.

## Run locally

```bash
npm install
npm start          # serves www/ in the browser
```

Android Studio build (optional): `npm install && npx cap add android && npx cap sync android && npx cap open android`.

## Project layout

| Path | Purpose |
|---|---|
| `www/index.html` | The whole game |
| `www/manifest.json`, `www/sw.js`, `www/icon*` | PWA / offline support |
| `assets/` | Source images for Android launcher icons |
| `capacitor.config.json` | Android wrapper settings (app id `com.privacyhq.game`) |
| `.github/workflows/pages.yml` | Deploys the web version |
| `.github/workflows/android.yml` | Builds the APK |

## Notes

- The APK is a **debug build**, fine for installing directly. For Google Play you need a signed release AAB (keystore + `./gradlew bundleRelease`).
- Change the app id in `capacitor.config.json` before publishing to Play.
- After editing the game, bump `CACHE` in `www/sw.js` so web users get the update.

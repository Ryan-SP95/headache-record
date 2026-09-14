# Headache Record

A private headache log. Everything stays in the browser on the device it was entered on — there is no server, no account, and nothing is uploaded.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app — markup, styles, and logic in one file |
| `manifest.webmanifest` | Name, icons, and colours used when it's installed to a home screen |
| `sw.js` | Service worker; caches the app so it opens with no connection |
| `icon-192.png`, `icon-512.png` | App icons |
| `apple-touch-icon.png` | Home screen icon for iOS |

## Run it locally

A service worker needs a real origin, so opening `index.html` directly from the file system won't register it.

```
cd headache-app
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Deploy it

Any static host works. With the setup you already have:

1. Push this folder to a GitHub repo.
2. Import the repo in Vercel — no build command, no framework preset, output directory is the repo root.
3. Open the deployed URL on your phone and install it:
   - **iOS (Safari):** Share → Add to Home Screen
   - **Android (Chrome):** the install prompt appears, or the menu → Install app

Serving over HTTPS is required for the service worker. Vercel does that by default.

## After you change anything

Bump `CACHE` in `sw.js` (`v1` → `v2`). Otherwise installed copies keep serving the cached version and your change never appears.

## Backups matter more than usual

The entries live only in that browser's storage. Clearing site data, switching phones, or a browser evicting storage will take the log with it. **Save a backup file** on the Summary tab now and then — it's the only way to move entries to a new device or recover them.

On iOS this is not theoretical: Safari can clear a site's storage after about a week of no use. Installing to the home screen and opening it regularly avoids that, but keep backups anyway.

## What this is not

It records and counts what you enter. It does not diagnose, interpret, or assess anything, and it isn't a substitute for care from a clinician.

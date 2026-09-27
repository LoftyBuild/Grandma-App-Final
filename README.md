# Currency Converter — Android app for Grandma

This folder is a small "installable web app" (PWA) version of your Python
converter. It uses live exchange rates from frankfurter.dev (free, no API
key needed) and, once hosted, can be installed on an Android phone so it
looks and behaves like a normal app — its own icon, opens full-screen,
no browser bar.

## Files
- `index.html` — the app itself
- `manifest.json` — tells the phone the app's name/icon/colors
- `sw.js` — lets it install and keep working if the connection blips
- `icon-192.png`, `icon-512.png` — app icon

## Step 1 — Put it online (needed once, free, ~5 minutes)
A phone can only "install" a page that's served over HTTPS, not a file
sitting on your computer. Easiest free options:

**GitHub Pages**
1. Create a new GitHub repo (e.g. `currency-app`).
2. Upload all 5 files in this folder to it.
3. Repo Settings → Pages → set source to the `main` branch → Save.
4. GitHub gives you a URL like `https://yourname.github.io/currency-app/`.

**Netlify (drag-and-drop, no account needed for a quick test)**
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. Netlify gives you a live URL immediately.

## Step 2 — Install it on grandma's phone (the simple route)
1. Open the URL from Step 1 in Chrome on her Android phone.
2. Tap the **⋮** menu → **"Install app"** (or "Add to Home screen").
3. Confirm. An icon now sits on her home screen like any other app —
   tapping it opens full-screen, no address bar, no browser chrome.

For most grandmas this is indistinguishable from a "real" app and needs
no app store, no APK, and no further building.

## Step 3 (optional) — Turn it into an actual installable APK file
If you specifically want a `.apk` file you can send her directly (e.g. via
WhatsApp) instead of a link:
1. Go to https://www.pwabuilder.com
2. Paste your Step-1 URL and click **Start**.
3. Once it scores your app, choose **Android** → **Download package**.
4. You'll get a signed APK/AAB you can send her — she taps it, allows
   "install from unknown sources" once, and it installs exactly like an
   app from the Play Store, with its own icon in the app drawer.

## Compiling the original desktop version
Your existing `customtkinter` script still works great as a Windows/Mac
app — that part doesn't need any of the above:
```
pip install pyinstaller
pyinstaller --onefile --windowed --name "CurrencyConverter" your_script.py
```
The `.exe` (or Mac app) appears in the `dist/` folder.

## Note on your original script
`API_KEY = "79.116.218.180"` looks like a stray IP address rather than a
real currencyapi.com key, which is why that call would have failed. The
web version above sidesteps this entirely by using frankfurter.dev,
which needs no key at all.

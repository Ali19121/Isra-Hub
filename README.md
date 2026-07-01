# Isra Portal Hub (PWA)

An installable Progressive Web App that brings your 4 portals into **one app**:

1. Mail Correspondence Management Portal
2. School Test Portal
3. Fehm-ul-Quran Course Management Portal
4. Schools Management & ERP Portal (Coming Soon — currently disabled)

Each portal opens on its own original GitHub Pages site (no data or logins are copied). This app is purely a **launcher/hub** that organizes them in one place with a home-screen icon.

---

## Important: why Google Drive won't work for this

A PWA becomes installable only when it's served as **live HTTPS files with a real web address** — the browser needs to fetch `manifest.json`, register the `service-worker.js`, and verify the site's origin before it will offer "Install App."

Google Drive doesn't do this. Opening an HTML file from Drive loads it inside a sandboxed preview frame with no real origin, so the manifest and service worker are ignored — you'd only get a browser bookmark, not a real installable app.

## Recommended: Netlify Drop (as easy as Drive, but actually works)

No account, no git, no command line — just drag and drop, exactly like uploading to Drive:

1. Go to **[app.netlify.com/drop](https://app.netlify.com/drop)** in your browser.
2. Drag the whole `isra-hub` folder (the one containing `index.html`) onto the page.
3. Netlify uploads it and gives you a live HTTPS link in a few seconds, e.g. `https://random-name-123.netlify.app`.
4. Open that link on your phone.
5. Tap **"Install App"** in the hub, or use your browser's **"Add to Home Screen"** option.

That's it — no redeploying needed unless you want to update the content later (just drag the folder again).

### Optional: a cleaner link
Once uploaded, you can rename the site (Site settings → Change site name) to something like `isra-portal-hub.netlify.app`, and optionally create a free Netlify account so the site doesn't expire.

---

## Alternative: GitHub Pages

If you'd still prefer GitHub Pages:

1. Create a new repository (e.g. `isra-hub`).
2. Upload all files in this folder (`index.html`, `manifest.json`, `service-worker.js`, `offline.html`, `icons/`).
3. Go to **Settings → Pages**, set Source to `main` branch, `/ (root)`, and save.
4. Your app goes live at `https://<your-username>.github.io/isra-hub/`.

---

## Installing on mobile

Once the link is live, open it in your phone's browser:

**Android (Chrome):**
- Tap the "Install App" button inside the hub, or
- Tap the ⋮ menu → **"Add to Home screen"** / **"Install app."**

**iPhone (Safari):**
- Tap the Share icon (☐↑) → **"Add to Home Screen."**

After installing, the app opens full-screen from your home screen icon — no browser address bar, just like a native app.

---

## Adding a new portal later (e.g. when ERP goes live)

Open `index.html`, find the `<ul class="registry">` section, and copy one of the existing `<li class="entry">` blocks. Update the `href`, icon, title, and description, and change the `stamp` class from `soon` to `live`.

---

## File structure

```
isra-hub/
├── index.html          ← main hub / dashboard
├── manifest.json        ← PWA install config
├── service-worker.js    ← offline shell caching
├── offline.html          ← no-internet fallback screen
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── icon-maskable-192.png
│   ├── icon-maskable-512.png
│   └── apple-touch-icon.png
└── README.md
```

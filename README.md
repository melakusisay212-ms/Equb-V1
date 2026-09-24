# Equb Admin – Installable App for Everyone

A modern, **installable** digital organizer for traditional Ethiopian Equbs (ዕቁብ).

Each person installs the app on their phone and logs in with **their own Google account**.  
Their Equb data is stored **only in their personal Google Drive**.  
When they log in again (any device), the app restores their data automatically.

**No central server. No shared database. Fully private per user.**

---

## How it works for multiple people

1. Person A installs the app → logs in with **A’s Google** → data goes to **A’s Google Drive**
2. Person B installs the same app → logs in with **B’s Google** → data goes to **B’s Google Drive**
3. They never see each other’s data
4. If Person A opens the app on a new phone and logs in with the same Google, all their Equbs come back

This is exactly how Google Docs / Drive works for each user.

---

## Install on Phone (PWA)

### Android (Chrome)
1. Open the deployed website
2. Tap the menu (⋮) → **Install app** or **Add to Home screen**
3. The app appears like a normal app icon

### iPhone (Safari)
1. Open the website in Safari
2. Tap the Share button → **Add to Home Screen**

---

## Deploy with GitHub Actions

1. Create a new **public** GitHub repository (e.g. `equb-admin`)
2. Upload all files from this folder
3. Go to **Settings → Pages** → Source: **GitHub Actions**
4. Push to `main` — the workflow will deploy automatically

Your public link will be:  
`https://YOUR_USERNAME.github.io/equb-admin/`

---

## Enable Google Login (Required for multi-device sync)

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a project
3. Enable **Google Drive API**
4. Create **OAuth Client ID** → Application type: **Web application**
5. Add **Authorized JavaScript origins**:
   - `http://localhost`
   - `https://YOUR_USERNAME.github.io`
6. Copy the Client ID
7. Open `index.html` and replace:

```js
const GOOGLE_CLIENT_ID = 'YOUR_GOOGLE_CLIENT_ID.apps.googleusercontent.com';
```

8. Commit & push — GitHub Actions redeploys automatically

---

## Project Structure

```
equb-admin/
├── index.html              ← Main app
├── manifest.json           ← PWA install config
├── sw.js                   ← Service Worker (offline + install)
├── icon-192.png
├── icon-512.png
├── README.md
└── .github/workflows/
    └── deploy.yml          ← Auto-deploy to GitHub Pages
```

---

## Features

- Installable on Android & iPhone
- Google Login → data stored in **that user’s** Google Drive
- Automatic restore when logging in again
- Offline support (works without internet after first load)
- Create multiple Equbs
- Payment tracking, lottery, SMS reminders, calendar
- CSV + PDF export
- Themes + Amharic support

---

Built for Ethiopian community organizers who want a private, installable, zero-cost digital ledger.

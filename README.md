# My Paintings — Personal catalog PWA

A private, password-protected web app for cataloging your paintings. Install to your phone's home screen like a real app. Works offline.

## What's inside

- `index.html` — the whole app
- `manifest.json` — makes it installable as an app
- `sw.js` — service worker for offline support
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` — app icons

All your data stays **on your device** in IndexedDB. Nothing gets sent to any server. Ever.

## Features

- Password gate (hashed + salted, stored locally — no recovery, write it down)
- Multiple images per painting (main + detail shots)
- Fields: title, year, medium, dimensions, category, series, colors, tags, description, location, status, price, sold date, buyer, notes
- Full-text search across every field at once
- Filter by category, series, status
- Sort by date, title, year
- Grid and list views
- Export / import JSON backup (with images baked in)
- Works offline once installed
- Light design, mobile-first, dark-mode aware

---

## Getting it onto your phone — step by step

### Step 1: Get the files
You should have a folder with all 5 files listed above. Keep them together.

### Step 2: Create a free GitHub account
Go to [github.com](https://github.com) and sign up if you don't have an account.

### Step 3: Create a new repository
1. Click the `+` in the top right → **New repository**
2. Name it something private-sounding like `my-art` or `paintings-private` (this becomes part of your URL)
3. Set it to **Public** (required for free Pages hosting — but remember, your data never leaves your phone, and access is password-gated)
4. Check **"Add a README file"**
5. Click **Create repository**

### Step 4: Upload the app files
1. In your new repo, click **Add file → Upload files**
2. Drag all 5 files (`index.html`, `manifest.json`, `sw.js`, and all 3 icon PNGs) into the upload area
3. Click **Commit changes** at the bottom

### Step 5: Enable GitHub Pages
1. In your repo, click **Settings** (top tabs)
2. In the left sidebar, click **Pages**
3. Under "Source", select **Deploy from a branch**
4. Branch: **main**, folder: **/ (root)**
5. Click **Save**
6. Wait 1–2 minutes. Refresh the Pages settings page — you'll see a green box with your URL like `https://yourusername.github.io/my-art/`

### Step 6: Open it on your phone and install
1. On your iPhone or Android, open that URL in **Safari** (iOS) or **Chrome** (Android)
2. Set your password when prompted (write it down — there's no recovery)
3. Install to home screen:
   - **iPhone (Safari):** tap the share button → **Add to Home Screen**
   - **Android (Chrome):** tap the three-dot menu → **Install app** or **Add to Home screen**
4. Launch from your home screen — it runs full-screen like a real app

---

## Important usage notes

**Back up regularly.** Tap the menu (⋮) → **Export backup**. This downloads a single JSON file containing all paintings and images. Save it somewhere safe (email to yourself, iCloud, Dropbox, external drive). If your phone breaks or browser data gets cleared, this is your only recovery path.

**500+ paintings with multiple images each is a lot of data.** Images are auto-resized to 1600px on the longest edge at 85% JPEG quality, which is good for viewing. Modern phones typically allow 1–2 GB of storage per site. The storage meter at the bottom of the app shows your usage. If you approach the limit, export a backup, and we can add finer image quality controls.

**The password protection is a privacy lock, not bank-level security.** It keeps casual eyes out. Since your data never leaves your phone, this is fine for a personal collection — but don't put truly sensitive info (like customer payment details) in the notes field.

**Transfer between devices:** Install the app on the second device, open it, tap menu → **Import backup**, select your JSON file. You can choose to merge or replace.

**To update the app later:** If I give you a new `index.html`, just upload the new file to GitHub (replacing the old one). Your data stays untouched — it lives in your phone's browser storage, separate from the app code.

---

## Troubleshooting

- **"Add to Home Screen" not showing the app icon:** Make sure you opened the site in Safari, not Chrome, on iPhone. iOS only supports PWA install from Safari.
- **App won't load after going offline:** The service worker needs one successful online load first to cache the app. After that, offline works.
- **Lost password:** There's no recovery. You'll need to wipe the app's data (browser settings → site data → clear) and start over. This is why export backups matter.
- **GitHub Pages URL not working yet:** First deploy takes up to 10 minutes. Check **Settings → Pages** for status.

---

Built for you. Have fun with it.

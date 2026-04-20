# Works — Private catalog

A private, password-protected web app for cataloging your works. Dark authentication gate, white gallery interior, PDF export with museum-style layout. Installs to your phone's home screen like a real app. Works offline.

## What's inside

- `index.html` — the whole app
- `manifest.json` — makes it installable
- `sw.js` — service worker for offline support
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` — default app icons
- (Optional) `logo.png` or `logo.svg` — your own logo file, drop it in anytime

All data lives on your device in IndexedDB. Nothing is sent to any server.

---

## Adding your logo

When you're ready, put your logo in the folder as one of these filenames:

- `logo.svg` (recommended — scales perfectly)
- `logo.png` (use a transparent PNG, ideally 512×512 or larger)
- `logo.jpg` / `logo.jpeg` / `logo.webp`

The app automatically detects the first one it finds. It appears on:

- The dark authentication gate, with a dramatic fade-in
- The top-left of the main gallery view

Until you add a logo file, a placeholder circle marked "LOGO" appears on the gate.

To upload your logo later:
1. Go to your GitHub repository
2. Click **Add file → Upload files**
3. Drag in your `logo.png` (or `.svg`)
4. Commit changes
5. Wait ~1 minute, then reload the app

---

## Features

**Authentication**
- Dark, minimalist gate with dramatic logo fade-in
- Password hashed + salted locally (PBKDF2, 150k iterations)
- No password recovery — write it down

**Gallery interior**
- White, gallery-style interface
- Monospace labels, generous whitespace
- Multiple images per work (main + detail shots)
- Fields: title, year, medium, dimensions, category, series, colors, tags, description, location, status, price (USD), sold date, buyer, notes
- Full-text search across everything
- Filter by category, series, status
- Sort by date, title, year
- Grid and list views

**PDF export**
- Per-work: landscape page with image left, specs right, in Times New Roman
- Layout exactly as you specified:
  - Line 1: **Title** (bold)
  - Line 2: Medium
  - Line 3: Dimensions · Series
  - (3 blank lines)
  - Price in USD
- Bulk export: all currently filtered/sorted works into one multi-page PDF
- Single work: export from the detail view ("PDF" button in the header)

**Data**
- JSON backup/restore (includes images)
- Storage meter at the bottom
- Works offline once installed

---

## Deploy to your phone

(Skip this if you've already set up GitHub Pages — just re-upload the new files to your existing repo.)

### Step 1: Create a GitHub account
[github.com](https://github.com) — sign up, verify email, pick "Free" plan.

### Step 2: Create a repository
Click **+** top right → **New repository** → name it `works` or similar → **Public** → check **Add a README** → **Create repository**.

### Step 3: Upload the app files
In your repo, click **Add file → Upload files**. Drag in all files from this folder (6 core files + your optional logo). Scroll down and click **Commit changes**.

### Step 4: Enable GitHub Pages
In your repo, click **Settings** (top row, right side, gear icon). In the left sidebar, click **Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, Branch to **main**, folder to **/ (root)**. Click **Save**.

Wait 1–3 minutes. Refresh the Pages settings page. You'll see a green box with your URL: `https://yourusername.github.io/works/`.

### Step 5: Open and install on your phone
On your phone, open that URL in **Safari** (iPhone) or **Chrome** (Android). Create a passphrase. Then:

- **iPhone:** Share button at the bottom of Safari → **Add to Home Screen**
- **Android:** Three-dot menu in Chrome → **Install app**

Launch from your home screen. You'll see the dark gate with your logo fading in, then the white gallery after you enter your passphrase.

---

## Important notes

**Back up regularly.** Menu → **Backup (JSON)** downloads everything (paintings + images) as one file. Save it to email, iCloud, or an external drive. If your phone browser data gets cleared, this is your only recovery path.

**500+ works with multiple images each is a lot of data.** Images auto-resize to 1600px at 85% JPEG quality. The storage meter shows usage. Modern phones allow 1–2 GB per site. Export backups before you get anywhere near the limit.

**Password is a privacy lock, not encryption.** It keeps casual eyes out; it doesn't encrypt your data on disk. For a personal catalog on your own phone this is fine.

**Updating the app later.** If you get a new `index.html` from me, just replace the old one on GitHub. Your collection data (stored in your phone's browser) is completely separate from the app code and won't be touched.

---

## PDF export details

The PDF library (jsPDF) loads from a CDN the first time you use it. It gets cached by the service worker, so after the first use it works offline too.

Price formatting: if you enter a raw number (like `2400`), the PDF will render it as `$2,400 USD`. If you enter a full string (`$2,400` or `2,400 USD`), it's used as-is. This gives you flexibility while keeping the default output clean.

If a work has no price, the price line is skipped on the PDF.

---

Have fun with it. Let me know what else you want changed.

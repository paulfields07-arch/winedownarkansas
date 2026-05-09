# WineDown Arkansas 🍷

Arkansas's guide to wineries licensed to ship wine directly to your door.
Verified against Arkansas ABC permit records, updated monthly.

---

## Deploy to Vercel (Step-by-Step)

### Step 1 — Create a GitHub Account
Go to [github.com](https://github.com) and sign up for a free account if you don't have one.

### Step 2 — Create a New Repository
1. Click the **+** icon in the top right → **New repository**
2. Name it `winedownarkansas`
3. Set it to **Public**
4. Click **Create repository**

### Step 3 — Upload Your Files
1. On your new repo page, click **uploading an existing file**
2. Drag and drop ALL files and folders from this zip into the upload area:
   - `src/` (folder)
   - `public/` (folder)
   - `index.html`
   - `package.json`
   - `vite.config.js`
   - `.gitignore`
3. Click **Commit changes**

### Step 4 — Deploy on Vercel
1. Go to [vercel.com](https://vercel.com) and sign up with your GitHub account
2. Click **Add New Project**
3. Find and select your `winedownarkansas` repository
4. Vercel will auto-detect it as a Vite/React project — no config needed
5. Click **Deploy**
6. Your site will be live at `winedownarkansas.vercel.app` in about 60 seconds

### Step 5 — Connect Your Custom Domain
1. In Vercel, go to your project → **Settings** → **Domains**
2. Add `winedownarkansas.com`
3. Vercel will show you DNS records to add at your domain registrar
4. Add those records (usually takes 10–30 minutes to go live)

---

## Making Updates

Whenever you need to update the winery list or any content:
1. Edit `src/App.jsx` in GitHub (click the file → pencil icon)
2. Commit the change
3. Vercel automatically redeploys — live in about 30 seconds

---

## Local Development (Optional)

If you want to preview changes on your computer before pushing:

```bash
npm install
npm run dev
```

Then open [http://localhost:5173](http://localhost:5173)

---

## Project Structure

```
winedownarkansas/
├── public/           # Static assets
├── src/
│   ├── App.jsx       # Main app — all winery data and UI lives here
│   └── main.jsx      # React entry point (don't edit this)
├── index.html        # HTML shell
├── package.json      # Dependencies
└── vite.config.js    # Build config
```

---

## Data Updates

All winery data is in `src/App.jsx` in the `WINERIES` array at the top of the file.

To add a new winery, add an object to the array:
```js
{
  id: 122,
  permit: "27XXX-01",
  name: "Winery Name",
  city: "City",
  state: "CA",
  approved: "2026-05-01",
  url: "https://www.winery.com",  // or null if unknown
  local: false                     // true only for Arkansas wineries
}
```

Permit data source: [Arkansas ABC Permit Changes](https://www.dfa.arkansas.gov/office/alcohol-beverage-control/permit-changes/)

---

*WineDown Arkansas is an independent information service and is not affiliated with the State of Arkansas.*
*Must be 21+ to visit. Please drink responsibly.*

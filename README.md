# Pitcher Training Tracker

Web app for logging pitcher training sessions from whiteboard photos. Uses Google Gemini AI (free tier) to parse the whiteboard, lets you confirm the data, and stores a history in this repo.

## One-Time Setup (5 minutes)

### 1. Create the GitHub repo

1. Go to github.com → **New repository**
2. Name it `pitcher-tracker` (or whatever you like)
3. Set it to **Public** (required for free GitHub Pages)
4. Click **Create repository**
5. Push these files to it:
   ```
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/pitcher-tracker.git
   git push -u origin main
   ```

### 2. Enable GitHub Pages

1. In your repo → **Settings** → **Pages**
2. Under "Branch", select `main` and folder `/root`
3. Click **Save**
4. Your site will be live at: `https://YOUR_USERNAME.github.io/pitcher-tracker`

### 3. Get a GitHub Personal Access Token

1. GitHub → **Settings** → **Developer settings** → **Personal access tokens** → **Tokens (classic)**
2. Click **Generate new token (classic)**
3. Give it a name (e.g. "Pitcher Tracker"), set expiration as desired
4. Check the **`repo`** scope
5. Click **Generate token** — copy it immediately

### 4. Get a Google Gemini API Key (FREE)

1. Go to **[aistudio.google.com/apikey](https://aistudio.google.com/apikey)**
2. Sign in with any Google account
3. Click **"Create API Key"** → "Create API key in new project"
4. Copy the key

**No billing required.** The free tier covers 15 requests/minute and 1500 requests/day — way more than you'll ever need for this.

### 5. Configure the App

1. Open your live site
2. Click the **⚙️** gear icon (top right)
3. Paste in:
   - Google Gemini API Key
   - GitHub Token
   - Your GitHub username
   - Repository name (e.g. `pitcher-tracker`)
4. Click **Save**

That's it. Keys are stored only in your browser's localStorage — never committed to the repo.

---

## Using the App

### Upload a Session
1. Go to **📸 Upload Session**
2. Select the session date
3. Drop or click to upload the whiteboard photo
4. Click **Parse Whiteboard** — Claude reads the photo automatically
5. Review the table: edit names, check/uncheck focus areas, set L/M/H intensity
6. Click **Confirm & Save**

### View Player History
1. Go to **📊 Player History**
2. See all players with their intent distribution (H/M/L stacked bars)
3. Click any player card for their full detail:
   - Total sessions + H/M/H breakdown
   - Intent distribution donut chart
   - Focus area breakdown (Velo/Delivery, Command, Pitch Design)
   - Chronological session log

---

## Data

All data lives in `data/training_log.json` in this repo. Every save creates a new git commit, so you have a full audit trail. You can export or edit the JSON directly if needed.

```json
{
  "sessions": [
    {
      "id": "2026-04-07-1712500000000",
      "date": "2026-04-07",
      "players": [
        { "name": "HALL, O", "velo_delivery": false, "command": false, "pitch_design": true, "intensity": "H" }
      ]
    }
  ]
}
```

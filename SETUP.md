# Setup — Annotations Website

A 4-step process to get your annotations site live, persistent, and password-protected.

---

## Step 1 — Create a free Supabase project

1. Go to [supabase.com](https://supabase.com) → **Start your project** → sign in with GitHub
2. Click **New project**, name it (e.g. `annotations`), choose any region, set a database password
3. Wait ~2 minutes for the project to provision
4. Go to **SQL Editor** (left sidebar) → **New query**
5. Open `supabase_migration.sql` from this folder, paste the entire contents, click **Run**
   - This creates your two tables (`sources`, `keywords`) and loads all 60 sources
6. Go to **Settings → API** (left sidebar)
7. Copy two values:
   - **Project URL** — looks like `https://abcdefghijkl.supabase.co`
   - **anon public key** — long string starting with `eyJ...`

---

## Step 2 — Add your keys to annotations.html

Open `annotations.html` in a text editor. Near the top of the `<script>` block, find:

```js
const SUPABASE_URL = 'https://YOUR_PROJECT.supabase.co';
const SUPABASE_KEY = 'YOUR_ANON_PUBLIC_KEY';
```

Replace with your actual values from Step 1. Save the file.

---

## Step 3 — Push to GitHub Pages

1. Create a new **public** repo at [github.com/new](https://github.com/new)
   - Name it something like `annotations` or `org-worldviews`
2. In Terminal, from the `concept-map` folder:
   ```bash
   git init
   git add annotations.html index.html supabase_migration.sql
   git commit -m "initial"
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```
3. In your repo on GitHub: **Settings → Pages → Source: Deploy from branch → main → / (root)** → Save
4. After ~1 minute your site is live at `https://YOUR_USERNAME.github.io/YOUR_REPO/annotations.html`

---

## Step 4 — Password protect with Netlify (optional)

GitHub Pages is public. If you want a password gate:

1. Go to [netlify.com](https://netlify.com) → **Add new site → Import an existing project → GitHub**
2. Select your repo → Deploy
3. In Netlify dashboard: **Site configuration → Access control → Site protection → Set password**
4. Share the URL + password with anyone you want to give access

---

## Daily workflow

- Open the site URL in any browser
- Click any row to expand it and read/edit the annotation
- Click the annotation text to edit; click elsewhere (or press Escape) to save
- Click the citation text to edit; works the same way
- Type `+ keyword` pills under each annotation to add tags
- Click `×` on a pill to remove it
- Click **+ Add** in the header to add a new source
- Click **Delete source** at the bottom of any detail panel to remove a source

All edits save automatically to Supabase (you'll see a "Saved" toast in the corner).

---

## Adding sources from existing PDFs

The most efficient workflow:

1. Read the paper, open the annotations site
2. Click the row to expand it (or add a new source)
3. Click the annotation text to start typing — write directly on the site
4. Save (click away) — it persists immediately to Supabase

No more switching between Word and the browser.

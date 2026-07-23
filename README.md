# Prosperly — deploy this site

This folder is a ready-to-deploy static site (just `index.html`). No build step needed.

## Option A: Vercel (recommended, free)

1. Go to https://vercel.com and sign up / log in (GitHub login is easiest).
2. Click **Add New → Project**.
3. If prompted for a Git repo: create a new GitHub repo, upload this folder's contents to it (see "Getting this into GitHub" below), then import that repo into Vercel.
   - Or, skip Git entirely: install the Vercel CLI (`npm i -g vercel`), run `vercel` inside this folder, and follow the prompts. This deploys directly from your machine.
4. Once deployed, go to your project → **Settings → Domains** → add `prosperlyventures.com`.
5. Vercel will show you DNS records (usually an A record or CNAME) — add those in your domain registrar's DNS settings (wherever you bought prosperlyventures.com).
6. DNS changes can take a few minutes to a few hours to propagate.

## Option B: Netlify (free)

1. Go to https://netlify.com and sign up / log in.
2. Drag and drop this whole folder onto the Netlify dashboard ("Deploy manually" / "Drag and drop your site output folder") — this is the fastest path, no Git needed.
3. Once deployed, go to **Site settings → Domain management → Add custom domain** → enter `prosperlyventures.com`.
4. Netlify will give you DNS records to add at your domain registrar.

## Getting this into GitHub (only needed for Option A via Git)

```bash
cd prosperly-site
git init
git add .
git commit -m "Initial Prosperly site"
git branch -M main
git remote add origin https://github.com/<your-username>/prosperly-site.git
git push -u origin main
```

Then import that repo in Vercel.

## Notes

- This is currently the marketing/landing page only. The interactive dashboard (`ProsperlyDashboard.jsx`) is a separate React component — deploying that as part of the same site would need a small build step (Vite), which I can set up next if you want the dashboard live at e.g. `prosperlyventures.com/app`.
- Update copy, contact info, or the "Get early access" button (currently non-functional) whenever you're ready to actually collect signups — I can wire that to an email capture (e.g. a Google Form, Airtable, or a simple backend) on request.

# Deploying Prosperly to Firebase Hosting (new project)

This mirrors the Lumora workflow, but pointed at a brand-new Firebase project for Prosperly.

## One-time setup

1. **Create the Firebase project**
   - Go to https://console.firebase.google.com
   - Click **Add project** → name it something like `prosperly` or `prosperly-ventures`
   - You can skip Google Analytics if you don't need it yet

2. **Install Firebase CLI** (skip if already installed from the Lumora setup)
   ```
   npm install -g firebase-tools
   firebase login
   ```

3. **Set up your local deploy folder** (same pattern as Lumora)
   ```
   mkdir C:\Users\vamsi\OneDrive\Desktop\prosperly-deploy
   cd C:\Users\vamsi\OneDrive\Desktop\prosperly-deploy
   firebase init hosting
   ```
   During `firebase init hosting`:
   - Choose **Use an existing project** → select the Prosperly project you just created
   - Public directory: `.` (current folder)
   - Configure as single-page app: **No** (unless you later add client-side routing for the dashboard)
   - Don't overwrite `index.html` if it asks (you'll copy your own in next)

   This creates `firebase.json` and `.firebaserc` in that folder, wired to the new project — same role as your `lumora-deploy` folder.

4. **Copy in the site file**
   ```
   copy /Y C:\Users\vamsi\Downloads\prosperly.html index.html
   ```
   (Save the landing page I gave you as `prosperly.html` in your Downloads first, same as you do for Lumora.)

## Every deploy after that (same rhythm as Lumora)

```
cd C:\Users\vamsi\OneDrive\Desktop\prosperly-deploy
copy /Y C:\Users\vamsi\Downloads\prosperly.html index.html
firebase deploy --only hosting
git add .
git commit -m "Update Prosperly site"
git push
```

(If this folder isn't a git repo yet, run `git init`, `git remote add origin <your-repo-url>` once beforehand — same as however Lumora's repo was set up.)

## Connecting prosperlyventures.com

1. In the Firebase console for the Prosperly project → **Hosting** → **Add custom domain**
2. Enter `prosperlyventures.com`
3. Firebase gives you TXT and A records to verify ownership and point the domain
4. Add those records at your domain registrar (wherever you bought prosperlyventures.com)
5. Firebase auto-provisions an SSL certificate once DNS verifies (can take a few hours)

## Notes

- This deploys the current landing page only. The interactive dashboard (`ProsperlyDashboard.jsx`) is a separate React component — happy to fold that into this same Firebase project (e.g. under `/app`) with a small Vite build step whenever you want it live too.

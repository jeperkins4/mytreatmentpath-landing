# Deploy to Vercel (Clean Landing Page Repo)

This repo contains ONLY the landing page - no backend, no SQLite, no build issues.

## Deploy to Vercel (2 minutes)

### Option A: Vercel Dashboard (Recommended)

1. **Go to:** https://vercel.com/new
2. **Click "Import"** next to `jeperkins4/mytreatmentpath-landing`
3. **Click "Deploy"** (no config needed - it's just HTML/CSS/JS)
4. **Done!** ✓ https://mytreatmentpath-landing.vercel.app

**No Root Directory needed.** This repo is landing page only.

---

### Option B: Vercel CLI

```bash
cd ~/.openclaw/workspace/mytreatmentpath-landing

# Login
vercel login

# Deploy
vercel --prod
```

---

## Why This Works

**Old repo (medical-research-tracker):**
- Root has package.json with SQLite dependencies
- Vercel tries to build SQLite → FAILS ❌

**New repo (mytreatmentpath-landing):**
- Only HTML/CSS/JS files
- package.json has ZERO dependencies
- No build step needed
- Vercel just serves static files → SUCCESS ✅

---

## Update DNS

Once deployed, add custom domain:

1. **Vercel Dashboard** → Your Project → **Settings** → **Domains**
2. **Add:** `mytreatmentpath.com`
3. **Follow DNS instructions** (add A record or change nameservers)

---

## Keep Landing Page Updated

When you update the landing page in the main repo:

```bash
# Sync changes from main repo
cd ~/.openclaw/workspace/mytreatmentpath-landing
cp ../medical-research-tracker/landing-page/index.html .

# Commit and push
git add .
git commit -m "Update landing page"
git push origin main

# Vercel auto-deploys!
```

---

**Ready to deploy!** Just visit https://vercel.com/new and import this repo.

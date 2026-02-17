# MyTreatmentPath - Marketing Website

**Public-facing landing page** for MyTreatmentPath desktop application.

> **💻 Desktop App Code:** See [medical-research-tracker](https://github.com/jeperkins4/medical-research-tracker) repo  
> **📥 Download App:** See [Releases](https://github.com/jeperkins4/medical-research-tracker/releases)

This repo contains ONLY the static marketing website (HTML/CSS/JS). The actual Electron desktop application lives in the main repo.

## Quick Deploy to Netlify (5 minutes)

### Option 1: Drag & Drop (Easiest)
1. Go to https://app.netlify.com/drop
2. Drag the `landing-page/` folder onto the page
3. Done! Site is live at `https://random-name.netlify.app`

### Option 2: CLI (For custom domain)
```bash
cd landing-page

# Install Netlify CLI
npm install -g netlify-cli

# Login
netlify login

# Deploy
netlify init
# Follow prompts:
# - Create new site
# - Site name: mytreatmentpath
# - Publish directory: . (current directory)

netlify deploy --prod

# Site live at: https://mytreatmentpath.netlify.app
```

## Custom Domain Setup

1. Buy domain (e.g., mytreatmentpath.com)
2. Netlify dashboard → Domain settings → Add custom domain
3. Update DNS records:
   ```
   A     @     → 75.2.60.5 (Netlify IP)
   CNAME www   → mytreatmentpath.netlify.app
   ```
4. SSL auto-configures in ~5 minutes

## Update Download Links

Before deploying, update GitHub username in `index.html`:

**Find & replace:**
```html
<!-- Old -->
https://github.com/yourusername/medical-research-tracker

<!-- New -->
https://github.com/jeperkins4/medical-research-tracker
```

Or use specific release URLs:
```html
<!-- Download button URLs -->
href="https://github.com/jeperkins4/medical-research-tracker/releases/download/v0.1.0/MyTreatmentPath-0.1.0-arm64.dmg"
href="https://github.com/jeperkins4/medical-research-tracker/releases/download/v0.1.0/MyTreatmentPath-0.1.0.dmg"
```

## File Structure

```
landing-page/
├── index.html        # Main landing page
├── README.md         # This file
├── privacy.html      # Privacy policy (create)
├── terms.html        # Terms of service (create)
└── disclaimer.html   # Medical disclaimer (create)
```

## Features

- ✅ Hero section with download buttons
- ✅ Feature showcase (6 cards)
- ✅ Privacy-first messaging
- ✅ FAQ section
- ✅ Responsive design (mobile-friendly)
- ✅ Smooth scrolling
- ✅ Download tracking (analytics-ready)
- ✅ Professional styling

## Add Analytics (Optional)

### Google Analytics
```html
<!-- Add before </head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Plausible (Privacy-Friendly)
```html
<!-- Add before </head> -->
<script defer data-domain="mytreatmentpath.com" src="https://plausible.io/js/script.js"></script>
```

## Track Downloads

Update the download tracking script (already in index.html):
```javascript
document.querySelectorAll('.download-button').forEach(button => {
  button.addEventListener('click', function() {
    const platform = this.textContent.includes('Apple Silicon') ? 'mac-arm64' : 'mac-intel';
    
    // Google Analytics
    if (window.gtag) {
      gtag('event', 'download', { platform });
    }
    
    // Plausible
    if (window.plausible) {
      plausible('Download', { props: { platform } });
    }
  });
});
```

## SEO Optimization

Already included:
- ✅ Meta description
- ✅ Open Graph tags (social sharing)
- ✅ Semantic HTML
- ✅ Responsive viewport

To improve:
- [ ] Add favicon (`favicon.ico` in root)
- [ ] Add Open Graph image (`og-image.png` 1200x630px)
- [ ] Add sitemap.xml
- [ ] Add robots.txt

## Legal Pages (TODO)

Create these pages before public launch:

### privacy.html
```html
<h1>Privacy Policy</h1>
<p>Your data stays on your device...</p>
<!-- Full privacy policy -->
```

### terms.html
```html
<h1>Terms of Service</h1>
<p>By using MyTreatmentPath...</p>
<!-- Full terms -->
```

### disclaimer.html
```html
<h1>Medical Disclaimer</h1>
<p>MyTreatmentPath is not medical advice...</p>
<!-- Full disclaimer -->
```

Link to these from footer.

## Deployment Checklist

Before going live:
- [ ] Update download URLs with real GitHub release links
- [ ] Test download links
- [ ] Add favicon
- [ ] Add Open Graph image
- [ ] Create privacy policy page
- [ ] Create terms of service page
- [ ] Create medical disclaimer page
- [ ] Test on mobile devices
- [ ] Test on different browsers
- [ ] Setup analytics (optional)
- [ ] Custom domain (optional)

## After Deploy

1. Test live site on multiple devices
2. Share link with friends for feedback
3. Submit to Product Hunt (optional)
4. Share on Twitter/LinkedIn
5. Monitor analytics

## Support

- Issues: https://github.com/jeperkins4/medical-research-tracker/issues
- Email: support@mytreatmentpath.com

---

**Ready to deploy? Drag `landing-page/` to https://app.netlify.com/drop now!**

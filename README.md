# Wesley J. Morris LLC — Website

Static site for [wesleyjmorris.com](https://wesleyjmorris.com).
Five pages · Netlify hosting · Custom domain · Netlify Forms contact.

---

## Pages

| File | URL | Description |
|------|-----|-------------|
| `index.html` | `/` | Home — hero, about, services, UHURU teaser, stats, contact form |
| `work.html` | `/work` | Full work history, services, engagements, education, awards |
| `framework.html` | `/framework` | Three frameworks: UHURU, The Luminous Dark™, The Friendship Doctrine™ |
| `blog.html` | `/blog` | 7 Medium essays with real links + 8 media/podcast appearances |

---

## Quick Start (Local Preview)

```bash
# No build step needed — pure HTML/CSS/JS
# Option 1: Python (built-in)
python3 -m http.server 8000
# Then open: http://localhost:8000

# Option 2: Node (if installed)
npx serve .
```

---

## GitHub Setup

```bash
# 1. Initialize and push
git init
git add .
git commit -m "Initial site build"

# 2. Create repo on GitHub, then:
git remote add origin https://github.com/YOUR_USERNAME/wjm-site.git
git branch -M main
git push -u origin main
```

---

## Netlify Deployment

### First Deploy
1. Go to [app.netlify.com](https://app.netlify.com) → **Add new site** → **Import from Git**
2. Connect your GitHub account and select `wjm-site`
3. Build settings:
   - **Build command:** *(leave blank)*
   - **Publish directory:** `.`
4. Click **Deploy site**

### Connect Custom Domain (`wesleyjmorris.com`)
1. In Netlify: **Site settings → Domain management → Add custom domain**
2. Enter `wesleyjmorris.com` → **Verify**
3. At your DNS registrar, update nameservers to Netlify's:
   ```
   dns1.p06.nsone.net
   dns2.p06.nsone.net
   dns3.p06.nsone.net
   dns4.p06.nsone.net
   ```
   *(Or add a CNAME record pointing to your Netlify subdomain)*
4. Netlify auto-provisions an SSL certificate via Let's Encrypt (takes ~1 min after DNS propagates)

### Enable Netlify Forms + Email to brotherwes44@gmail.com
The contact form on `index.html` is already wired with `data-netlify="true"`.
After deploying, Netlify detects it automatically. To receive each submission by email:

1. Netlify Dashboard → **Forms** → `contact`
2. Click **Form notifications** → **Add notification**
3. Select **Email notification**
4. Enter `brotherwes44@gmail.com` as the recipient
5. Click **Save**

Every new contact form submission will now arrive in your inbox.

---

## Adding Photos

1. Save your image files to the `photos/` folder
2. Follow the naming guide in `photos/.gitkeep`
3. **Key file:** `photos/wjm-headshot.jpg` — used in the hero and about section on every page. **Add this first.**
4. In `gallery.html`, replace the placeholder `<div class="gallery-placeholder">` blocks with `<img>` tags:
   ```html
   <!-- Before (placeholder) -->
   <div class="gallery-masonry-item" data-category="kilimanjaro" ...>
     <div class="gallery-placeholder">...</div>
     ...
   </div>

   <!-- After (real photo) -->
   <div class="gallery-masonry-item" data-category="kilimanjaro" ...>
     <img src="photos/kili-summit-2017.jpg" alt="Uhuru Peak summit, 2017" loading="lazy" />
     ...
   </div>
   ```

---

## File Structure

```
wjm-site/
├── index.html          ← Home
├── work.html           ← Work & Experience
├── framework.html      ← UHURU Framework™
├── blog.html           ← Writing & Media
├── gallery.html        ← Photo Gallery
├── netlify.toml        ← Netlify config (headers, redirects, domain)
├── _redirects          ← Netlify redirect rules
├── assets/
│   └── styles.css      ← Shared stylesheet (all pages)
├── photos/
│   ├── .gitkeep        ← Naming guide for photos
│   └── wjm-headshot.jpg ← ADD THIS: headshot referenced throughout
└── README.md
```

---

## Design System

| Token | Value | Use |
|-------|-------|-----|
| `--parchment` | `#f0e8d8` | Main background |
| `--earth` | `#3d2b1f` | Dark sections, text |
| `--copper` | `#8b4513` | Accent, links |
| `--gold` | `#c9972b` | Highlights, UHURU |
| `--ink` | `#1a1008` | Footer, deep dark |

**Fonts:** Cormorant Garamond (display) · Cinzel (labels/nav) · Crimson Pro (body)
All loaded via Google Fonts.

---

## Ongoing Refinement

The site is built to grow. Planned next steps:
- [ ] Add `photos/wjm-headshot.jpg` and real gallery images
- [ ] Populate real Medium post URLs in `blog.html`
- [ ] Add `assets/resume.pdf` and link from `work.html`
- [ ] Set up Netlify form email notifications
- [ ] Add Google Analytics or Plausible (privacy-friendly)
- [ ] Consider adding a `404.html` custom error page
- [ ] Add Open Graph / social sharing meta tags

---

*© 2026 Wesley J. Morris LLC. All rights reserved.*

# Deploying IntakeHQ to intakehq.org

Quick guide to get your car audio website live on intakehq.org

## 🚀 Fastest Method: Netlify (Recommended)

### Step 1: Create Netlify Account (2 minutes)

1. Go to https://netlify.com
2. Click "Sign up"
3. Use GitHub, GitLab, or email
4. **FREE FOREVER** for static sites

### Step 2: Deploy Your Site (5 minutes)

**Option A: Drag & Drop (Easiest)**

1. Log into Netlify
2. Click "Add new site" → "Deploy manually"
3. Drag the entire `intakehq-audio` folder onto the upload area
4. Wait 30 seconds
5. **SITE IS LIVE!** (on random Netlify URL)

**Option B: GitHub (Better for updates)**

1. Create GitHub account (if you don't have one)
2. Create new repository: `intakehq-audio`
3. Push your files:
   ```bash
   cd C:\Users\tytewyte\CascadeProjects\intakehq-audio
   git init
   git add .
   git commit -m "Initial car audio website"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/intakehq-audio.git
   git push -u origin main
   ```
4. In Netlify: "Add new site" → "Import from Git"
5. Connect GitHub and select your repo
6. Click "Deploy"

### Step 3: Connect intakehq.org Domain (10 minutes)

**In Netlify:**

1. Go to your site dashboard
2. Click "Domain settings"
3. Click "Add custom domain"
4. Enter: `intakehq.org`
5. Click "Verify"
6. Netlify will show you DNS records to add

**In Namecheap:**

1. Log into Namecheap
2. Go to Domain List
3. Click "Manage" next to intakehq.org
4. Go to "Advanced DNS" tab
5. Delete any existing A Records and CNAME Records
6. Add these new records:

   **A Record:**
   ```
   Type: A Record
   Host: @
   Value: 75.2.60.5
   TTL: Automatic
   ```

   **CNAME Record:**
   ```
   Type: CNAME Record
   Host: www
   Value: [your-site-name].netlify.app
   TTL: Automatic
   ```

7. Click "Save all changes"

**Wait for DNS Propagation:**
- Usually takes 5-30 minutes
- Can take up to 24 hours
- Check status: https://dnschecker.org

### Step 4: Enable HTTPS (Automatic)

1. In Netlify: Domain settings
2. Scroll to "HTTPS"
3. Click "Verify DNS configuration"
4. Click "Provision certificate"
5. Wait 1-2 minutes
6. **HTTPS ENABLED!**

---

## ✅ Verification Checklist

After deployment, test these:

- [ ] Site loads at https://intakehq.org
- [ ] Site loads at https://www.intakehq.org
- [ ] Navigation links work (smooth scroll)
- [ ] All sections visible
- [ ] Contact form works
- [ ] Mobile responsive (test on phone)
- [ ] HTTPS padlock shows in browser

---

## 🔧 Making Updates

### If Using Drag & Drop:

1. Edit `index.html` locally
2. Go to Netlify dashboard
3. Click "Deploys" tab
4. Drag updated folder to "Drop to update" area
5. **LIVE IN 30 SECONDS!**

### If Using GitHub:

1. Edit `index.html` locally
2. Commit and push:
   ```bash
   git add .
   git commit -m "Update pricing"
   git push
   ```
3. Netlify auto-deploys in 1-2 minutes
4. **AUTOMATIC!**

---

## 📝 Before Going Live - Customize These:

### Required Changes:

1. **Contact Information** (line 442-449 in index.html):
   ```html
   <p>[Your Address]</p>          ← Add real address
   <p>[City, State ZIP]</p>       ← Add city/state
   <p>[Your Phone Number]</p>     ← Add phone
   ```

2. **Raffle Date** (line 413):
   ```html
   <p>Next Drawing: [DATE]</p>    ← Set actual date
   ```

3. **Contact Form** (line 457):
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID"
   ```
   
   **Get Form ID:**
   - Go to https://formspree.io
   - Sign up (free)
   - Create new form
   - Copy form ID
   - Replace `YOUR_FORM_ID`

### Optional Changes:

4. **Business Hours** (line 449-451):
   - Update to your actual hours

5. **Pricing** (lines 350-400):
   - Adjust if needed

6. **Brand Names** (lines 320-340):
   - Add/remove brands

---

## 🎨 Adding Your Logo

### Create Logo:

1. Make logo image (PNG with transparent background)
2. Size: 200x50 pixels recommended
3. Save as `logo.png` in same folder as `index.html`

### Update Code:

Replace line 33 in `index.html`:

**Current:**
```html
<div class="logo">INTAKEHQ</div>
```

**New:**
```html
<div class="logo">
    <img src="logo.png" alt="IntakeHQ" style="height: 50px;">
</div>
```

---

## 📸 Adding Photos

### Create Images Folder:

1. Create folder: `intakehq-audio/images/`
2. Add your photos:
   - `install1.jpg`
   - `install2.jpg`
   - `install3.jpg`
   - etc.

### Add Gallery Section:

Add after the Services section (around line 400):

```html
<!-- Gallery Section -->
<section id="gallery" class="gallery">
    <h2>Our <span>Work</span></h2>
    <div class="gallery-grid">
        <img src="images/install1.jpg" alt="Custom subwoofer box install">
        <img src="images/install2.jpg" alt="Amplifier installation">
        <img src="images/install3.jpg" alt="Component speaker upgrade">
        <img src="images/install4.jpg" alt="Full system install">
    </div>
</section>
```

Add CSS (in `<style>` section):

```css
.gallery {
    background: #0a0a0a;
}

.gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1rem;
    margin-top: 3rem;
}

.gallery-grid img {
    width: 100%;
    height: 300px;
    object-fit: cover;
    border-radius: 10px;
    border: 2px solid #ff0000;
    transition: transform 0.3s;
}

.gallery-grid img:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 30px rgba(255, 0, 0, 0.5);
}
```

Update navigation (add Gallery link):

```html
<li><a href="#gallery">Gallery</a></li>
```

---

## 🎟️ Raffle System Setup

### Current Setup:
- Manual entry via contact form
- You track entries manually
- Monthly drawing

### Upgrade to Automated:

**Option 1: Netlify Forms (Free)**

1. Change form action:
   ```html
   <form name="raffle" method="POST" data-netlify="true">
   ```

2. Netlify will email you entries
3. You can export to spreadsheet

**Option 2: Stripe Integration ($)**

For actual payment processing:
1. Create Stripe account
2. Add Stripe Checkout button
3. Collect payments automatically

---

## 📱 Social Media Integration

### Add Social Links to Footer:

Before `</footer>` tag:

```html
<div style="margin: 2rem 0;">
    <a href="https://instagram.com/YOUR_HANDLE" 
       style="color: #ff0000; margin: 0 1rem; text-decoration: none; font-size: 1.5rem;">
        📷 Instagram
    </a>
    <a href="https://facebook.com/YOUR_PAGE" 
       style="color: #ff0000; margin: 0 1rem; text-decoration: none; font-size: 1.5rem;">
        📘 Facebook
    </a>
    <a href="https://tiktok.com/@YOUR_HANDLE" 
       style="color: #ff0000; margin: 0 1rem; text-decoration: none; font-size: 1.5rem;">
        🎵 TikTok
    </a>
</div>
```

---

## 🔍 SEO Optimization

### Already Included:
- Meta description
- Semantic HTML
- Fast loading
- Mobile responsive

### Add Later:
- Google Analytics
- Google Business Profile
- Local SEO optimization
- Sitemap

---

## 💡 Pro Tips

### Performance:
- Keep images under 500KB each
- Use JPG for photos, PNG for logos
- Compress images before uploading

### Mobile:
- Test on real phone
- Check all buttons work
- Verify forms work on mobile

### Marketing:
- Post on social media when live
- Tell local car clubs
- Partner with detail shops
- Run raffle promotion

---

## 🆘 Troubleshooting

### Site Not Loading:

**Check:**
1. DNS records correct in Namecheap?
2. Waited 30+ minutes for DNS?
3. Tried clearing browser cache?
4. Tried different browser?

**Test:**
- Visit Netlify URL directly (works = DNS issue)
- Check https://dnschecker.org

### Form Not Working:

**Check:**
1. Formspree ID correct?
2. Email verified in Formspree?
3. Form action URL correct?

**Fix:**
- Use Netlify Forms instead (easier)

### Mobile Issues:

**Check:**
1. Viewport meta tag present? (it is)
2. Text readable on small screen?
3. Buttons big enough to tap?

---

## 📞 Need Help?

Contact Wendell or check:
- Netlify Docs: https://docs.netlify.com
- Formspree Docs: https://help.formspree.io

---

## 🎯 Launch Checklist

Before announcing:

- [ ] All contact info updated
- [ ] Raffle date set
- [ ] Contact form tested
- [ ] Pricing confirmed
- [ ] Photos added (if ready)
- [ ] Mobile tested
- [ ] HTTPS working
- [ ] Social links added
- [ ] Business hours correct
- [ ] All links work

**THEN:**
- [ ] Post on social media
- [ ] Tell friends/family
- [ ] Print flyers
- [ ] Tell car clubs
- [ ] Launch raffle
- [ ] **GO LIVE!**

---

Built with ⚔️ by Kevin (Top Wizard)
Ready to bring in customers! 🔊

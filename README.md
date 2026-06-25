# IntakeHQ - Car Audio Installation Website

Professional car audio installation website featuring modern design, premium brands, and raffle system.

## 🔊 Features

- **Modern Design**: Bold, dark theme optimized for today's generation
- **Premium Brands**: Sundown Audio, Kicker, Memphis Audio, Skar Audio, JL Audio
- **Service Packages**: 4 pricing tiers from $449 to $1499+
- **Monthly Raffle**: Lead generation system with ticket sales
- **Mobile Responsive**: Optimized for all devices
- **Contact Forms**: Quote requests and general inquiries

## 🚀 Quick Start

### View Locally

1. Open `index.html` in your browser
2. That's it! No build process needed.

### Deploy to intakehq.org

#### Option 1: Netlify (Recommended - Free)

1. **Create Netlify Account**
   - Go to https://netlify.com
   - Sign up (free)

2. **Deploy Site**
   - Drag and drop the `intakehq-audio` folder onto Netlify
   - OR connect to GitHub (if you push to repo)

3. **Connect Custom Domain**
   - In Netlify: Site Settings → Domain Management
   - Click "Add custom domain"
   - Enter: `intakehq.org`
   - Follow DNS instructions

4. **Update Namecheap DNS**
   - Go to Namecheap dashboard
   - Manage intakehq.org
   - Add these records:
     ```
     Type: A Record
     Host: @
     Value: 75.2.60.5
     
     Type: CNAME
     Host: www
     Value: [your-site].netlify.app
     ```

#### Option 2: GitHub Pages

1. Create GitHub repo
2. Push files to repo
3. Enable GitHub Pages in repo settings
4. Point intakehq.org to GitHub Pages

## ✏️ Customization

### Update Business Info

Edit `index.html` and replace these placeholders:

**Contact Information:**
- Line 442: `[Your Address]`
- Line 443: `[City, State ZIP]`
- Line 446: `[Your Phone Number]`

**Raffle Date:**
- Line 413: `[DATE]` - Set next drawing date

**Contact Form:**
- Line 457: Replace `YOUR_FORM_ID` with your Formspree ID
  - Get free form at https://formspree.io
  - Or use Netlify Forms (built-in)

### Update Pricing

Edit the service cards (lines 350-400):
- Change prices
- Modify package details
- Add/remove features

### Change Colors

Current theme: Black/Red
To change:
- Find `#ff0000` (red) - replace with your color
- Find `#000` (black) - replace with your background color

### Add Your Logo

Replace line 33 text logo with image:
```html
<div class="logo">
    <img src="logo.png" alt="IntakeHQ" style="height: 50px;">
</div>
```

## 📱 Social Media Integration

### Add Instagram Feed

Add before closing `</body>` tag:
```html
<!-- Instagram Feed Widget -->
<script src="https://cdn.lightwidget.com/widgets/lightwidget.js"></script>
<iframe src="//lightwidget.com/widgets/YOUR_WIDGET_ID.html" 
        scrolling="no" allowtransparency="true" 
        class="lightwidget-widget" 
        style="width:100%;border:0;overflow:hidden;">
</iframe>
```

### Add Social Links

Add to navigation or footer:
```html
<div class="social-links">
    <a href="https://instagram.com/YOUR_HANDLE">📷 Instagram</a>
    <a href="https://facebook.com/YOUR_PAGE">📘 Facebook</a>
    <a href="https://tiktok.com/@YOUR_HANDLE">🎵 TikTok</a>
</div>
```

## 🎟️ Raffle System

### Current Setup
- Manual ticket sales (contact form)
- Monthly drawings

### Upgrade Options

**Option 1: Stripe Payment**
Add Stripe for online payments:
```html
<script src="https://js.stripe.com/v3/"></script>
<!-- Add Stripe checkout button -->
```

**Option 2: PayPal**
Add PayPal button for ticket purchases

**Option 3: Netlify Forms**
Use built-in form handling (free):
- Change form action to `netlify`
- Add `data-netlify="true"` attribute

## 📸 Adding Gallery

Create new section after services:
```html
<section id="gallery" class="gallery">
    <h2>Our <span>Work</span></h2>
    <div class="gallery-grid">
        <img src="images/install1.jpg" alt="Install 1">
        <img src="images/install2.jpg" alt="Install 2">
        <!-- Add more images -->
    </div>
</section>
```

Add CSS:
```css
.gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1rem;
}

.gallery-grid img {
    width: 100%;
    border-radius: 10px;
    transition: transform 0.3s;
}

.gallery-grid img:hover {
    transform: scale(1.05);
}
```

## 🎨 Design Notes

### Modern Features for Today's Generation

**What Makes It Modern:**
- Dark theme (preferred by younger audience)
- Bold typography
- Smooth animations
- Mobile-first design
- Fast loading (no heavy frameworks)
- Social proof ready

**Color Psychology:**
- Red: Energy, power, excitement
- Black: Premium, sophisticated, bold
- White: Clean, professional

### Mobile Optimization

Site is fully responsive:
- Touch-friendly buttons
- Readable text on small screens
- Fast loading on mobile data
- Easy navigation

## 📊 Analytics (Optional)

### Add Google Analytics

Before closing `</head>` tag:
```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## 🔧 Technical Details

- **No Build Process**: Pure HTML/CSS/JS
- **No Dependencies**: Works offline
- **Fast Loading**: < 50KB total
- **SEO Optimized**: Meta tags included
- **Accessibility**: Semantic HTML

## 📝 Content Tips

### Writing for Today's Audience

**Do:**
- Keep it short and punchy
- Use emojis (but not too many)
- Show, don't tell (use photos/videos)
- Be authentic
- Highlight results

**Don't:**
- Write long paragraphs
- Use technical jargon
- Be boring
- Oversell

### Photo Tips

**What to Photograph:**
- Before/after comparisons
- Custom boxes (show craftsmanship)
- Clean wire installations
- Happy customers with their cars
- Action shots (bass demos)

**Photo Quality:**
- Good lighting
- Clean backgrounds
- High resolution
- Multiple angles

## 🚀 Marketing Ideas

### Social Media Strategy

**Instagram:**
- Post install photos
- Bass demo videos
- Behind-the-scenes
- Customer testimonials

**TikTok:**
- Quick install time-lapses
- Bass test reactions
- Tips and tricks
- Trending audio with your work

**Facebook:**
- Local community engagement
- Event announcements
- Customer reviews
- Raffle promotions

### Local SEO

1. Create Google Business Profile
2. Get customer reviews
3. Post regularly
4. Add photos
5. Respond to questions

### Raffle Promotion

**Where to Promote:**
- Social media posts
- In-shop signage
- Partner locations
- Car clubs/meets
- Local Facebook groups

**How to Promote:**
- Create urgency (countdown)
- Show prize value
- Feature past winners
- Make it easy to enter

## 💰 Pricing Strategy

Current packages are based on 2026 market research:

- **Starter Bass ($449)**: Competitive entry point
- **Serious Bass ($849)**: Most popular tier
- **Competition Level ($1499+)**: Premium/custom
- **Highs Upgrade ($699)**: Alternative to bass

**Profit Margins:**
- Parts cost: ~40-50% of price
- Labor: ~30-40% of price
- Overhead: ~10-20%
- Profit: ~20-30%

## 🎯 Next Steps

1. **Customize Content**
   - Add your contact info
   - Set raffle date
   - Update any text

2. **Add Photos**
   - Create `images` folder
   - Add install photos
   - Update gallery section

3. **Deploy**
   - Choose hosting (Netlify recommended)
   - Connect domain
   - Test everything

4. **Market**
   - Create social accounts
   - Post first content
   - Launch raffle
   - Tell everyone!

## 📞 Support

Need help customizing? Contact Wendell!

Built with ⚔️ by Kevin (Top Wizard)

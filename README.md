# Bywater Sauna - Seattle Beach Sauna Experience

A beautiful, fully-featured website for Bywater Sauna with content management, multiple design themes, and SEO optimization.

🌐 **Live Site**: [bywatersauna.com](https://bywatersauna.com)
📝 **CMS Admin**: [bywatersauna.com/admin](https://bywatersauna.com/admin)

## ✨ Features

### Design & UX
- 🎨 **4 Color Themes**: 2 dark (Midnight Forest, Coastal Night), 2 light (Cedar & Stone, Sage Garden)
- 🎭 **4 Icon Sets**: Emoji, Lucide, Natural, Winter (open source Lucide icons)
- 📐 **Layout Options**: Contained or Full-Width sections
- 🃏 **Card Styles**: Default, Minimal, Bold
- 🔘 **Button Styles**: Default, Rounded, Square
- 📝 **Text Sizes**: Small, Default, Large
- 💾 **Persistent Preferences**: All design choices saved to localStorage

### Interactive Features
- 🗺️ **Interactive Map**: Leaflet.js map with 4 Seattle location markers
- 📍 **Sticky Map Scroll**: Map follows you down the page until pricing section
- 🎯 **Location Hover**: Markers highlight when hovering over location cards
- 🎬 **Smooth Animations**: Intersection Observer scroll-triggered animations
- 📱 **Fully Responsive**: Mobile-first design, works on all devices

### Content Management
- 🖥️ **Decap CMS**: Edit content via web interface (no Netlify required)
- 📂 **JSON Data**: All content in `_data/*.json` files
- 🔗 **GitHub Backend**: Direct integration with GitHub repository
- 🆓 **Free & Open Source**: MIT licensed CMS

### SEO & Performance
- 🔍 **SEO Optimized**: Meta tags, Open Graph, Twitter Cards
- 🤖 **robots.txt**: Search engine crawling configuration
- 🗺️ **sitemap.xml**: Complete site structure for search engines
- 📊 **Structured Data**: JSON-LD for local business (Schema.org)
- 🖼️ **Social Previews**: Custom og:image for sharing on social media
- 🎯 **Favicon**: Custom SVG favicon

## 🚀 Quick Start

### Deploy to GitHub Pages

1. **Push to GitHub**:
   ```bash
   git push origin main
   ```

2. **Enable GitHub Pages**:
   - Go to repository Settings → Pages
   - Set Source to `main` branch
   - Save and wait for deployment

3. **Set up Custom Domain** (optional):
   - Add `CNAME` file with your domain
   - Configure DNS with GitHub Pages IPs

### Set up Content Management

See [DECAP_CMS_SETUP.md](DECAP_CMS_SETUP.md) for detailed CMS setup instructions.

**Quick version**:
1. Create GitHub OAuth App
2. Configure `admin/config.yml`
3. Access CMS at `/admin/`
4. Login and edit content!

## 📁 File Structure

```
bywatersauna/
├── index.html              # Main homepage
├── about.html              # About page (Nate & Simeon)
├── book.html               # Booking information
├── membership.html         # Membership tiers
├── events.html             # Private events
├── contact.html            # Contact form
├── privacy.html            # Privacy policy
├── admin/
│   ├── index.html          # Decap CMS admin interface
│   └── config.yml          # CMS configuration
├── _data/
│   ├── locations.json      # 4 Seattle location data
│   └── about.json          # About page content
├── images/
│   └── uploads/            # CMS uploaded images
├── favicon.svg             # Site favicon
├── social-preview.svg      # Social media preview image
├── robots.txt              # Search engine instructions
└── sitemap.xml             # Site structure for SEO
```

## 🎨 Design System

### Color Themes

| Theme | Type | Primary | Accent | Best For |
|-------|------|---------|--------|----------|
| Midnight Forest | Dark | #1C1C1C | #ca5e43 (Orange) | Default, professional |
| Coastal Night | Dark | #0f1419 | #5eb3d6 (Blue) | Ocean-inspired |
| Cedar & Stone | Light | #F5F1E8 | #A6634F (Red) | Warm, earthy |
| Sage Garden | Light | #FAFAF8 | #4A6156 (Green) | Fresh, natural |

### Icon Sets

All icons from **[Lucide Icons](https://lucide.dev)** (MIT License):

- **Emoji**: 🔥 💧 🔄 (Default)
- **Lucide**: Flame, Droplets, Repeat
- **Natural**: Sun, Waves, Refresh-cw
- **Winter**: Flame, Snowflake, Rotate-cw

## 📝 Editing Content

### Via CMS (Recommended)
1. Go to `https://bywatersauna.com/admin/`
2. Login with GitHub
3. Edit locations, about page, etc.
4. Changes commit directly to GitHub

### Via GitHub
1. Edit files in `_data/` folder
2. Commit and push changes
3. Site updates automatically

## 🧪 Local Development

```bash
# Serve locally
python -m http.server 8000
# or
npx serve

# Run Decap CMS locally
npx decap-server
```

Open `http://localhost:8000/`

## 🔧 Customization

### Change Colors
Edit CSS variables in `index.html` or use the theme switcher in Design Options panel (⚙️ button bottom-right).

### Add Locations
Edit `_data/locations.json` or use the CMS at `/admin/`.

### Modify Pages
Edit HTML files directly or configure CMS in `admin/config.yml`.

## 📦 Dependencies

- [Leaflet.js](https://leafletjs.com/) - Interactive maps
- [Decap CMS](https://decapcms.org/) - Content management
- [Lucide Icons](https://lucide.dev/) - Open source icons
- [Google Fonts](https://fonts.google.com/) - Playfair Display + Inter

All dependencies loaded via CDN (no build step required).

## 🤝 Contributing

This is a private business website, but feel free to fork and adapt for your own projects!

## 📄 License

Website code: MIT License
Content & branding: ©2026 Bywater LLC. All rights reserved.

## 🐛 Issues & Support

- [GitHub Issues](https://github.com/nicolaspratt/bywatersauna/issues)
- [Decap CMS Docs](https://decapcms.org/docs/)
- [Leaflet Docs](https://leafletjs.com/reference.html)

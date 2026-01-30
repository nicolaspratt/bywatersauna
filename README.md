# Bywater Sauna Website with CMS

A beautiful, responsive website for Bywater Sauna with an easy-to-use CMS backend.

## Features

- ✅ Fully responsive design (desktop, tablet, mobile)
- ✅ Interactive map showing all 4 Seattle locations
- ✅ Smooth animations and transitions
- ✅ Easy content management through Decap CMS
- ✅ Hosted for free on GitHub Pages
- ✅ No database required

## Setup Instructions

### 1. Push to GitHub

```bash
git add .
git commit -m "Add CMS and initial content"
git push origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Source", select **main** branch
4. Click **Save**
5. Your site will be live at: `https://[username].github.io/bywatersauna/`

### 3. Set Up Netlify Identity (for CMS authentication)

Since GitHub Pages doesn't support server-side authentication, we'll use Netlify as a proxy:

1. Go to [Netlify](https://netlify.com) and sign up
2. Click "Add new site" → "Import an existing project"
3. Connect your GitHub repository
4. Deploy settings:
   - Build command: (leave empty)
   - Publish directory: `/`
5. After deployment, go to **Site settings** → **Identity**
6. Click "Enable Identity"
7. Under "Registration preferences", select "Invite only"
8. Under "Services" → "Git Gateway", click "Enable Git Gateway"

### 4. Update CMS Config

1. In `admin/config.yml`, the backend is already configured for Git Gateway
2. Add this script to your `index.html` before `</body>`:
```html
<script>
  if (window.netlifyIdentity) {
    window.netlifyIdentity.on("init", user => {
      if (!user) {
        window.netlifyIdentity.on("login", () => {
          document.location.href = "/admin/";
        });
      }
    });
  }
</script>
```

### 5. Access the CMS

1. Go to `https://[your-site].netlify.app/admin/`
2. Click "Login with Netlify Identity"
3. You can now edit content!

### 6. Invite Team Members

1. In Netlify, go to **Identity** tab
2. Click "Invite users"
3. Enter email addresses
4. They'll receive an invite to access the CMS

## Content Structure

All content is stored in `_data/*.json` files:

- `settings.json` - Site title, contact info, social links
- `hero.json` - Hero section content
- `about.json` - About section paragraphs
- `services.json` - Service offerings and pricing
- `locations.json` - Location details with GPS coordinates
- `how_it_works.json` - Step-by-step instructions and guidelines

## Editing Content

### Via CMS (Recommended)
1. Go to `/admin/` on your site
2. Login with Netlify Identity
3. Edit content through the visual interface
4. Click "Publish" to save changes

### Via GitHub
1. Edit JSON files in `_data/` folder
2. Commit and push changes
3. Site rebuilds automatically

## Local Development

```bash
# Serve locally
python3 -m http.server 8000

# Or use any static server
npx serve
```

Then open: `http://localhost:8000/mockup/`

## File Structure

```
bywatersauna/
├── mockup/
│   └── index.html          # Main website
├── admin/
│   ├── index.html          # CMS admin interface
│   └── config.yml          # CMS configuration
├── _data/
│   ├── settings.json       # Site settings
│   ├── hero.json          # Hero section
│   ├── about.json         # About section
│   ├── services.json      # Services & pricing
│   ├── locations.json     # Location data
│   └── how_it_works.json  # Instructions
└── assets/
    └── images/            # Image uploads from CMS
```

## Customization

### Colors
Edit these CSS variables in `mockup/index.html`:
- Primary: `#2d5555` (teal)
- Accent: `#d4c4a8` (tan)
- Background: `#f8f9fa` (light gray)

### Sections
Add/remove sections by editing the CMS config in `admin/config.yml`

### Map
The interactive map automatically loads locations from `_data/locations.json`

## Support

For issues or questions, check:
- [Decap CMS Docs](https://decapcms.org/docs/)
- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Leaflet Map Docs](https://leafletjs.com/reference.html)

## License

MIT License - feel free to use for your own projects!

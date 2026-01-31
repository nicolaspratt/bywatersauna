# Decap CMS Setup Guide (Without Netlify)

Decap CMS is configured to work with GitHub backend without requiring Netlify hosting.

## Setup Steps

### 1. Enable GitHub Pages
1. Go to your repository settings: `https://github.com/nicolaspratt/bywatersauna/settings/pages`
2. Under "Source", select your branch (e.g., `main` or `claude/bywater-sauna-mockup-Dt9Ga`)
3. Save and wait for deployment
4. Your site will be available at: `https://nicolaspratt.github.io/bywatersauna/`

### 2. Create GitHub OAuth App
1. Go to GitHub Settings → Developer settings → OAuth Apps
   - Direct link: https://github.com/settings/developers
2. Click "New OAuth App"
3. Fill in:
   - **Application name**: `Bywater Sauna CMS`
   - **Homepage URL**: `https://nicolaspratt.github.io/bywatersauna`
   - **Authorization callback URL**: `https://api.netlify.com/auth/done`
   
   *Note: Even though we're not using Netlify hosting, Decap CMS uses Netlify's OAuth service for GitHub authentication*

4. Click "Register application"
5. Note your **Client ID** (you'll need this)
6. Generate a **Client Secret** and save it securely

### 3. Set up OAuth Service

Since Decap CMS requires an OAuth server, you have two options:

#### Option A: Use Netlify's OAuth Service (Recommended for simplicity)
Even though you're not hosting on Netlify, you can still use their free OAuth service:

1. Create free Netlify account (no hosting required)
2. Deploy a simple OAuth gateway using Netlify Functions
3. Update `admin/config.yml` with your site URL

#### Option B: Self-Hosted OAuth Gateway
Use a service like:
- **GitHub's git-gateway** - lightweight OAuth proxy
- **DecapCMS Auth Provider** - community solutions
- **Roll your own** using serverless functions on Vercel/CloudFlare

### 4. Update Decap CMS Config

Edit `admin/config.yml` and update:

```yaml
backend:
  name: github
  repo: nicolaspratt/bywatersauna
  branch: main  # or your target branch
  base_url: https://api.netlify.com  # if using Netlify OAuth
  auth_endpoint: auth
```

### 5. Access CMS

1. Navigate to: `https://nicolaspratt.github.io/bywatersauna/admin/`
2. Click "Login with GitHub"
3. Authorize the application
4. Start editing content!

## Local Development

To test locally:

1. Install Decap CMS proxy:
   ```bash
   npx decap-server
   ```

2. In `admin/config.yml`, ensure `local_backend: true` is set

3. Run a local server:
   ```bash
   python -m http.server 8000
   # or
   npx serve
   ```

4. Open `http://localhost:8000/admin/`

## Editing Content

Once logged in, you can edit:
- **Locations**: Update location details, parking info, amenities
- **About**: Modify about page content
- **Pages**: Edit hero sections and other page content

All changes are committed directly to your GitHub repository.

## Alternative: Use Git Directly

If you prefer not to set up OAuth:
- Edit JSON files in `_data/` folder directly
- Commit and push changes to GitHub
- GitHub Pages will automatically rebuild

## Troubleshooting

- **"Cannot read config.yml"**: Ensure the file exists at `/admin/config.yml`
- **OAuth errors**: Check your GitHub OAuth app callback URL
- **403 Forbidden**: Verify repository permissions and branch name

## Resources

- [Decap CMS Documentation](https://decapcms.org/docs/)
- [GitHub Backend Guide](https://decapcms.org/docs/github-backend/)
- [Authentication Setup](https://decapcms.org/docs/authentication-backends/)

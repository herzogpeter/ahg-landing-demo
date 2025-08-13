# Deployment Instructions

## Quick Deployment to Vercel (Recommended)

### Option 1: Command Line (2 minutes)

1. **Install and login to Vercel:**
   ```bash
   npx vercel login
   ```
   - Choose your preferred login method (GitHub recommended)
   - This will open a browser window for authentication

2. **Deploy the site:**
   ```bash
   npx vercel
   ```
   - Follow the prompts:
     - Setup and deploy? **Y**
     - Which scope? **Select your account**
     - Link to existing project? **N**
     - Project name? **ahg-demo** (or press enter for default)
     - Directory? **./** (press enter)
     - Build settings? **N**

3. **Get your production URL:**
   ```bash
   npx vercel --prod
   ```
   This will give you a permanent URL like: `https://ahg-demo.vercel.app`

### Option 2: Drag & Drop with Vercel (30 seconds)

1. Visit: https://vercel.com/new
2. Click "Import from Git" OR drag your project folder
3. Get instant preview URL

## Alternative: Netlify Drop (No Account Needed)

1. Visit: https://app.netlify.com/drop
2. Drag the entire `localWebsite` folder into the browser
3. Get instant HTTPS URL (like `amazing-newton-123456.netlify.app`)

## Sharing with Client

Your deployed site will have:
- ✅ HTTPS secure connection
- ✅ Professional URL
- ✅ Fast global CDN
- ✅ Mobile responsive
- ✅ No server maintenance needed

### URLs to Share:
- Main landing: `https://your-project.vercel.app/`
- Clone version: `https://your-project.vercel.app/ahg-clone.html`
- Accurate version: `https://your-project.vercel.app/ahg-accurate.html`

## Local Testing

To test locally before deployment:
```bash
python3 server.py
```
Then visit: http://localhost:8000/

## Files Included in Deployment

- `index.html` - Main landing page
- `ahg-clone.html` - American Hartford Gold clone design
- `ahg-accurate.html` - Accurate representation version
- `american-hartford-gold-logo.svg` - Official logo
- `vercel.json` - Deployment configuration
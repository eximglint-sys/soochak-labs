# Deployment Guide - Step by Step

## Step 1: Push to GitHub

### 1.1 Create a GitHub Repository
1. Go to [GitHub.com](https://github.com) and sign in
2. Click the "+" icon in the top right corner
3. Select "New repository"
4. Name your repository (e.g., `gemstones-pages`)
5. Choose **Public** or **Private**
6. **DO NOT** initialize with README, .gitignore, or license (we already have these)
7. Click "Create repository"

### 1.2 Push Your Code to GitHub
After creating the repository, GitHub will show you commands. Use these commands in your terminal:

```bash
# Add all files
git add .

# Commit the files
git commit -m "Initial commit"

# Add your GitHub repository as remote (replace YOUR_USERNAME and REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

**Note:** You'll need to authenticate. If prompted:
- Use a Personal Access Token (not your password)
- Create one at: GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
- Give it `repo` permissions

---

## Step 2: Deploy to Vercel

### 2.1 Sign Up / Sign In to Vercel
1. Go to [vercel.com](https://vercel.com)
2. Click "Sign Up" or "Log In"
3. Choose "Continue with GitHub" (recommended - easiest integration)

### 2.2 Import Your Project
1. After logging in, click "Add New..." → "Project"
2. You'll see your GitHub repositories listed
3. Find and click "Import" next to your `gemstones-pages` repository
4. Vercel will auto-detect it's a static site

### 2.3 Configure Deployment
1. **Project Name:** Keep default or change it
2. **Framework Preset:** Select "Other" or leave as auto-detected
3. **Root Directory:** Leave as `./` (root)
4. **Build Command:** Leave empty (static site, no build needed)
5. **Output Directory:** Leave empty (files are in root)
6. Click "Deploy"

### 2.4 Your Site is Live!
- Vercel will provide a URL like: `https://your-project-name.vercel.app`
- Every push to GitHub will automatically deploy
- You can add a custom domain later in Project Settings → Domains

---

## Step 3: Deploy to GoDaddy

### 3.1 Prepare Your Files
Your static files need to be uploaded to GoDaddy hosting. You have two options:

#### Option A: Using GoDaddy File Manager (Easiest)
1. Log in to your GoDaddy account
2. Go to "My Products" → Find your hosting plan
3. Click "Manage" → "cPanel" or "File Manager"
4. Navigate to `public_html` folder (or `www` or `htdocs` depending on your hosting)
5. Upload all your files:
   - `index.html`
   - `report.html`
   - `app.js`
   - `style.css`
   - `gemstone_reports.json`
   - `assets/` folder (with all images)

#### Option B: Using FTP (More Control)
1. Get your FTP credentials from GoDaddy:
   - Go to "My Products" → Hosting → "Manage" → "FTP"
   - Note your FTP host, username, and password
2. Use an FTP client (FileZilla, WinSCP, or VS Code FTP extension)
3. Connect to your FTP server
4. Navigate to `public_html` folder
5. Upload all your files

### 3.2 Configure Domain (If Needed)
1. In GoDaddy, go to "My Products" → Domains
2. Find your domain and click "DNS"
3. If using GoDaddy hosting, DNS should already be configured
4. If using Vercel with GoDaddy domain:
   - In Vercel: Project Settings → Domains → Add your domain
   - In GoDaddy DNS: Add CNAME record pointing to Vercel (instructions in Vercel)

### 3.3 Test Your Site
1. Visit your domain (e.g., `https://yourdomain.com`)
2. Test the search functionality
3. Verify all images load correctly

---

## Quick Reference Commands

### Git Commands (for future updates)
```bash
# After making changes
git add .
git commit -m "Description of changes"
git push origin main
```

### Vercel Auto-Deploy
- Every `git push` to GitHub automatically triggers Vercel deployment
- No manual steps needed after initial setup

### GoDaddy Updates
- Upload new/changed files via File Manager or FTP
- Replace existing files when updating

---

## Troubleshooting

### GitHub Issues
- **Authentication failed:** Use Personal Access Token instead of password
- **Repository not found:** Check repository name and username

### Vercel Issues
- **Build failed:** Check that all files are in the repository
- **404 errors:** Ensure `index.html` is in the root directory

### GoDaddy Issues
- **Files not showing:** Check you're uploading to `public_html` or `www` folder
- **Images not loading:** Verify `assets/` folder path is correct
- **404 errors:** Ensure `index.html` is in the root of your hosting folder


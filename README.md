# Hayer Home Healthcare — hayerhhc.com

Production-ready website with fully functional contact forms.

## Forms
Both forms send emails to **hayerhomehealthcare@gmail.com** via a 3-layer system:
1. **Netlify Forms** (server-side, works on Netlify hosting)
2. **FormSubmit.co** (direct email delivery, any hosting)
3. **mailto fallback** (opens email client if both above fail)

### Features
- Real-time field validation (required fields, email format)
- Auto-response email sent to the person who submitted the form
- Success/error UI feedback
- Spam protection (Netlify honeypot + FormSubmit captcha disabled for UX)

## Deployment: GitHub Pages

### 1. Push to GitHub
```bash
git init
git add -A
git commit -m "Production site with working forms"
git remote add origin https://github.com/farahabdullahi9/hayerhhc.com.git
git push -u origin main
```

### 2. Enable GitHub Pages
- Go to repo Settings → Pages
- Source: Deploy from branch → `main` → `/ (root)`
- Save

### 3. Connect Porkbun Domain
In Porkbun DNS, add these records:

| Type  | Host | Value                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| CNAME | www  | farahabdullahi9.github.io |

### 4. Set Custom Domain in GitHub
- Repo Settings → Pages → Custom domain: `hayerhhc.com`
- Check "Enforce HTTPS" (SSL auto-configured via Let's Encrypt)

## ⚠️ IMPORTANT: Activate FormSubmit Email Delivery
On first submission, FormSubmit.co will send a **confirmation email** to hayerhomehealthcare@gmail.com.
**You must click the confirmation link** to activate email delivery.

After that, all form submissions will be emailed automatically.

## Deployment: Netlify (Alternative — Better for Forms)
Netlify handles forms server-side with no extra configuration needed.

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Deploy
netlify deploy --prod --dir .
```

Then connect your Porkbun domain in Netlify → Domain Management.

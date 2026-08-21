# sharpwingstudio.com

Static studio site for **SharpWing Studio**. No build step. Open `index.html` in a browser to preview.

Host: GitHub Pages on a **GitHub Organization** (not a personal user account).  
Registrar: Porkbun (`sharpwingstudio.com` live, `sharpwingstudio.net` redirects here).

---

## What you do once (GitHub org)

You must be logged into GitHub as yourself (`jackdmcgowen`). Nobody “logs in as the studio.”

1. Open [https://github.com/organizations/new](https://github.com/organizations/new)
2. Organization name: **`SharpWingStudio`** (if taken: `sharpwing-studio`)
3. Plan: **Free**
4. You are the Owner
5. Create a **public** repository named **exactly** `<org>.github.io`  
   Example: org `SharpWingStudio` → repo `SharpWingStudio.github.io`
6. Do not add a README / gitignore / license in the GitHub wizard (this folder already has them)

Then push this folder into that repo (GitHub Desktop is fine if you do not want the command line):

```powershell
cd "$env:USERPROFILE\OneDrive\Desktop\sharpwing-studio"
git init
git add .
git commit -m "Initial SharpWing Studio site"
git branch -M main
git remote add origin https://github.com/SharpWingStudio/SharpWingStudio.github.io.git
git push -u origin main
```

Change the `origin` URL if the org slug is different.

7. In the repo: **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: `main` / folder `/ (root)`
   - Custom domain: `sharpwingstudio.com`
   - After the certificate appears (can take up to 24 hours), check **Enforce HTTPS**

Temporary URL before DNS: `https://sharpwingstudio.github.io/`

---

## Porkbun DNS (sharpwingstudio.com)

Domain Management → **DNS** for `sharpwingstudio.com`.  
Leave nameservers on Porkbun. Delete parking / default URL-forward records on `.com` so they do not fight these.

| Type | Host | Answer |
|------|------|--------|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `sharpwingstudio.github.io` |

If the org slug is not `SharpWingStudio`, the CNAME target is `<org>.github.io`.

### sharpwingstudio.net

Domain Management → **URL Forwarding** (not a second website):

- Forward to `https://sharpwingstudio.com`
- Type: **301** permanent
- Include `www` if Porkbun has a checkbox for it

### Email forwarding (free)

Porkbun → **Email Forwarding** on `.com`:

| Alias | Forwards to |
|-------|-------------|
| `hello@sharpwingstudio.com` | the Gmail (or other) inbox you actually read |
| `press@sharpwingstudio.com` | same inbox is fine |

Only change MX records if Porkbun’s forwarding wizard tells you to.

---

## Editing the site later

Change the HTML in this folder, commit, push. GitHub Pages updates in a minute or two.

| File | Page |
|------|------|
| `index.html` | Home |
| `centroid.html` | Game |
| `about.html` | Studio |
| `press.html` | Press kit |
| `contact.html` | Contact |
| `css/site.css` | Look |
| `img/` | Logos and screenshots |
| `CNAME` | Must stay `sharpwingstudio.com` |

When you have a Steam URL, put it on `centroid.html` as a button. When you have a trailer, embed the YouTube URL there.

---

## Local preview

Double-click `index.html`, or from this folder:

```powershell
Start-Process index.html
```

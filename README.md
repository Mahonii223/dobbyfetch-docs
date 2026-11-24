# DobbyFetch Public API Verification Documentation (`dobbyfetch-docs`)

This directory contains a clean, static, self-contained HTML documentation site (zero external CDN dependencies) designed to provide a public HTTPS URL for third-party API application verification:

- **Allegro REST API Developer Portal** (includes English documentation + Polish compliance summary)
- **Shopify Admin API** (Custom/Private app documentation)
- **Google Ads API** (Basic/Standard access verification)

## Files Included

- `index.html` — Single-page technical documentation covering application identity, read-only Allegro REST API scope, other integrations, inline SVG architecture diagram, security controls, and retention policy.
- `privacy.html` — Internal Data Processing & Privacy Policy (GDPR / RODO aligned, with Polish summary), linked from `index.html`.
- `README.md` — Publishing instructions (this file).

---

## Pre-Publication Checklist

Before publishing to a public URL, complete the following steps:

1. **Fill in the highlighted placeholders** in both `index.html` and `privacy.html`:
   - Replace every instance of `[Company Name]` with your legal company name.
   - Replace every instance of `[Administrator Contact Email]` with your official company/administrator email address.
   - *(Optional)* Once replaced, remove the `<span class="placeholder">...</span>` wrapper or restyle it to plain text, and remove the "Pre-Publication Notice" callout box in `index.html` (Section 6).
2. **Verify no sensitive information was added:** Confirm there are no internal IP addresses, database credentials, API keys, or private repository URLs anywhere in `index.html` or `privacy.html`.
3. **Preview locally:** Open `index.html` directly in any web browser and verify that the layout, SVG architecture diagram, and link to `privacy.html` render properly.

---

## Publishing to GitHub Pages (Recommended)

Because the main `DobbyFetch` repository is private, the cleanest and safest approach is to publish **only the contents of `dobbyfetch-docs/`** to a dedicated **public** GitHub repository (e.g., `dobbyfetch-docs`).

### Step 1: Create a New Public GitHub Repository

1. Sign in to GitHub and click **New repository**.
2. Name the repository (for example: `dobbyfetch-docs`).
3. Set visibility to **Public** (required for free GitHub Pages hosting).
4. Leave it empty (do not initialize with a README) and click **Create repository**.

### Step 2: Push `dobbyfetch-docs/` to the New Repository

From a terminal inside `DobbyFetch/dobbyfetch-docs/`:

```bash
cd dobbyfetch-docs
git init
git add index.html privacy.html README.md
git commit -m "Initial public documentation for API verification"
git branch -M main
git remote add origin https://github.com/<your-org-or-username>/dobbyfetch-docs.git
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Open your new `dobbyfetch-docs` repository on GitHub.
2. Go to **Settings** → **Pages** (in the left sidebar).
3. Under **Build and deployment**:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` and folder `/ (root)`
4. Click **Save**.
5. Wait 1–2 minutes for GitHub Actions to publish the site. Your public HTTPS URL will appear at the top of the Pages settings:
   - **Application Homepage URL:** `https://<your-org-or-username>.github.io/dobbyfetch-docs/`
   - **Privacy Policy URL:** `https://<your-org-or-username>.github.io/dobbyfetch-docs/privacy.html`

*(Optional)* Under **Pages** settings, ensure **Enforce HTTPS** is checked.

---

## Alternative: Publishing to Cloudflare Pages

If you prefer hosting under Cloudflare Pages (or a custom company subdomain such as `docs.yourcompany.com`):

1. Push `dobbyfetch-docs/` to a GitHub repository (public or private) as shown above, **or** upload the folder directly via Cloudflare Dashboard → **Workers & Pages** → **Create** → **Pages** → **Upload assets**.
2. If connecting via Git, set **Build command** to empty (static HTML) and **Build output directory** to `/`.
3. Cloudflare will automatically provision an HTTPS URL (`https://<project-name>.pages.dev`) and allow binding a custom domain.

---

## URLs to Submit During API Verification

| Portal | Field | URL to Provide |
| :--- | :--- | :--- |
| **Allegro Developer Portal** | Application Website / Description URL | `https://<your-host>/dobbyfetch-docs/` |
| **Allegro / Shopify / Google Ads** | Privacy Policy URL | `https://<your-host>/dobbyfetch-docs/privacy.html` |

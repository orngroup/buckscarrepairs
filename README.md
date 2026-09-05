# Bucks Car Repairs — website

A single-file website (no build step, no Lovable, no server). Everything runs from `index.html`
plus the images in `/assets`. Works anywhere that serves static files: GitHub Pages, Netlify,
your own hosting, or just double-clicking `index.html` locally.

## What's in this folder

| File | What it is |
|------|-----------|
| `index.html` | The whole website (Home, Services, The Garage, Contact) |
| `404.html` | Copy of index — makes deep links work on GitHub Pages |
| `assets/` | Logo, favicon and all photos |
| `CNAME` | Your custom domain (edit this — see below) |
| `robots.txt`, `sitemap.xml` | For Google |
| `.nojekyll` | Tells GitHub Pages to serve files as-is |

## The WhatsApp button

The contact form and every "WhatsApp" button open WhatsApp with a message pre-filled and
addressed to **07810 778 794** (stored in international format `447810778794`).

To change the number later, open `index.html`, find this line near the top of the script:

```js
var WA_NUMBER = "447810778794"; // 07810 778 794 in international format
```

Replace it with the new number in the same format (country code, no `+`, no spaces, drop the
leading `0`). For a UK mobile `07xxx xxx xxx` → `447xxxxxxxxx`.

> Note: WhatsApp only works with a **mobile** or **WhatsApp Business** number. The landline
> `0330 043 5499` is kept as the "Call" number only.

## Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `buckscarrepairs`).
2. Upload **everything in this folder** (including the `assets` folder) to the repo — drag and
   drop works: on the repo page click **Add file → Upload files**.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source = Deploy from a branch**, **Branch = main**,
   **Folder = / (root)**, then **Save**.
5. Wait 1–2 minutes. Your site is live at `https://<your-username>.github.io/<repo>/`.

## Connect your custom domain

1. Edit the `CNAME` file so it contains exactly your domain, e.g.:
   ```
   www.buckscarrepairs.co.uk
   ```
   (One line, no `https://`, no slash.) It's currently set to `www.buckscarrepairs.co.uk` —
   change it if your domain is different.
2. At your domain registrar (where you bought the domain), add these DNS records:

   **For `www.` (recommended):**
   | Type | Name | Value |
   |------|------|-------|
   | CNAME | `www` | `<your-username>.github.io` |

   **For the root/apex domain (`buckscarrepairs.co.uk` with no www), add four A records:**
   | Type | Name | Value |
   |------|------|-------|
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |

3. Back in **Settings → Pages → Custom domain**, enter your domain and Save.
4. Tick **Enforce HTTPS** once it becomes available (can take up to an hour while the
   certificate is issued).

DNS changes can take anywhere from a few minutes to a few hours to take effect.

## Editing content

All text (services, prices, reviews, FAQs, opening hours) lives in the `SERVICES`, `STATS`,
`REVIEWS`, `FAQS` and `GALLERY` arrays inside the `<script>` in `index.html`. Change the text
there and re-upload the file.

To swap a photo, replace the matching file in `/assets` with a new one of the same name.

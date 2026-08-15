# River Thames Evidence & Representation Programme — public site

Static public website for an independent, source-referenced evidence programme on the
River Thames between Teddington Weir and Richmond.

**Live site:** <https://thamesevidence.org.uk>
**Azure default host:** <https://jolly-flower-06c523503.7.azurestaticapps.net>

| | |
|---|---|
| Azure resource | `swa-teddington-thames-evidence` |
| Resource group | `rg-teddington-rbl-dev` (West Europe) |
| Subscription | Pay-As-You-Go Dev/Test |
| Tier | Free — £0 |
| Deploys from | `main`, via `.github/workflows/azure-static-web-apps-jolly-flower-06c523503.yml` |

Hosted on **Azure Static Web Apps (Free tier)**. Every push to `main` redeploys the site
automatically via GitHub Actions. There is no build step — the files in this repository are
served as-is.

---

## ⚠️ This repository is public

The parent folder on disk (one level up from this repo) contains FOI/EIR correspondence as
`.eml` files. **Those files are deliberately outside this repository** so they cannot be
committed by accident. `.gitignore` also blocks `*.eml`, `*.msg` and similar as a second line
of defence, but the folder boundary is the real protection.

Before committing anything new, check it contains no personal contact details of private
individuals. Official role mailboxes (e.g. `national.requests@environment-agency.gov.uk`) and
published representatives (MPs, councillors) are fine. Named volunteers and personal addresses
are not.

---

## Structure

```
.
├── index.html                  Landing page. Self-contained, inline CSS, no JS.
├── 404.html                    Not-found page, links back to home.
├── staticwebapp.config.json    Routing, 404 override, security headers, image caching.
├── favicon.ico / favicon.svg   Browser-tab icons (waves-and-weir mark).
├── apple-touch-icon.png        iOS home-screen icon.
├── icon-192.png / icon-512.png Manifest icons.
├── site.webmanifest            Web app manifest.
├── robots.txt                  Crawl policy + pointer to the sitemap.
├── sitemap.xml                 Page list for search engines (see SEO section).
├── IMAGE-BRIEF.md              Commissioning brief for new artwork: style, sizes, prompts.
├── .gitignore
├── images/
│   ├── originals/              Full-resolution source illustrations (PNG).
│   ├── web/                    Optimised derivatives the pages serve (WebP + JPEG, 1600w and 800w).
│   ├── topics/                 Drawn SVG topic plates (placeholders where no photo-illustration exists yet).
│   └── brand/                  Logo mark, horizontal lockup, social-share image.
└── docs/
    └── River-Thames-Programme-Dashboard.html
```

Documents live in `docs/`. The landing page links to them at `/docs/<filename>.html`.

---

## Images, branding and SEO

**Naming is deliberate.** Every image file is named descriptively with hyphens —
`river-thames-water-quality-monitoring-teddington-1600.webp`, never `IMG_0231.png` — and every
`<img>` on a page carries descriptive `alt` text. Keep that convention for anything new: the
filename and the alt text are what search engines index.

**Adding an image to a page.** Drop the full-size PNG into `images/originals/` under a
descriptive hyphenated name, then generate four derivatives into `images/web/`:
1600×900 and 800×450, each as `.webp` (quality ~80) and `.jpg` (quality ~82). Reference them
with a `<picture>` block — WebP `<source>` plus JPEG `<img>` fallback — with `loading="lazy"`,
explicit `width`/`height`, and honest alt text. The gallery and lightbox markup in
`index.html` are the template to copy.

**Hero artwork is wired in CSS, not HTML.** Each page's header carries
`class="hero art hero--<topic>"`. The matching rule in `site.css` sets two custom properties:
`--hero-art` (the image) and `--hero-veil` (the navy gradient laid over it). The veil is what
holds text contrast, so if artwork is swapped the text stays readable. Two gotchas, both already
hit once: the modifier rules must be written `header.hero.hero--x{...}` — a bare `.hero--x` loses
on specificity to `header.hero` and silently falls back to the default image; and the drawn SVG
plates in `images/topics/` are already navy, so they take a much lighter veil than a photograph.

**Adding new artwork.** `IMAGE-BRIEF.md` holds the full commissioning brief — house style,
dimensions, filenames and a ready-to-use prompt for every outstanding slot. Follow it rather than
generating ad hoc, so the set stays coherent.

**Honesty rule.** The seven current illustrations are AI-assisted artwork commissioned for the
site. The gallery labels them as illustrations, and they must never be presented as photographs
or evidence — anything presented as evidence gets a source, like every figure on this site.

**The mark.** The logo is a navy badge: a heron standing at the dashed white line of Teddington
Weir — the tidal limit this programme's geography pivots on — above one freshwater and one
tidal wave. `favicon.svg` / `favicon.ico` use a simplified waves-and-weir variant that stays
legible at 16 px. The full lockup is `images/brand/logo.svg`; the social-share card
(`og:image`) is `images/brand/river-thames-evidence-programme-share.jpg`.

**Search engines.** `sitemap.xml` lists all eleven indexable pages and `robots.txt` points
crawlers at it. Both use the canonical custom domain `https://thamesevidence.org.uk`. Every page
carries `<link rel="canonical">` and Open Graph tags.

When you add a page, add a matching `<url>` entry to `sitemap.xml` with its `lastmod`, then
resubmit the sitemap in Google Search Console.


---

## Adding a new document

Three steps, then it's live in about a minute and a half.

**1. Drop the file into `docs/`**

Any self-contained `.html` file. Use hyphens rather than spaces in the filename —
`Water-Quality-Analysis-2026.html`, not `Water Quality Analysis 2026.html`.

**2. Add a card to `index.html`**

Find the `<ul class="doc-grid">` block. Copy an existing `<li class="doc-card">` and edit the
four points marked ①②③④ in the comment:

```html
<li class="doc-card">
  <span class="tag">Analysis</span>
  <h3><a href="/docs/Water-Quality-Analysis-2026.html">Water Quality Analysis</a></h3>
  <p>One or two sentences on what the document contains.</p>
  <p class="foot"><span>Working document · v1 · 12 August 2026</span><span class="open">Open →</span></p>
</li>
```

The grid reflows on its own — no CSS changes needed, at any number of cards.

**3. Commit and push**

```bash
git add . && git commit -m "Add water quality analysis" && git push
```

GitHub Actions picks it up and redeploys. Also update the `<time>` element in the footer of
`index.html` so the "Last updated" date stays honest.

---

## Checking deployment status

```bash
gh run list --limit 5
```

Watch the most recent run to completion:

```bash
gh run watch
```

If a run fails, read the log:

```bash
gh run view --log-failed
```

**One gotcha, already fixed but worth knowing.** `app_location` in the workflow must be `"/"`.
If you ever re-run `az staticwebapp create` from Git Bash on Windows, MSYS silently rewrites a
`"/"` argument into `C:/Program Files/Git/` before the CLI sees it, and Azure writes that
literal path into the workflow — the deploy then fails with *"App Directory Location is
invalid"*. Either edit the workflow back to `"/"` by hand, or prefix the command with
`MSYS_NO_PATHCONV=1`. Running `az` from PowerShell avoids it entirely.

You can also see deployment history in the Azure Portal under the Static Web App resource →
**Environments**, or on GitHub under the **Actions** tab.

Deployments typically take 1–2 minutes. Azure purges its CDN cache automatically on each
deploy, so you do not need to invalidate anything by hand — but your own browser may still
hold an old copy, so hard-refresh (Ctrl+F5) if a change seems missing.

---

## A note on the Content Security Policy

`staticwebapp.config.json` sets a deliberately strict policy:

```
default-src 'none'; style-src 'self' 'unsafe-inline'; img-src 'self' data:;
font-src 'self'; script-src 'none'; object-src 'none';
base-uri 'none'; form-action 'none'; frame-ancestors 'none'
```

This is safe because every current page is pure HTML and CSS with no JavaScript.

**If you add a document that uses JavaScript** — an interactive chart, a sortable table — it
will silently fail to run until you relax the policy. To allow inline scripts, change
`script-src 'none'` to:

```
script-src 'self' 'unsafe-inline'
```

Prefer `'self'` with the script in a separate `.js` file over `'unsafe-inline'` where you can;
it's meaningfully stronger. Similarly, `img-src` currently allows only same-origin images and
`data:` URIs — add a host there if you ever embed an image from elsewhere.

`frame-ancestors 'none'` means no other site can embed these pages in an iframe. If you ever
want a partner organisation to embed a document, that directive is what to change.

---

## Adding a custom domain later

The site is built so this needs no rework — all internal links are root-relative (`/docs/...`),
so they keep working unchanged under any domain.

When you're ready:

1. **Buy the domain** from any registrar. Azure does not need to be the registrar.

2. **Add it in Azure.** In the Portal, open the Static Web App → **Custom domains** → **Add**.
   Or via CLI:

   ```bash
   az staticwebapp hostname set \
     --name <app-name> \
     --resource-group <resource-group> \
     --hostname www.example.org
   ```

3. **Create the DNS record** your registrar needs:
   - **Subdomain** (e.g. `www.example.org`) — a `CNAME` pointing at the
     `<generated-name>.azurestaticapps.net` hostname.
   - **Apex/root** (e.g. `example.org`) — an `ALIAS`/`ANAME` record if your DNS provider
     supports one, or use Azure DNS and let Azure create an alias record. A plain `CNAME`
     is not valid at the apex.

   Azure will show the exact record and a validation token to add.

4. **Wait for validation.** Azure verifies the record, then issues and installs a **free
   managed TLS certificate** automatically. It renews itself; there is nothing to diary.

5. **Update the site.** Set your preferred canonical domain, and consider adding a
   `<link rel="canonical">` to `index.html` once the domain is settled.

Custom domains and managed certificates are **included in the Free tier** — adding one costs
nothing. The Free tier allows two custom domains per app.

---

## Cost

Everything here is on the **Free** Static Web Apps tier: 100 GB bandwidth per month, 0.5 GB
storage, free managed TLS, two custom domains. No cost is incurred by this site as configured.

Free-tier apps have no SLA. For a public evidence site that is normally an acceptable trade;
upgrading to Standard (a paid tier) would add an SLA, more custom domains and private
endpoints, and can be done later without redeploying.

---

## Local preview

Because links are root-relative, opening `index.html` straight from the filesystem will not
resolve `/docs/...`. Serve the folder over HTTP instead:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

Note that `staticwebapp.config.json` is **not** applied by a plain HTTP server — security
headers and the 404 page only take effect on Azure. To emulate those locally, use the Static
Web Apps CLI:

```bash
npx @azure/static-web-apps-cli start .
```

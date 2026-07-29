# Ryan Contracting — Company Apps Hub

A single landing page that links to all of Ryan Contracting Company's internal web tools.

**One file. No backend. No dependencies.** The logo is embedded directly in `index.html`, so the page works even if you email it to someone or open it off a USB stick.

```
ryan-hub/
├── index.html   ← the entire page (HTML + CSS + logo, all inline)
├── CNAME        ← the custom domain: apps.ryancont.com
└── README.md    ← this file
```

---

## Currently linked

| Tile | URL | Who it's for |
|---|---|---|
| Applicant Tracking | http://applicants.ryancont.com | Office & hiring managers |
| Repair Submissions | https://requests.ryancont.com/ | Field crews (phones) |
| Repair Dashboard | https://repairdashboard.ryancont.com | Shop & managers |
| FleetView | https://ryan-fleetview.vercel.app/ | Shop, PMs & dispatch |

The grid lays out 2 across on a desktop and 1 on a phone.

---

## Get it online — about 10 minutes

### 1. Create the repo

1. Go to [github.com/new](https://github.com/new).
2. **Owner:** `andrewjryan1-ops` (same account as the applicant tracker).
3. **Repository name:** `ryan-hub`
4. **Visibility:** **Public** is fine here — this page has no sensitive data on it, just links. (The sites it points to keep their own protection.)
5. Do **not** initialize with a README — you already have one.
6. **Create repository**.

### 2. Push these files

Open a terminal in this `ryan-hub` folder:

```bash
git init
git add .
git commit -m "Company apps landing page"
git branch -M main
git remote add origin https://github.com/andrewjryan1-ops/ryan-hub.git
git push -u origin main
```

### 3. Turn on GitHub Pages

1. Repo → **Settings** → **Pages**.
2. **Source:** Deploy from a branch · **Branch:** `main` / `/ (root)` → **Save**.
3. Under **Custom domain**, enter `apps.ryancont.com` → **Save**.
4. Check **Enforce HTTPS** once it becomes available (a few minutes after DNS resolves).

### 4. Point the DNS

Wherever `ryancont.com` DNS is managed (same place you set up `applicants.ryancont.com`), add:

| Type | Name | Value |
|---|---|---|
| CNAME | `apps` | `andrewjryan1-ops.github.io` |

Give it 5–30 minutes to propagate, then visit **https://apps.ryancont.com**.

> Want a different subdomain — `hub`, `start`, `tools`? Change it in **two** places: the `CNAME` file in this folder, and the DNS record name. They have to match.

---

## Adding a new site later

Open `index.html` and find this comment:

```html
<!-- ============ ADD NEW SITES BY COPYING ONE <a class="card"> BLOCK ============ -->
```

Copy any one of the three `<a class="card"> … </a>` blocks, paste it below the others, and change four things:

1. `href="..."` — the new site's URL
2. `<h2>…</h2>` — the tile name
3. `<p>…</p>` — the one-paragraph description
4. `<span class="who">…</span>` — who it's for
5. `<span class="url">…</span>` — the URL shown at the bottom of the tile

The grid re-flows on its own — 3 across on a desktop, 2 on a tablet, 1 on a phone. No layout work needed.

To swap the icon, grab any outline SVG (e.g. from [lucide.dev](https://lucide.dev)) and paste its `<path>` elements inside the `<svg viewBox="0 0 24 24">` in the `.icon` div.

Then:

```bash
git add index.html
git commit -m "Add <new site>"
git push
```

GitHub Pages redeploys in about a minute.

---

## Branding

- **Ryan Navy** `#221859` — header, headings, icon tiles
- **Ryan Navy Mid** `#43368D` — gradient partner
- **Ryan Orange** `#EC6303` — accent bar, arrows, "who it's for" chips
- **35th Anniversary logo** (white knockout) in the header

---

## Tips for rollout

- Set it as the **browser homepage** on office and shop computers — Chrome: Settings → On startup → Open a specific page → `https://apps.ryancont.com`.
- On phones, open it in Safari/Chrome → Share → **Add to Home Screen**. It gets the 35-year logo as its icon and opens like an app.
- A **QR code** for `apps.ryancont.com` posted in the shop and in trucks gets crews to all three tools with one scan.

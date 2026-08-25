# Putting your site online — pick one

The whole site is a single file: `index.html`. No build step, no dependencies, no framework to install. That's deliberate — it means it loads instantly and can be hosted anywhere for free, forever.

---

## Option A — Netlify Drop (fastest, ~2 minutes)

Best if you just want a link today.

1. Put `index.html` in a folder on its own, e.g. a folder called `isita-site`.
2. Go to **https://app.netlify.com/drop**
3. Drag that **folder** (not the file) onto the page.
4. It deploys immediately and gives you a URL like `random-name-123.netlify.app`.
5. Sign up (free) to keep it permanently, then go to **Site configuration → Change site name** and set it to `isitaghosh` → your URL becomes **`isitaghosh.netlify.app`**.

To update later: drag the new folder onto the same site's *Deploys* tab.

---

## Option B — GitHub Pages (best long-term, looks great on a résumé)

Gives you `isitaghosh.github.io` — a URL that reads as your own.

1. Create a GitHub account if you don't have one, using the username **`isitaghosh`** (the username becomes the URL).
2. Create a **new public repository** named exactly `isitaghosh.github.io`.
3. On the repo page click **Add file → Upload files**, drag in `index.html`, and click **Commit changes**.
4. Wait about a minute. Your site is live at **`https://isitaghosh.github.io`**.

To update later: edit or re-upload `index.html` in that repo.

---

## Adding a custom domain (optional, ~₹800/year)

If you later want `isitaghosh.com`, buy the domain from Namecheap/GoDaddy/Cloudflare and point it at Netlify or GitHub Pages — both support custom domains free, with free HTTPS. Happy to walk you through it when you get there.

---

## Sharing it on LinkedIn

- **Profile → Contact info → Add website** → paste the URL, label it "Portfolio".
- Add it in your **About** section too — the contact panel is easy to miss.
- When you post about it, paste the raw URL in the post body (not just a comment); LinkedIn's reach favours posts where the link preview renders.

---

## Editing the content yourself

Open `index.html` in any text editor. The content is plain HTML near the bottom half of the file and is commented by section:

```
<!-- ============ HERO ============ -->
<!-- ============ STATS ============ -->
<!-- ============ EXPERIENCE ============ -->
<!-- ============ SKILLS ============ -->
<!-- ============ CREDENTIALS ============ -->
<!-- ============ CONTACT ============ -->
```

To add a new job, copy an entire `<article class="entry">…</article>` block and edit the text. To add a project inside a job, copy a `<details class="proj">…</details>` block.

### Swapping in the official certification badges

The credential cards currently use custom hexagon marks (`MCD 1`, `MCD 2`, `SF AI`)
drawn in the site's own palette. If you'd rather show the real Salesforce-issued
badge artwork:

1. Download the PNGs from your Trailhead profile → **Credentials**, or from Credly
   if your certs are issued there. Save them at around 240×240.
2. Make a `badges/` folder next to `index.html` and drop them in, e.g.
   `badges/mcd1.png`.
3. In the `CREDENTIALS` section, replace the badge block:

```html
<!-- from -->
<span class="badgemark"><span class="face">…</span></span>
<!-- to -->
<span class="badgemark art"><img src="badges/mcd1.png" alt=""></span>
```

The `.art` variant drops the hexagon frame and just shows the image, so the
official badge shape comes through unaltered. Leave `alt=""` — the credential
name is already right beside it, so a screen reader would otherwise read it twice.

Use the official artwork only for certifications you actually hold; the badge is
issued to you and its licence covers exactly that.

### Verify links

Each certification card links to Salesforce's public credential-verification page.
Replace those `href`s with your personal Trailhead profile URL once you have it —
a recruiter clicking through to your name is far more convincing than a generic
lookup form.

---

Colours live at the very top of the `<style>` block as CSS variables (`--accent`, `--ground`, `--ink`), with the dark-mode values just below. Changing `--accent` in both places re-themes the whole site.

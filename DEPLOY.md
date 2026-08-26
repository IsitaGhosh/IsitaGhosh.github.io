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

### Certification badges and certificates

The credential cards use the **real Salesforce badge artwork**, cut straight out of
your issued certificates and knocked out to transparent PNGs so they sit correctly
on both the light and dark themes:

```
badges/         mulesoft-developer-1.png    (160×160, transparent)
                mulesoft-developer-2.png
                salesforce-ai-associate.png
certificates/   mulesoft-developer-1.jpg    (full certificate, opened on click)
                mulesoft-developer-2.jpg
                mulesoft-developer-2.pdf    (the original download)
                salesforce-ai-associate.jpg
```

Clicking a card opens the full certificate in a new tab. The "Emerging Award" keeps
a drawn hexagon mark, since an employer award has no issued badge artwork.

**To add a new certification:** drop the badge PNG in `badges/` and the certificate
image in `certificates/`, then copy an existing `<a class="cert">` block in the
`CREDENTIALS` section and change the two paths, the name, and the sub-line. Keep
`alt` describing the badge — the credential name sits right beside it.

Your original downloads (`1736414723486.jpeg` and friends) are listed in
`.gitignore`, so they stay on your Mac and never reach the public repo. Safe to
delete once you're happy with the site.

---

Colours live at the very top of the `<style>` block as CSS variables (`--accent`, `--ground`, `--ink`), with the dark-mode values just below. Changing `--accent` in both places re-themes the whole site.

---

## Visitor analytics

The site sends a page view to **GoatCounter**, a privacy-friendly analytics
service. The snippet sits just before `</body>` in `index.html`.

**Before it records anything you must claim the account:**

1. Go to **https://www.goatcounter.com/signup**
2. Set the site code to exactly **`isitaghosh`** — that is what the snippet
   already points at. If you pick a different code, change both places in the
   snippet to match.
3. Free plan, personal use. No card needed.

Your dashboard is then at **https://isitaghosh.goatcounter.com**, behind your
login. Nobody else can see it.

**What it shows you:** total views, views per day, which page, the referrer
(so you can tell when someone arrived from LinkedIn or a job application),
country, browser and screen size.

**What no analytics tool can show you:** the names of individual visitors. See
the note below.

### Why there is no "who viewed my profile"

LinkedIn can name your visitors because they are logged into LinkedIn and
agreed to that in LinkedIn's terms. A public website has no such relationship
with the people who open it — the only things a browser sends are an IP
address, a user agent and a referrer. None of those is a person's name.

So: use **LinkedIn's own "Who viewed your profile"** for identity, and
GoatCounter for how many people reach the site and where they came from.
Together they answer most of the question.

Reverse-IP tools that claim to name the *company* a visitor came from do exist,
but they are paid, they guess, and they are close to useless for anyone on home
broadband or mobile data. Not worth it for a personal portfolio.

### Reaching your dashboard from the site

Open **https://isitaghosh.github.io/#admin** and an *Analytics* button appears in
the bottom-right corner, linking to your GoatCounter dashboard. Without the
`#admin` on the end, the button does not render at all.

To be clear about what this is and is not: the link is in the page source, so it
is not a secret. It does not need to be. What keeps your numbers private is that
**the dashboard requires your GoatCounter login** — a stranger who found the
button would land on a login screen. The `#admin` fragment is a convenience so
the button stays out of the way of visitors, not a security control.

### Knowing who looked: tagged links

You cannot learn a stranger's name from a website visit — see the note above.
But for anyone you send the link to *yourself*, you can tag the link and know
exactly whose visit it was.

GoatCounter reads a `ref` (or `campaign`) query parameter automatically and
groups visits under it in the **Campaigns** widget on your dashboard. No setup
needed — a new tag appears the first time it is used.

Send a different link to each person or application:

```
https://isitaghosh.github.io/?ref=rahul
https://isitaghosh.github.io/?ref=tcs-application
https://isitaghosh.github.io/?ref=linkedin-post-aug
https://isitaghosh.github.io/?ref=infosys-recruiter
```

The page looks identical to them — the parameter is invisible in the layout.
On your dashboard you then see which tag the visit came from, so you know
*which application* or *which person* produced it.

This is the practical answer to "who viewed my profile" for a public site:
you cannot identify people who find you on their own, but you can absolutely
tell apart the people you reached out to.

Recognised parameters: `ref`, `src`, `source`, `utm_source` for the source, and
`campaign` or `utm_campaign` for the campaign name.

### Turning it off

Delete the `<script data-goatcounter=...>` tag at the bottom of `index.html`.
Nothing else depends on it.

### The link preview image

`og.png` (1200x630) is what LinkedIn, WhatsApp, Slack and email show when the
site is shared. It is generated from the site's own design, so it stays on
brand.

To regenerate it after a change, recreate the small template and screenshot it
at exactly 1200x630 with headless Chrome. The meta tags in `index.html` point at
`https://isitaghosh.github.io/og.png?v=1` - **bump that `?v=` number whenever you
replace the image**, or the networks will keep serving the cached old one.

**LinkedIn caches previews hard.** After changing the image, paste the URL into
**https://www.linkedin.com/post-inspector/** and hit inspect; that forces
LinkedIn to re-fetch. Without it, an old or missing preview can persist for
weeks.

### Where to put the link on LinkedIn

1. **Featured section** - Profile, Add profile section, Recommended, Add
   featured, Add a link. Most visible: renders a large card using `og.png`.
2. **Contact info** - the pencil icon under your headline, Add website, type
   "Portfolio".
3. **About** - paste the raw URL at the end. Not clickable, but read more often
   than the contact panel.
4. **Each Experience entry** - Add media, Link, so it shows against Prowess and
   Exavalu too.

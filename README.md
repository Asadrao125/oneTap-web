# oneTap website

A tiny, dependency-free static site: a waitlist landing page and a privacy policy.
No build step, no framework — just `index.html`, `privacy.html`, and `styles.css`.

## Files

- `index.html` — landing page with features, how-it-works, screenshots, and a waitlist form
- `privacy.html` — privacy policy
- `styles.css` — shared styles for both pages
- `screenshots/` — real app screenshots shown in the "See it in action" section — must be
  uploaded/pushed along with the HTML/CSS files, or those images will 404 on the live site

## 1. Deploy free with GitHub Pages (~5 minutes)

1. Create a new **public** GitHub repository (e.g. `onetap-website`). Don't add a README —
   you already have one here.
2. Upload `index.html`, `privacy.html`, `styles.css`, and the whole `screenshots/` folder to
   the repo (drag-and-drop on github.com works fine, or via git):
   ```bash
   git init
   git add index.html privacy.html styles.css screenshots README.md
   git commit -m "Add oneTap landing page"
   git branch -M main
   git remote add origin https://github.com/<your-username>/onetap-website.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment," set **Source** to `Deploy from a branch`, branch `main`,
   folder `/ (root)`. Save.
5. GitHub will give you a live URL within a minute or two, usually:
   `https://<your-username>.github.io/onetap-website/`

That's it — it's free, HTTPS is automatic, and any push to `main` updates the live site.

### Optional: a custom domain

If you buy a domain later (e.g. from Namecheap, Cloudflare, Google Domains), add a `CNAME`
file to the repo containing just your domain (e.g. `onetap.app`), then point your domain's
DNS at GitHub Pages following
[GitHub's custom domain guide](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).
GitHub Pages itself stays free either way — you'd only be paying for the domain name.

## 2. Make the waitlist form actually work (2 minutes)

The form on `index.html` posts to [Formspree](https://formspree.io), a free service that
forwards form submissions to your email with no backend code needed.

1. Go to [formspree.io](https://formspree.io) and sign up free (50 submissions/month on the
   free plan — plenty for a waitlist).
2. Create a new form, set the target email to wherever you want signups delivered.
3. Formspree gives you a form ID / endpoint URL like `https://formspree.io/f/abcd1234`.
4. In `index.html`, find this line:
   ```html
   <form class="waitlist-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST" id="waitlistForm">
   ```
   and replace `YOUR_FORM_ID` with your real form ID.
5. Push the change — the form now emails you every signup.

Until you do this, the form is visible but won't actually deliver anywhere — swap in your
form ID before sharing the link publicly.

## Editing content

Everything is plain HTML/CSS — open the files in any editor, no build tools required.
Colors, spacing, and layout live in `styles.css` under the `:root` variables at the top if
you want to tweak the theme.

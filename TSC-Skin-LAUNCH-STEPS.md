# TSC Skin — how to publish the website

Domain: **tscskin.com** (registered with Fasthosts)
Files: **tsc-skin-website.zip** — unzip it; you need the *contents* of the `tsc-skin` folder.

---

## Step 1 — GitHub (about 5 minutes)

1. Sign up at **github.com**.
2. Click **+** (top right) → **New repository**.
3. Name it `tsc-skin`, set it to **Public**, click **Create repository**.
4. On the next page click **uploading an existing file**.
5. Open the `tsc-skin` folder and drag **its contents** into the browser — not the folder itself.
   `index.html` must end up at the top level, with `images` and `videos` beside it.
6. Scroll down, click **Commit changes**.

## Step 2 — Netlify (about 10 minutes)

1. Go to **netlify.com** → **Sign up** → **Sign up with GitHub**.
2. **Add new site** → **Import an existing project** → **Deploy with GitHub** → authorise → pick `tsc-skin`.
3. Leave **build command** and **publish directory** blank. There is no build step.
4. Click **Deploy**. In about a minute you get a test URL like `sparkly-cat-a1b2c3.netlify.app`.

**Test properly here before going further:** does the video play, does the enquiry popup open,
and do the Doctify widgets display instead of showing an error?

## Step 3 — Point the domain (5 minutes, then waiting)

**In Netlify:** Domain settings → **Add domain** → `tscskin.com` → Verify → Add.

**In Fasthosts:** Control Panel → Domains → tscskin.com → **DNS / Advanced DNS**
(sometimes labelled "Manage DNS"):

| Type  | Host | Points to |
|-------|------|-----------|
| A     | `@` (or blank) | `75.2.60.5` |
| CNAME | `www` | `your-site-name.netlify.app` (no https://, no trailing slash) |

**Delete any existing A record for `@`** that points at the Fasthosts parking page,
otherwise it will compete with the new one. Then save.

Wait: usually under an hour, occasionally up to 24. HTTPS (the padlock) is issued
automatically by Netlify once it sees the records — nothing to do.

## Updating the site afterwards

Upload the changed file to GitHub (drag and drop in the browser) and the live site
refreshes itself within a minute.

---

## Before real visitors arrive

- [ ] **Formspree endpoint** — sign up free at formspree.io, create a form, and paste the
      endpoint into `FORM_ENDPOINT` in index.html. Without it, enquiries fall back to opening
      the patient's own email app, which loses some of them.
- [ ] **Doctify** — ask them to whitelist `tscskin.com`, or visitors may see a 403 error
      where the review widgets should be.
- [ ] **Real terms & conditions** — `terms.html` is currently a placeholder template.
- [ ] **UK GDPR privacy notice** — the enquiry form collects personal and health-related
      data, including for under-18 patients.
- [ ] BAD membership badge, if you want it alongside the BMLA and Bupa ones.

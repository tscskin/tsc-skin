# TSC Skin — website

Everything the website needs is in this folder.

| File / folder | What it is |
|---|---|
| `index.html` | The entire website — structure, styling and content |
| `terms.html` | Terms & conditions page (**placeholder — must be replaced before launch**) |
| `images/` | Logos, treatment photos, portrait, credential badges |
| `videos/hero.mp4` | The background video at the top of the page |

## Viewing it
Double-click `index.html` and it opens in your browser. No internet or software needed
(though the Doctify widgets need a connection, and only display once the site is hosted
on your real domain).

## Editing the content
Open `index.html` in any text editor and scroll to the section marked:

```
EDIT YOUR CONTENT HERE
```

Everything you'd change day to day lives there:

| To change... | Edit... |
|---|---|
| Email address, social links | the `SITE` block |
| Clinic locations, days, hours, addresses | `SITE.locations` |
| Treatments and their photos | `SERVICES` |
| Enquiry form dropdown options | `ENQUIRY_REASONS` |
| Journal posts | `POSTS` |
| Biography and philosophy | `ABOUT_HTML` |
| Press logos | `FEATURED` |
| Where enquiries are sent | `FORM_ENDPOINT` |

**Golden rules:** only change text between quote marks, keep the commas at line ends,
and save a copy before big edits.

## Updating through Claude
Save this project in Claude and describe the change you want ("add a journal post about
summer SPF", "change Solihull hours to 10–3"). Claude edits the file and returns the new
version to upload.

## Publishing
1. Create a free GitHub account and upload this folder to a new repository.
2. Connect the repository to Netlify or Vercel (both free) — the site goes live in minutes.
3. Point tscskin.com at the host using the instructions they provide.

To update afterwards: upload the changed file(s) to GitHub and the live site refreshes itself.

## Still to do before launch
- [ ] **Formspree endpoint** — sign up at formspree.io, create a form, paste the endpoint
      into `FORM_ENDPOINT` in index.html. Without it, enquiries fall back to opening the
      patient's own email app.
- [ ] **Doctify** — ask them to whitelist tscskin.com, or the review widgets will show a
      403 error to visitors.
- [ ] **Real terms & conditions** in terms.html (currently a placeholder template).
- [ ] **UK GDPR privacy notice** — the enquiry form collects personal and health-related
      data, including for under-18s.
- [ ] BAD membership badge, if you want it alongside the BMLA and Bupa ones.

## Publishing to tscskin.com (Fasthosts domain)
1. **GitHub** — create a free account, make a public repository named `tsc-skin`, and
   upload the *contents* of this folder (index.html at the top level, with images/ and
   videos/ beside it).
2. **Netlify** — sign up with GitHub, then Add new site → Import an existing project →
   pick the repository. Leave build command and publish directory blank. You get a live
   test URL in about a minute. Check the video, the enquiry form and the Doctify widgets.
3. **Fasthosts DNS** — in Netlify, Domain settings → Add domain → tscskin.com. Then in
   the Fasthosts control panel, under Domains → your domain → DNS:
   - A record: host `@` → `75.2.60.5`
   - CNAME record: host `www` → your-site-name.netlify.app
   - Delete any existing `@` A record pointing at Fasthosts' parking page.
   Allow up to 24 hours. HTTPS is issued automatically.

## Handing it to a developer
Send them this folder or add them to your GitHub repository. It is standard
HTML/CSS/JavaScript in a single file with no build step, framework or dependencies —
any web developer can pick it up immediately.

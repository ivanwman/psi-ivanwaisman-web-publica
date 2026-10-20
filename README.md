# psi.ivanwaisman.com — public pages

This repo holds the public pages of the site. It deploys to its own Vercel project, and
psi.ivanwaisman.com forwards to it every address that the main (private) project doesn't serve.
**Once the setup is finished, a push to `main` goes live on psi.ivanwaisman.com within a minute or two.**

| URL | File |
|-----|------|
| `/`, `/es` | `index.html` |
| `/en` | `index-en.html` |
| `/robots.txt`, `/sitemap.xml` | same names |
| any address that doesn't exist | `404.html` |

New page: add the file, plus a rewrite in `vercel.json` if it needs a short address. Nothing has
to change on the main project.

## What stays in the main project (not here)

- **The new-patient form (`/intake`) and the privacy pages (`/privacidad`, `/privacy`).** Patients
  enter clinical data there, so they stay under Iván's direct control. On this project's own
  `.vercel.app` address they redirect to the live site.
- **Images that already exist** (`media/…`, `favicon.png`, `consultorio.jpg`). The patient portal
  and other private pages use them too, so the main project keeps serving its own copies.
  Replacing one of these files here changes nothing on the live site. To use a different image,
  add it under a **new name**; new files are served from here.
- The patient portal, admin panel and `/api` routes.

## Rules

- **Consent first.** Many visitors are in the EU. Google Analytics only loads after the visitor
  accepts the cookie banner (see `window.cargarAnalytics` in `index.html`). Any Ads / GTM tag must
  go through the same gate (or Consent Mode v2 defaulting to *denied*). Never load it before consent.
- **New or rewritten pages** go to a branch first; send Iván the preview link and merge after his OK.
  Small SEO changes (titles, descriptions, robots.txt, sitemap.xml) can go straight to `main`.
- **Don't touch:** the `GAS` URL / routing script in `index.html`.
- **Generated parts.** Iván's tools write some parts of these files and push them here as normal
  commits. Edit around them, not inside them:
  - the JSON-LD block (`<script type="application/ld+json">`) and the `#areas` section of `index.html`
  - the testimonials between `<!-- testimonios:start -->` and `<!-- testimonios:end -->`
  - **`index-en.html` as a whole**: it's regenerated from `index.html`. Make changes in
    `index.html`, and tell Iván so the English version is regenerated; direct edits to
    `index-en.html` get overwritten.
- Pull before you push: Iván's tools also commit to `main`.

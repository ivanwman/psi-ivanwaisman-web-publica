# psi.ivanwaisman.com — public pages

This repo holds only the public pages of the site, as they are live today. The rest of the
system (backend, patient portal, admin panel) is not included and is not needed for Ads work.

| URL | File |
|-----|------|
| `/` | `index.html` |
| `/en` | `index-en.html` |
| `/intake` (new patient form — main conversion) | `intake-vercel.html` |
| `/privacidad`, `/privacy` | `privacidad-vercel.html`, `privacidad-en-vercel.html` |

## Please keep in mind

- **This repo does not deploy.** Changes are reviewed and merged into the main project by hand.
  Please send them as a pull request.
- **Consent first.** The site serves EU visitors. Google Analytics only loads after the visitor
  accepts the cookie banner (see `window.cargarAnalytics` in `index.html`). Any Ads / GTM tag must
  go through the same gate (or Consent Mode v2 defaulting to *denied*). Never load it before consent.
- **Don't touch:** the JSON-LD block and the `#areas` section of `index.html` (both are generated
  and get overwritten), the `GAS` URL / routing script in `index.html`, and the `/api/intake` calls
  in `intake-vercel.html`.
- `index-en.html` is generated from `index.html`. Edit `index.html`; English changes are ported by hand.
- The intake form can't be submitted locally (its backend isn't here). Test conversions on the live
  site with Tag Manager's preview mode.

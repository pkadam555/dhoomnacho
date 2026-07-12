# dhoomnacho website

Static marketing site for the DhoomNacho app, deployed via GitHub Pages from this repo (`pkadam555/dhoomnacho`, `main` branch, root).

**Live URL (current)**: https://pkadam555.github.io/dhoomnacho/
**Intended custom domain** (used in meta tags / store listing): https://dhoomnacho.app — **not yet set up**, see below.

## App-ads.txt setup

`app-ads.txt` ([IAB Tech Lab spec](https://iabtechlab.com/ads-txt/)) declares which companies are authorized to sell ads on this app, and is required by AdMob for ad serving.

1. **File location**: [`app-ads.txt`](app-ads.txt) lives at the repo root, so GitHub Pages publishes it to `https://pkadam555.github.io/dhoomnacho/app-ads.txt`. The domain it's served from must match exactly what's entered on Google Play / the App Store listing as the developer website.
2. **Contents** — AdMob publisher line:
   ```
   google.com, pub-3790746534786906, DIRECT, f08c47fec0942fa0
   ```
3. **Publish**: push to `main` — GitHub Pages redeploys automatically. No subpath under the domain root.
4. **Verify**: in AdMob, go to **Sites/Apps → your app → App-ads.txt status**, and let Google crawl the file to confirm it's found and formatted correctly. This can take a few moments, sometimes longer.

### ⚠️ Custom domain (`dhoomnacho.app`) is not configured yet

The site's meta tags (`og:url`, `og:image`, Play Store deep links) and this README's original assumption all reference `dhoomnacho.app`, but:
- There's no `CNAME` file in this repo.
- `dhoomnacho.app` does not currently resolve (no DNS record).

Until the custom domain is set up, `app-ads.txt` is only reachable at `https://pkadam555.github.io/dhoomnacho/app-ads.txt`. **AdMob/Play Store verification will only pass against whatever domain is entered on the store listing** — so either:
- Register `dhoomnacho.app`, point its DNS at GitHub Pages, and add a `CNAME` file to this repo (see [GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)), then re-verify `app-ads.txt` at `https://dhoomnacho.app/app-ads.txt`, **or**
- Update the Play Console "Developer website" field to `https://pkadam555.github.io/dhoomnacho/` and verify against that URL instead.

If the crawl ever fails, check that:
- The file is at the domain root, not nested in a subfolder.
- The domain matches the store listing exactly (including `www` vs. no `www`).
- The deployment actually published the latest `app-ads.txt` (check the live URL directly in a browser).

# dhoomnacho website

Static marketing site for the DhoomNacho app, deployed to [dhoomnacho.app](https://dhoomnacho.app).

## App-ads.txt setup

`app-ads.txt` ([IAB Tech Lab spec](https://iabtechlab.com/ads-txt/)) declares which companies are authorized to sell ads on this app, and is required by AdMob for ad serving.

1. **File location**: [`app-ads.txt`](app-ads.txt) lives at the repo root, so it publishes to `https://dhoomnacho.app/app-ads.txt` (the domain must match exactly what's entered on Google Play / the App Store listing).
2. **Contents** — AdMob publisher line:
   ```
   google.com, pub-3790746534786906, DIRECT, f08c47fec0942fa0
   ```
3. **Publish**: deploy this repo (GitHub Pages) so the file is served from the domain root — no subpath.
4. **Verify**: in AdMob, go to **Sites/Apps → your app → App-ads.txt status**, and let Google crawl `https://dhoomnacho.app/app-ads.txt` to confirm it's found and formatted correctly. This can take a few moments, sometimes longer.

If the line above is ever missing or the crawl fails, check that:
- The file is at the domain root, not nested in a subfolder.
- The domain matches the store listing exactly (including `www` vs. no `www`).
- The deployment actually published the latest `app-ads.txt` (check `https://dhoomnacho.app/app-ads.txt` directly in a browser).

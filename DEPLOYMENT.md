# Deploy version 9

1. Extract this ZIP.
2. Replace the existing `index.html`, `manifest.json`, and `sw.js` files in the root of the GitHub Pages repository with the extracted versions.
3. Commit and push the changes, then wait for GitHub Pages to finish deploying.
4. Open the live website once with `?v=9` at the end of its address, for example: `https://YOUR-SITE.github.io/?v=9`.
5. Refresh once. The version 9 service worker will take control and future updates will check the network for the app page before using its offline cache.

If the app was installed as a phone home-screen app and still shows the old version, remove that installed shortcut, open the `?v=9` address in the browser, then install it again.

The changed pages are:

- **Dashboard**: Nannybear branding and live employment overview values.
- **Nanny**: blank starter profile, masked ID and bank account values, and flexible children list.
- **Settings**: Account Management, Activity Log, Sync & Backup.
- **Home screen**: black-bear and white-bear Nannybear app icon.

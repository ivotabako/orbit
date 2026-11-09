# Orbit

A front-end-only React application for browsing YouTube subscriptions. Run `npm install`, then `npm run dev`. Production: `npm run build`.

## Deployment

Pushes to `main` now trigger automatic deployment to GitHub Pages via [deploy-pages.yml](./.github/workflows/deploy-pages.yml). The production build uses the repository path as Vite `base` during GitHub Actions so assets resolve correctly on project pages.

The first launch displays labeled sample channels. Search, topic filters, favorites, grid/carousel browsing, and local visit ranking work immediately. Visits count channel links opened from Orbit, not YouTube watch history. All library data is stored in localStorage; export JSON for backup or device transfer.

## Connect your subscriptions

Enable YouTube Data API v3 in a Google Cloud project. Configure the OAuth consent screen and add your account as a test user if needed. Create an OAuth Web application client and authorize the exact app origin (e.g. http://127.0.0.1:5173). Enter its public client ID in Connection & data. No client secret or server is required. The app requests only youtube.readonly and fetches every subscription page. Access tokens stay in memory and are never written to localStorage. Reconnect to refresh. Public distribution may require Google OAuth verification.

Alternatively import Google Takeout's YouTube subscriptions.csv. Import replaces the current library. Orbit JSON exports preserve favorites and visits as well. Sample imagery is illustrative and loaded from Unsplash; real synced channels use YouTube thumbnails. Google Fonts are loaded remotely. No analytics.


Unsubscribing is handled on the channel's YouTube page, keeping the initial app read-only. No backend is needed unless you want cross-device synchronization, unattended refresh, or shared accounts. Orbit cannot measure visits in other apps, detect shadow bans, or retrieve unavailable channels.

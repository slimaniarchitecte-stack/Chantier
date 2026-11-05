# Deploying Chantier

Five files, no build step, no framework. Upload them and you have a URL.

## GitHub Pages, from the browser, no command line

1. Go to github.com and sign in. If you have no account, make one; it's free.
2. Click **+** at the top right, then **New repository**.
3. Name it `chantier`. Set it to **Public**. Pages won't serve a private repo on a free account. Don't tick "Add a README". Click **Create repository**.
4. On the empty repo page, click **uploading an existing file**.
5. Drag in all five files: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`. They go at the top level, not inside a folder.
6. Click **Commit changes**.
7. Go to **Settings** → **Pages** in the left sidebar. Under "Build and deployment", set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
8. Wait a minute or two, then reload that page. It shows your URL: `https://<your-username>.github.io/chantier/`

## Changing it later

Open `index.html` in the repo on github.com, click the pencil icon, edit, commit. Live within a minute. Works from your phone.

Two things to know when you edit:

- The plan lives in the `S` object (what each session is) and the `PLANS` object (which sessions fall on which weekday in each phase). Weekday 0 is Sunday.
- If you change anything, bump the cache name at the top of `sw.js` (`rebuild-20261105-1` → `-2`). Otherwise phones that already installed the app keep serving the old version from cache.

## Adding it to your home screen

**iPhone:** open the URL in Safari, tap the Share button in the bottom bar, scroll to **Add to Home Screen**, name it, Add. Safari specifically; Chrome on iOS won't do it.

**Android:** open the URL in Chrome, tap the three dots, then **Install app** or **Add to Home screen**.

Once installed it opens without the browser bars and works with no signal.

## Your data

It lives in your browser's storage, on that one device. It does not sync to your laptop and nobody else can see it. Clearing your browser data erases it.

So: **Objectives tab → Export backup, once a month.** That downloads a JSON file. Import reads it back, which is also how you move to a new phone.

## The reminder

The 17:09 daily nudge was a Claude scheduled task reading Claude's database. This version has no connection to that, so it stops being useful once you move.

Replace it with a repeating alarm on your phone at 17:09. It won't know what you've already logged, it just tells you to open the app.

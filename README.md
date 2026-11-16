# Marquee

**A film and TV diary for watching together.** Log what you watch, keep a watchlist, get recommendations from what you've loved, see where anything is streaming, and settle "what are we watching tonight?" with friends in about a minute.

**Live site:** https://YOUR-USERNAME.github.io/marquee/

![Marquee home page](screenshot.png)

## Features

- **Diary and ratings.** Log films and TV seasons with half-star ratings, likes, reviews, who you watched with, where, and the vibe of the night.
- **You may like.** "Because you liked…" recommendations built from your highest-rated and liked titles, for both films and TV.
- **Popular this week.** Trending films and shows, updated weekly.
- **Best of every decade.** The top-rated films of each decade from the 1930s to today, filtered by genre.
- **Where to watch.** Streaming, rental and purchase options for your country, powered by JustWatch data.
- **Tonight.** Merges your group's watchlists, keeps only what's streaming on your services and finishes in time, then runs an anonymous keep-or-veto round to land on one pick.
- **Friends without accounts.** Swap share links to compare ratings, see a Taste Clash of your biggest disagreements, and merge watchlists for Tonight.
- **Calibrated ratings.** Once someone has rated 8+ titles, their stars are shown on their own personal scale, so a harsh critic's 4★ reads as the rave it is.
- **Taste map.** A grid of the regions and decades you've watched, with one-click paths into your blind spots.
- **Watchlist, favorites, TV progress.** Four favorite films on your profile, a watchlist, and "Continue watching" for shows.
- **Letterboxd import.** Bring in your `diary.csv` or `ratings.csv` export.
- **Backups.** Download and restore all your data as a JSON file.

## How it works

Marquee is a single `index.html` file with no build step, no framework and no server.

- Film and TV data comes from the [TMDB API](https://developer.themoviedb.org/).
- Each person's diary, ratings, watchlist and friends are stored in their own browser (`localStorage`). Nothing is sent to a server except requests to TMDB for film information.
- Friend share links encode a display name, ratings, watchlist and recent logs in the URL. Opening one adds that person locally.

## Run it yourself

1. Get a free TMDB key: create an account at [themoviedb.org](https://www.themoviedb.org/signup), then go to **Settings › API** and request a developer key.
2. Open `index.html` and paste your key into the config block near the top of the script:

   ```js
   const CONFIG = {
     TMDB_KEY: 'paste-your-key-here',
     DEFAULT_REGION: 'US',
     SITE_NAME: 'Marquee'
   };
   ```

   Either the **API Key** or the **API Read Access Token** works.
3. Open `index.html` in a browser. That's it.

If you leave `TMDB_KEY` empty, the site shows a setup screen where a key can be entered and saved in that browser only.

## Deploy to GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings › Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, then **Save**.
4. After a minute or two the site is live at `https://YOUR-USERNAME.github.io/marquee/`.

> **About the API key:** because this is a static site, the key is visible to anyone who views the page source. TMDB keys are read-only, so the risk is limited to someone using up your request quota. If that happens, regenerate the key on TMDB. For a large launch, route requests through a small server so the key stays private.

## Roadmap

- Accounts and sync across devices (Supabase or similar)
- Clubs: small groups with a weekly pick and spoiler-locked discussion
- Episode-level TV logging
- Lists you can share and follow

## Credits

This product uses the TMDB API but is not endorsed or certified by TMDB. Film and TV data, posters and backdrops come from [The Movie Database (TMDB)](https://www.themoviedb.org/).

Where-to-watch data is provided by [JustWatch](https://www.justwatch.com/).

## License

Code is released under the [MIT License](LICENSE). Film and TV data and images belong to their respective owners and are provided through TMDB under its [terms of use](https://www.themoviedb.org/api-terms-of-use).

# CineVerse

A fast, simple movie database site built with Next.js. English only. Runs on demo data until you add a TMDB key.

## Run it

```bash
npm install
npm run dev                  # http://localhost:3000
npm run build && npm start   # production
```

Needs Node 18.18 or newer.

## Settings

Create a `.env.local` file (see `.env.example`):

| Variable | What it does |
|---|---|
| `NEXT_PUBLIC_SITE_URL` | Your domain. Used for canonical links, sitemap and structured data |
| `TMDB_API_KEY` | When set, real movie data replaces the demo data |
| `NEXT_PUBLIC_ADSENSE_CLIENT` / `NEXT_PUBLIC_ADSENSE_SLOT` | Add after AdSense approves the site |

## Deploy

Push to GitHub, import the repo in Vercel, add the variables above, connect your domain.
Then submit `https://yourdomain.com/sitemap.xml` in Google Search Console.

## Structure

- `lib/demo-data.js`: demo movies (add more here while testing)
- `lib/movies.js`: data layer, switches between demo data and TMDB
- `lib/format.js`: genre names, mood list, date and number formatting
- `app/`: pages (`/`, `/movie/[slug]`, `/browse`, `/mood`, `/upcoming`, `/compare`, `/watchlist`, `/search`)
- `components/AdSlot.js`: ad container. Space is reserved so the page does not shift. Shows a dashed box in development only, and nothing in production until AdSense keys are set
- `app/globals.css`: all styling, plain CSS with a few variables at the top

## Design notes

Flat dark neutral palette, one accent colour (amber, used for ratings and the main button), serif headings with a system sans body, no gradients, no emoji, no icon tiles. Posters are plain typographic blocks until TMDB is connected, then real posters load lazily.

## Performance

Pages are pre-built static HTML and refresh hourly. First Load JS is about 108 KB. Images are lazy-loaded with fixed dimensions.

## Before you earn from it

- The free TMDB API is for non-commercial use. Get a commercial licence before showing ads, and keep the attribution line in the footer.
- AdSense approval is hard for sites that only republish API data. Add original content such as reviews and lists.
- Ratings, votes and "where to watch" are sample data until TMDB is connected. The "where to watch" links currently open a search, swap in affiliate links when you have them (`app/movie/[slug]/page.js`).
# cineverse

# TripWise — The World, Unfolded

An editorial, responsive travel discovery and itinerary app for **AWS Student Builder Group — VIT Chennai, Frontend Track**.

## Features
- **Real external API:** Wikipedia MediaWiki API, fetched live using browser `fetch` and CORS (`origin=*`). Destination descriptions and images are enhanced from API responses; the initial destination catalog is a curated list with coordinates and categories.
- **Explore:** Responsive image-rich destination cards.
- **Search, filter, sort:** Search by place, country, region, or category; filter by category; sort by name or region.
- **Details:** Open a destination modal with a longer API description, category, region, and OpenStreetMap link.
- **My Trip:** Add, view, and remove saved destinations, with persistence via `localStorage`.
- **Reliability:** Loading skeletons, API error with retry, no-results state, empty itinerary, and graceful details fallback.
- **Mobile:** Responsive navigation, cards, details, and itinerary.

## Tech stack
React 18, Vite, CSS, Lucide React, Wikipedia MediaWiki API, browser localStorage. No API key or backend required.

## Run locally
```bash
npm install
npm run dev
```
Visit the local URL displayed by Vite.

## Production build
```bash
npm run build
npm run preview
```

## Deploy
Push this folder to a public GitHub repository and import it into Vercel or Netlify. Build command: `npm run build`; output directory: `dist`.

## API details
GET `https://en.wikipedia.org/w/api.php?action=query&prop=pageimages|extracts&piprop=thumbnail&pithumbsize=800&exintro=1&explaintext=1&exsentences=2&titles=Kyoto|Bali&format=json&origin=*`

Wikipedia data is used for informational descriptions and some images; fallback photography uses Unsplash. See Wikipedia/Wikimedia attribution and photo licensing terms before production publication. API availability and returned image metadata can vary. This application does not claim to have booked travel or fetched live weather.

## Submission checklist
- [ ] Push to a **public GitHub repository**.
- [ ] Deploy a live website and verify the link.
- [ ] Capture desktop and mobile screenshots of Explore, Details, My Trip, filtered search, populated itinerary, and empty itinerary.
- [ ] Put screenshots into a PDF named according to the recruitment instructions: `<register no>_<Track>`.
- [ ] Test live API connectivity and saved itinerary persistence.

## Design approach
Travel-editorial aesthetic: forest green, cream, terracotta accents, expressive serif headlines, large destination photography, generous spacing, restrained microinteractions.

## Live weather API (Open-Meteo)

When a destination is opened, TripWise requests current temperature, apparent temperature, humidity, wind speed and weather code from `https://api.open-meteo.com/v1/forecast` using that destination's coordinates. No API key is required. If the weather API is unavailable, the UI shows an unavailable message instead of invented data. Wikipedia supplies the destination information. Weather and Wikipedia requests need an internet connection.

## Travel Time Machine
Open **Time Machine** in the navigation or **Preview my trip** from My Trip.
Each saved destination becomes one day, in collection order. Choose a departure
date, play/pause the story, move between days, or click a scene thumbnail.
Playback duration is adjustable; replay starts again at the final scene.
Edit the morning, afternoon and evening activities and each day's USD allowance.
Edits and departure date persist in localStorage separately from your itinerary.
The default $100/day is an illustrative allowance, not a researched price.
Totals exclude flights and transfers. Activities are suggestions, not reservations.
Open-Meteo supplies daily highs/lows and conditions for matching dates in its
16-day forecast window. Loading, unavailable, retry and out-of-range states are
shown explicitly. External API connectivity and photography require internet.
Reduced-motion preferences disable scene movement. Mobile layouts stack the
planning panels and allow horizontal scrolling through scenes.

### Validation of this update
- Production build: `npm ci` and `npm run build` passed.
- Browser checks could not run in the build environment (browser unavailable).
- Before submission, verify desktop/mobile playback, automatic final-scene stop,
  edited activity/budget persistence, empty itinerary, and live forecast responses.

This update uses the complete TripWise Parallel Universe source archive because
the four newly supplied files do not include the referenced src folder. Explore,
search/filter/sort, destination details, weather, My Trip and Parallel Universe
remain included.

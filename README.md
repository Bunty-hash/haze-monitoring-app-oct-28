# Haze Watch

A single-page haze and weather monitor.

- **Singapore tab:** NEA 24-hour PSI by region (north, south, east, west, central) on a map of Singapore's 28 postal districts, with PM2.5, PM10 and main pollutant, plus Open-Meteo weather and a four-day outlook.
- **ASEAN cities tab:** Open-Meteo weather for 12 cities (the 11 ASEAN capitals and Pekanbaru).

## Data

| What | Source | Coverage |
| --- | --- | --- |
| PSI, PM2.5, PM10 | National Environment Agency via [data.gov.sg](https://data.gov.sg) real-time PSI API | Singapore only |
| Weather | [Open-Meteo](https://open-meteo.com) forecast API | All cities |

The values in `index.html` are a **snapshot taken 28 Oct 2026, 10:15 SGT**. The page does not refresh itself. Postal-district shapes are an approximate drawing, each shaded by the NEA region it falls in.

## Deploy on Vercel

It is a static site with no build step.

1. Import this repository in Vercel.
2. Framework preset: **Other**. Leave build command and output directory empty.
3. Deploy. `vercel.json` only adds clean URLs and a few security headers.

To preview locally, open `index.html` in a browser.

## Making the data live

Browsers can call both APIs directly. To refresh on load, fetch these and replace the embedded `NEA` and `CITIES` objects in the script:

- `https://api-open.data.gov.sg/v2/real-time/api/psi`
- `https://api.open-meteo.com/v1/forecast` with `current` and `daily` parameters (see the `CITIES` structure for the fields used)

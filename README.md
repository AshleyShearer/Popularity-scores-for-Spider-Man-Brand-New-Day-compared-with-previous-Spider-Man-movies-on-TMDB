# Popularity-scores-for-Spider-Man-Brand-New-Day-compared-with-previous-Spider-Man-movies-on-TMDB
I’ll compare TMDB daily popularity scores for Spider-Man: Brand New Day against No Way Home and Far From Home over about 30 days in 2026, using TMDB’s public Daily ID Exports, requests, and pandas. I’ll chart the results with line and bar graphs to see how the newest film compares online.

# Spider-Man Popularity on TMDB: Brand New Day vs. No Way Home and Far From Home

Author: Ashley Shearer

## Summary

I compare TMDB daily popularity scores for Spider-Man: Brand New Day against No Way Home
and Far From Home over about 30 days in 2026, using TMDB's public Daily ID Exports, requests,
and pandas. I'll chart the results with line and bar graphs to see how the newest film
compares online.

## Data
**Source:** TMDB Daily ID Exports
(https://developer.themoviedb.org/docs/daily-id-exports), files named
`movie_ids_MM_DD_YYYY.json.gz`. This project uses TMDB data but is not
endorsed or certified by TMDB.
[If using Wikipedia: Wikimedia pageviews API, en.wikipedia, "user" traffic.]

**Collected:** November 15, 2026, covering exports from
October 16 to November 14, 2026. Requests used a User-Agent that identifies
me and a 3-second pause between downloads.

**Records:** 30 daily exports downloaded (none missing). After filtering to
the three movies by TMDB ID: 90 rows (30 per movie).

**In the repo:** `data/sample_clean.csv` (first 15 rows of the cleaned data)
and `data/DATA_DICTIONARY.md` (every field and what it means).

**Left out of the repo:** The raw `.json.gz` files (`data/raw/`). Each file
lists over a million movies, way more than used in this project. TMDB's
terms limit redistribution of its data. The full cleaned CSV is also left
out, the sample shows its structure. All files can be re-created by running
the notebook. No personal information was collected.

## Methods
Each daily export was downloaded with `requests`, saved locally, and
streamed line by line to keep only the three movies' TMDB IDs. The rows
were combined into one table (date, ID, title, popularity), checked for
missing values and duplicates, and compared using pandas and matplotlib.
A log scale is used in the line graph because Brand New Day's scores are
far higher than the other two.

## Findings


## How to reproduce

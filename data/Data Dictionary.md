# Data Dictionary

Cleaned dataset: one row per movie per day (`sample_clean.csv` shows the first 15 rows).

| Field | Type | Meaning |
|---|---|---|
| `date` | date (YYYY-MM-DD) | Day of the TMDB daily export the score came from |
| `tmdb_id` | integer | TMDB's unique ID for the movie |
| `title` | string | Original title as listed by TMDB |
| `popularity` | float | TMDB's popularity score on that day (TMDB does not publish the exact formula) |
| `movie` | string | Short label I assigned: Brand New Day, No Way Home, or Far From Home |
| `wiki_views` | integer | Daily English Wikipedia pageviews (human traffic) for the movie's article. Only in `sample_merged.csv`. |

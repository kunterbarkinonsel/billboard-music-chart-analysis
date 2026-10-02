# Rolling Beats Magazine: Music Chart Analysis (2000–2024)

What makes a song rise on the Billboard chart, and what makes it stay there? A data story built in Python on 25 years of Billboard chart data combined with Spotify audio features.

## The brief

Rolling Beats Magazine is producing a "25 Years of Pop" retrospective and wants data-driven stories about how popular music has evolved since 2000. I took the role of data journalist and looked for patterns behind chart success.

## Questions

1. Do audio characteristics (danceability, energy, tempo and others) relate to chart position?
2. Do explicit songs perform differently from clean songs?
3. Does the month of release affect how long a song stays on the chart?
4. Do studio-polished songs chart better than live-sounding or instrumental ones?

## Data

| Table | Rows | Content |
|---|---|---|
| `chart_positions` | 129,305 | Weekly Billboard chart positions, 2000–2024 |
| `tracks` | 11,070 | Release date, duration, album type, explicit flag |
| `audio_features` | 10,783 | Spotify audio features per track |

After merging and cleaning, the analysis covers 10,652 songs. The data was provided by Hyper Island through Google BigQuery and is not included in this repository. The notebook is saved with all outputs and charts, so it can be read without running it.

## Key findings

- **Audio features do not predict chart position.** All six features tested have a correlation with peak position between -0.07 and +0.03.
- **Clean songs stay on the chart about 40% longer** than explicit songs (13.8 vs. 9.8 weeks on average) and peak slightly higher (position 46.9 vs. 49.8).
- **January, September and November releases last longest.** July and August releases have the shortest chart lives, so the "summer hit" is not supported by the data.
- **Production style makes almost no difference.** Studio-polished and live-sounding songs peak within one or two positions of each other.

The sound of a song explains very little of its chart success. Factors outside the dataset, such as promotion, radio play and artist popularity, are likely to matter more.

## Approach

1. Load the tables from BigQuery into pandas.
2. Aggregate weekly chart rows to one row per song: peak position and weeks on chart.
3. Merge with track metadata and audio features, and extract release year and month.
4. Compare groups and compute correlations, with a Matplotlib chart for each question.

## Tools

Python, pandas, Matplotlib, Google BigQuery, Jupyter Notebook

## Files

| File | What it is |
|---|---|
| `rolling_beats_music_chart_analysis.ipynb` | Full analysis with code, charts and written interpretation |

## Next steps

- Add artist popularity and collaborations to see how much they explain chart success
- Track how the share of explicit songs has changed year by year
- Check release dates where only the year is known, which may inflate the January result

---

Built as the individual assessment for the *Python Programming* course in the Data Analyst Programme at Hyper Island.

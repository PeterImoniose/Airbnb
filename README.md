# Airbnb Rio de Janeiro: Pricing Dynamics, Host Characteristics, and Amenity Impacts

An exploratory data analysis of Airbnb listings in Rio de Janeiro (real data from Inside
Airbnb), examining what drives listing prices, how host professionalism relates to guest
satisfaction, and how amenities affect price across property and room types.

## What's in this repo

- [`Airbnb_data.ipynb`](Airbnb_data.ipynb) - the full analysis: data cleaning and feature
  engineering, exploratory analysis, three research questions, and a conclusion with
  findings, limitations, and recommendations for further work.
- [`Inside Airbnb Data Dictionary.pdf`](Inside%20Airbnb%20Data%20Dictionary.pdf) - the
  source data dictionary describing every column in the raw listings/reviews files.

## Research questions

1. Which property, room, and neighbourhood characteristics most strongly determine
   Airbnb listing prices in Rio de Janeiro?
2. How does host professionalism influence guest satisfaction ratings?
3. How do amenities contribute to price variation, and does their impact differ across
   room types?

## Key findings

- Property and room characteristics (accommodates, bedrooms, bathrooms, room type) are
  the strongest predictors of price; premium neighbourhoods (Leblon, Ipanema, Barra da
  Tijuca) command considerably higher median prices on top of that.
- Guest satisfaction is generally high and stable citywide (concentrated around 4.5-5).
  Host attributes (response rate, acceptance rate, experience) show a weak but positive
  association with ratings - professionalism supports satisfaction without strongly
  differentiating listings.
- Superhosts consistently score slightly higher than non-superhosts.
- City-wide correlations mask real local patterns: relationships between price and
  structural features are noticeably stronger within a single neighbourhood (e.g.
  Copacabana) or a single room type than across the full dataset - global models
  understate what's actually happening locally.

Full detail, all charts, and the limitations/recommendations sections are in the
notebook.

## A note on the reviews dataset

The listings dataset already includes aggregate guest-review statistics per listing
(`review_scores_rating`, `reviews_per_month`, etc.), which is what this analysis uses.
The separate reviews dataset (individual review text, reviewer IDs, and dates) is loaded
and inspected in the notebook but not merged into the analytical dataset - the listings
file's own aggregates were sufficient for the research questions above.

## Data

Neither CSV is included in this repository (the reviews file alone is over 300MB, well
past what's practical to version-control). Source: Inside Airbnb, Rio de Janeiro. Place
`airbnb_listings(1).csv` and `airbnb_reviews(1).csv` in this folder, or update `DATA_DIR`
in the second code cell to point at wherever you keep them.

## Running it

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook Airbnb_data.ipynb
```

Originally developed in Google Colab with Google Drive mounted; it also runs locally out
of the box - the data-loading cell falls back to a local path automatically outside Colab.

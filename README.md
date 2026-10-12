# MoveInSync Review Insights

**A small review-analysis project for the Forward Deployed Engineer case study.**

I looked at recent public reviews of MoveInSync on Google Play and grouped the issues by where they happen in the employee commute. The goal here is not to claim that four reviews explain the entire rating. It is to show how I would turn user feedback into a short list of things to investigate, then repeat the analysis as new reviews appear.

## What stood out

The four examples in `data/reviews.csv` point to three areas worth validating:

1. **Ride information:** GPS location and ETA can be unreliable, and notifications may arrive late.
2. **Booking confidence:** the booking flow can leave a user unsure whether a ride was actually booked.
3. **No-show handling:** booking records, vehicle arrival and check-in may not always feel consistent to the user.

These are reports from users, not verified root causes. I would check them against internal booking, GPS, notification and support data before deciding how widespread they are.

## What I would do first

- Make the booking confirmation explicit, including date, shift, pickup point and current status.
- Track GPS freshness, ETA error and notification delivery. If location data is old, show that clearly.
- Review how no-show status is triggered and pilot a pickup reminder without relying on uncertain GPS as the only signal.

## Run the analysis

Python 3.10+ recommended.

```bash
pip install -r requirements.txt
python src/analyze_reviews.py
```

The script creates:
- `outputs/theme_counts.png`
- `outputs/analysis_summary.md`

The chart describes only the small seed set in this repository. It is not a percentage estimate for all users.

## How I would keep it useful each week

1. Add recent reviews with date, star rating, app version (if visible) and source URL.
2. Ask an LLM to suggest a theme and journey stage, while requiring it to point to the text supporting the label.
3. Manually check a sample and every high-severity item.
4. Compare this week's themes with last week's and with product/operations metrics.
5. Pick the top three issues, name an owner and track the relevant metric after a fix.

A reusable prompt is in `prompts/review_classification_prompt.md`.

## Data and limitations

- Source: [MoveInSync on Google Play](https://play.google.com/store/apps/details?id=com.moveinsync.ets)
- The CSV contains four public review examples dated June–July 2026. The summaries are paraphrased; they are not presented as full verbatim reviews.
- Star ratings are blank because I could not reliably verify the individual rating values from the captured review text. I have not guessed them.
- This is a small, non-random sample. Public reviews are self-selected and may reflect app, transport-operation, employer-policy or device/network issues.
- No internal MoveInSync data was available, and no full review scrape was performed.

The next step would be to collect a defined larger sample and validate the signals against booking success, GPS freshness, ETA error, push delivery, disputed no-shows and support tickets.

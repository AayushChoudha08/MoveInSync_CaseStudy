# Method and limitations

## Question
What user problems appear in public MoveInSync reviews, and how could I turn review reading into a repeatable process?

## Source and sample
- Official Google Play listing: https://play.google.com/store/apps/details?id=com.moveinsync.ets
- Access date: 12 October 2026.
- Four visible review examples dated 11 June, 18 June, 29 June and 7 July 2026.
- Each CSV entry is a paraphrase of a visible review.
- Individual star ratings are blank because they were not reliably captured in the source extract; do not infer them from sentiment.

## Labels
The labels were assigned manually from the content: tracking/ETA/notifications, booking-date/no-show, check-in reminder, and booking-flow clarity.

## What this can and cannot tell us
It can identify specific problems worth investigating. It cannot tell us how common those problems are across all users, establish root cause, or prove that a change will improve the overall rating.

## Validation I would do next
1. Expand to a defined recent review sample and record rating/date/app version accurately.
2. Deduplicate and keep source links.
3. Have an LLM suggest themes, then manually review a subset.
4. Compare themes with internal booking, GPS, ETA, notification, no-show and support metrics.
5. Pilot one fix and measure before/after, with a holdout where practical.

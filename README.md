# Budventure

An English, responsive MVP for international students planning and managing life abroad. Independent of QualiFi.

## Run and test

Serve `dist/` with any static server, for example:

```sh
python3 -m http.server 8080 --directory dist
node --test tests/student-journey.test.cjs
```

No package installation, API keys or paid services required.

## Student journey

1. Create a personal profile with name, destination, start date, duration, housing and lifestyle. An underfunded plan is flagged immediately and can only be saved as a clearly labelled draft.
2. See monthly cost estimates, funding gap, remaining budget and safe daily flexible allowance. Add everyday expenses by category.
3. Request food, coffee or an activity; local rule-based guidance takes the current allowance into account.
4. Filter fictional listings by category and price. A zero allowance offers free activities instead of pretending paid options fit.
5. Record a visit, rating, actual price, date and optional receipt. Saving creates exactly one linked expense and returns to My profile.
6. My profile holds past experiences, locally saved receipt photos, spending history and an updated forecast. Reloading preserves the profile on this browser.

## Budget and prediction model

`dist/model.js` contains pure calculations, separately tested from UI scenario handlers.

- City baseline × lifestyle/housing factors, plus a 10% emergency reserve.
- Real calendar start/end dates determine remaining days; month-end dates are clamped.
- Safe allowance = max(0, unspent budget − unpaid housing/transport reserves − emergency reserve) / remaining days.
- Paying housing or transport releases its matching reserve so those payments are not counted twice.
- Before there is sufficient history, projected total uses the selected lifestyle's flexible spending estimate.
- Once there are entries on at least 3 completed days, projection uses flexible spending per calendar day over the latest 14 completed days (or elapsed days when fewer). Zero-spending days are included; this requires complete expense logging.
- Today's logged flexible spending is included once. A used-up budget produces zero suggested allowance.
- Actual spending may exceed the budget; it is recorded honestly rather than rejected.
- Receipts and reviews are saved together; duplicate submission does not create another expense.

## Data and scope

All businesses, prices and ratings are fictional fixtures. City estimates are illustrative, not live market data. Amounts are EUR. Flights, visas and deposits are excluded.

Profiles, reviews, expenses and resized receipt photos use localStorage only. There is no server account, server upload, community sharing, real booking/payment, cloud sync, LLM or live currency provider. Receipt storage failure preserves the form and rolls back the linked records. Clear browser data to remove the local profile. Only one trip is supported; destination/dates are locked once spending exists to preserve ledger consistency. Historic v1 settings migrate to English labels; original user-authored reviews are preserved.

## Validation

See `tests/student-journey.test.cjs` and `TESTING.md`. Browser visual QA remains unverified because the managed environment does not expose the supported browser runtime. Responsive CSS is included; scenario tests exercise logic and handlers, not a real rendered browser.

## Deployment

Static Sites configuration is in `.openai/hosting.json`. The dedicated source repository is https://github.com/Talhaguler1/Budventure.

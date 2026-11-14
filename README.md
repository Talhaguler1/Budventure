# Budventure

Responsive Turkish student travel budgeting MVP. A standalone project, independent of QualiFi.

## Run
Serve `dist/` with any static web server, e.g. `python3 -m http.server 8080 --directory dist`.
No dependencies, build step, API keys, or paid services required.

## Customer journey
1. Destination, duration, total EUR budget, housing, four lifestyle profiles.
2. Personalized monthly breakdown, funding shortfall, daily flexible allowance, expense tracking.
3. Activity request and deterministic category-based recommendations.
4. Filter demo local businesses by category/price and select one.
5. Rate, review, preview a receipt photo, optionally record the expense.

## MVP boundaries
Prices, businesses and ratings are illustrative fixtures, not verified live data. Chat responses are local rules, not an LLM. Data persists in localStorage on the current browser. Receipt images stay in session memory for preview only; no server upload or OCR. No login, payments, real ads, public reviews, live FX, or offline service worker. All amounts use EUR. Flight/visa/deposit costs are excluded from the living-cost estimate.

## Budget model
City baseline × profile factors, housing multiplier, 10% contingency. Daily flexible allowance deducts housing, transit, contingency and recorded spending from total budget, divided by total planned days. This demo does not infer elapsed trip days.

## Next steps
Verified price data and timestamps, authenticated user storage, consent-based receipt storage with redaction, review moderation, real travel dates and FX provider, backend recommendation service.

## Deployment
`.openai/hosting.json` declares static Sites hosting. Source is also maintained in the dedicated Budventure GitHub repository.

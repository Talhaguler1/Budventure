# Student journey review

## Persona

Alex Morgan is a fictional exchange student spending four months in Milan, staying in a shared apartment and choosing Student Lifestyle. Alex has €5,500, wants a local lunch, pays €12 and rates the visit four stars.

The persona is exercised with deterministic Node scenario tests against the application handlers and budget model. This is a scripted student simulation, not a claim that a separate autonomous agent operated a browser.

## Problems found and corrected

| Student action | Earlier issue | Updated behavior |
| --- | --- | --- |
| Enter €100 for a four-month stay | Reassuring introduction despite unaffordable costs | Immediate shortfall warning, lowest-cost benchmark, explicit draft wording |
| Save a restaurant experience | No personal home for past visits | My profile automatically shows the review, actual price, date and receipt |
| Record a visit | Expense entry was optional and disconnected | One linked expense always updates the budget; duplicate submission does not add it again |
| Return during the trip | Allowance always used total planned days | Actual calendar dates determine days remaining |
| Pay rent | Paid housing could be deducted twice | Corresponding unpaid reserve decreases with the housing payment |
| Build spending history | No estimate based on behavior | Three completed logging days enable a recent-spending forecast |
| Spend today | Forecast could count today twice | Today's spending is deducted from the remaining daily forecast |
| Change a star rating | Re-render discarded typed review | Rating updates without replacing the form |
| Seek food with no flexible budget | “Affordable” suggestions could still cost money | Empty state leads to free activities; paid options are clearly labelled |
| Attach a receipt and return later | Receipt was preview-only | Resized image is saved locally with the experience |
| Save when storage is full | Possible unsaved or mismatched records | Clear error, transaction rollback, draft retained |
| Enter a future visit | Spending could be invented for future dates | Visits must be within the trip and no later than today |

## Research and verification boundary

Reviewed https://github.com/browser-use/browser-use, an open-source browser agent framework. It was not installed or integrated: the supported managed browser runtime is unavailable here, and an additional paid/API-based agent is unnecessary for these deterministic budget checks. No credentials were sent to a third-party agent.

The tests verify profile creation, persistence/reload, history, linked expense records, budget and prediction arithmetic, month ends, overspending, migration, and zero-budget alternatives. They do not verify actual browser layout, image decoding or mobile touch interactions. Those remain visual QA work.

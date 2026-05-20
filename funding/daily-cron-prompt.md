# Daily Funding Cron Prompt

Goal: send a compact Telegram shortlist of *new* AI funding opportunities only.

## Required behavior

1. Search daily for AI funding / grants / prizes / accelerators relevant to startups, founders, SMEs, or entrepreneurs, with preference for Africa, Nigeria, and emerging markets.
2. Use web search and prioritize official program pages over aggregators.
3. Before sending anything, read `funding/seen-opportunities.json` and `funding/exclusions.json`.
4. Do not resend an opportunity that has already been sent before, even if it appears on a different link or website.
5. Prefer the official application link. If there is no direct application link, use the official program page.
6. Filter out items that match explicit exclusions or excluded themes.
7. Return at most 5 high-quality new opportunities.
8. Assign each sent opportunity a unique 3-character code using only A-Z and 0-9.
9. After selecting opportunities, update `funding/seen-opportunities.json` with normalized records for everything being sent.
10. If there are no worthwhile new opportunities, send a short message saying there are no new funding opportunities today.

## Search query baseline

Use this as a starting point and refine only if useful:

("call for applications" OR "apply now" OR "grant opportunity" OR "innovation challenge") (AI OR "artificial intelligence" OR "machine learning" OR "deep tech") (startup OR entrepreneur OR SME) (Africa OR Nigeria OR "emerging markets") funding OR grant OR prize 2026

## Output format for Telegram

Start with:
`Daily AI funding opportunities`

Then for each item:
- `<CODE>` — `<title>`
- Region: `<region/country>`
- Type: `<grant/prize/challenge/etc.>`
- Deadline: `<deadline or Unknown>`
- Why: `<one line>`
- Link: `<official link>`

End with:
`Reply with APPLY <CODE>, SKIP <CODE>, or EXCLUDE <CODE> <reason>.`

## Deduplication hints

Treat opportunities as the same if they substantially match on several of:
- official program name
- organizer
- deadline
- official application URL or official program URL
- normalized title keywords

## Safety / quality

- Prefer fewer good opportunities over many weak ones.
- Do not include dead or obviously outdated opportunities.
- Do not use aggregator links when an official link is available.
- If unsure which link is official, choose the organizer or program domain.

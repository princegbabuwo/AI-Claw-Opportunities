# Daily Funding Cron Prompt

Goal: send a compact Telegram shortlist of *new* AI funding opportunities only.

## Required behavior

1. Use RSS-driven discovery as the primary search method.
2. Read and use the query set in `/home/node/.openclaw/workspace/funding/rss-keywords.md`.
3. For **each keyword/query**, fetch the corresponding Google News RSS feed with `exec` + `curl`.
4. Before sending anything, read:
   - `/home/node/.openclaw/workspace/funding/seen-opportunities.json`
   - `/home/node/.openclaw/workspace/funding/exclusions.json`
   - `/home/node/.openclaw/workspace/funding/search-notes.md`
   - `/home/node/.openclaw/workspace/funding/rss-keywords.md`
5. Extract candidate opportunities from the RSS results, but do **not** trust headline pages alone.
6. Follow through thoroughly using `web_fetch` or `exec` + `curl`:
   - open the official-looking source page
   - if that page links onward to application details, follow those links too
   - continue until you reach the best official application page or official program page
7. Prefer links in this order:
   - official application form
   - official program page
   - official announcement page
   - trusted secondary source only if no official page exists
8. Do not resend an opportunity that has already been sent before, even if it appears under a different title or source.
9. Filter out items that match explicit exclusions or excluded themes.
10. Return at most 5 high-quality new opportunities.
11. Assign each sent opportunity a unique 3-character code using only A-Z and 0-9.
12. After selecting opportunities, update `seen-opportunities.json` with normalized records for everything being sent.
13. If there are no worthwhile new opportunities, send a short message saying there are no worthwhile new AI funding opportunities today.
14. If the run hits any blocker or failure condition, do **not** crash silently. Send a concise Telegram-friendly failure update describing the problem.

## Search execution rules

- Use the saved query list as the baseline and actually run all of them.
- Prefer feeds and official source pages over generic search-engine result pages.
- When RSS items point to article/aggregator coverage, use that only as a lead and keep following through to the official source.
- If one official page contains multiple opportunities, inspect them and include only those that fit the AI/tech + African startup brief.
- Prefer fewer strong opportunities over many weak ones.
- Do not include dead, outdated, already-closed, or vague opportunities.

## Output format for Telegram

If successful and you found items, start with:
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

If no worthwhile new items exist, send only a short note.

If blocked or failing, send:
- a short status line
- the specific blocker/error
- if possible, one next-step suggestion

## Deduplication hints

Treat opportunities as the same if they substantially match on several of:
- official program name
- organizer
- deadline
- official application URL or official program URL
- normalized title keywords

## Quality bar

Only send an opportunity if it is all of the following:
- relevant to AI / tech startups, founders, entrepreneurs, or SMEs
- meaningfully relevant to African startups, or open to them in practice
- still open or plausibly current
- supported by an official source page

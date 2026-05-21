# Funding Run Logging Spec

Each funding cron run must leave a detailed audit trail in the workspace so the search can be debugged later.

## File layout

- Create directory: `/home/node/.openclaw/workspace/funding/logs/` if missing.
- For each run, write a new JSON file:
  - `/home/node/.openclaw/workspace/funding/logs/YYYY-MM-DDTHH-MM-SSZ.json`
- Also write/update a latest pointer copy:
  - `/home/node/.openclaw/workspace/funding/logs/latest.json`

## Minimum fields

```json
{
  "runStartedAt": "ISO-8601",
  "runFinishedAt": "ISO-8601",
  "status": "ok|no_results|error",
  "searchesPlanned": 0,
  "searchesCompleted": 0,
  "queries": [
    {
      "index": 1,
      "query": "string",
      "rssUrl": "string",
      "fetchStatus": "ok|error",
      "itemsFound": 0,
      "notes": "string"
    }
  ],
  "rawCandidatesCount": 0,
  "uniqueCandidatesCount": 0,
  "candidates": [
    {
      "title": "string",
      "leadSource": "string",
      "sourceQuery": "string",
      "leadUrl": "string",
      "officialUrl": "string or null",
      "region": "string or null",
      "type": "string or null",
      "deadline": "string or null",
      "decision": "approved|rejected|duplicate|excluded|unclear",
      "reason": "short human-readable reason",
      "evidence": ["short notes"],
      "duplicateOf": "code or title if relevant"
    }
  ],
  "selectedCount": 0,
  "selectedCodes": ["ABC"],
  "selectedTitles": ["Opportunity title"],
  "rejectionSummary": {
    "duplicate": 0,
    "closed": 0,
    "weak_fit": 0,
    "non_africa": 0,
    "women_only": 0,
    "missing_official_source": 0,
    "unclear_or_stale": 0,
    "other": 0
  },
  "finalMessagePreview": "string"
}
```

## Logging rules

1. Run **all saved queries** from `rss-keywords.md` and log each one.
2. Count how many feed items each query returned.
3. Log every candidate that was seriously considered, not just the winners.
4. For every approval or rejection, store a brief reason.
5. If a candidate is rejected because of policy/fit, say exactly why.
6. If fewer than 3 opportunities are selected, explain why in the log.
7. If the run errors, still write the partial log with the blocker.
8. The Telegram message should stay compact, but the workspace log should be exhaustive enough to debug the run later.

# Funding Workflow

This folder tracks the AI funding opportunity workflow.

## Files

- `applicant-profile.md` — blank profile/questions the agent can use when applying
- `seen-opportunities.json` — canonical ledger of opportunities already sent
- `exclusions.json` — opportunities or themes to avoid in future
- `application-queue.json` — opportunities approved for application
- `search-notes.md` — operating rules for the daily search + messaging flow
- `rss-keywords.md` — saved Google News RSS keyword/query set for daily opportunity discovery
- `run-logging.md` — schema/rules for detailed per-run audit logs
- `logs/` — per-run funding search audit logs (`latest.json` + timestamped run files)

## Intended Flow

1. Daily search finds candidate opportunities.
2. Agent normalizes and deduplicates them before sending.
3. Each sent item gets a 3-character reply code.
4. You reply with codes like:
   - `APPLY A7Q`
   - `SKIP B2M`
   - `EXCLUDE C9Z climate-only grants`
5. Approved items are processed one at a time.
6. If application info is missing or uncertain, the agent messages you with exact questions.

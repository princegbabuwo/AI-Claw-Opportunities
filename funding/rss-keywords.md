# RSS Search Keywords

Use these Google News RSS search queries as the primary daily discovery layer for African AI/tech funding opportunities.

## Query Set

1. `("artificial intelligence" OR AI OR "machine learning") (grant OR funding OR fund OR accelerator OR incubator OR challenge OR prize OR "open call") (startup OR founder OR entrepreneur OR SME) (Africa OR African OR Nigeria OR Kenyan OR Ghana OR Egypt OR Rwanda) 2026`
2. `("call for applications" OR "apply now" OR "open call") (AI OR "artificial intelligence" OR "machine learning" OR tech) (startup OR entrepreneur OR SME) (Africa OR Nigeria OR "emerging markets") (grant OR accelerator OR challenge OR prize) 2026`
3. `("AI startup" OR "tech startup") (Africa OR Nigeria) (grant OR funding OR accelerator OR incubator OR challenge) official 2026`
4. `("deep tech" OR AI OR "artificial intelligence") (Africa OR African) (grant OR fund OR accelerator) startup official 2026`
5. `(Nigeria OR Kenya OR Ghana OR South Africa OR Egypt OR Rwanda) (AI OR tech) (grant OR accelerator OR challenge OR funding) startup official 2026`
6. `site:org OR site:gov OR site:com (AI OR "artificial intelligence") (Africa OR Nigeria) (grant OR funding OR accelerator OR challenge) startup 2026`

## Feed Construction Rule

For each query, URL-encode it and request the Google News RSS endpoint directly:

`https://news.google.com/rss/search?q=<URL_ENCODED_QUERY>&hl=en-US&gl=US&ceid=US:en`

You may also use the equivalent Google News search URL form when exploring manually:

`https://news.google.com/search?q=<URL_ENCODED_QUERY>&hl=en-US&gl=US&ceid=US:en`

## Selection Standard

Candidates are worth deeper verification only if they appear to be:
- currently open or recently announced
- relevant to AI / tech startups or founders
- plausibly usable by African startups or founders
- backed by an official or clearly attributable program page

## Exclude Early

Usually discard items that are:
- winner announcements rather than open applications
- generic VC/fund news with no application path
- old cohort announcements that are already closed
- secondary articles with no path to an official source

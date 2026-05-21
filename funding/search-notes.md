# Search + Messaging Rules

## Deduplication
Before sending an opportunity to the user, compare it against `seen-opportunities.json` using:
- official program name
- organizer name
- deadline
- official application URL
- normalized title keywords

Do not resend an opportunity already sent before, even if found on a different website.

## Link quality
Prefer links in this order:
1. official application form
2. official program page
3. official announcement page
4. trusted secondary source only if no official page is available

## Reply codes
Every opportunity sent to the user should have a unique 3-character code using only A-Z and 0-9.

## Suggested reply syntax
- `APPLY <CODE>`
- `SKIP <CODE>`
- `EXCLUDE <CODE> <reason/theme>`
- `INFO <CODE> <notes>`

## Application handling
When the user approves an opportunity:
1. confirm the official URL
2. add it to `application-queue.json`
3. process one opportunity at a time
4. if any answer is missing or uncertain, ask the user exact follow-up questions before submitting

## Standing eligibility rule
- Do not apply for women-only opportunities for Motherland AI.
- Treat programs limited to women founders, female-led startups, or equivalent women-only eligibility as ineligible unless the user says otherwise.
- Motherland AI founders are not women.

## Documentation maintenance
- When the user provides new eligibility, exclusion, or preference information relevant to funding, update the funding files/documentation in this folder as part of the workflow, not just the chat response.
- Keep debug coverage broad and inspectable: funding runs should log searches performed, result counts, candidate approvals/rejections, and reasons in workspace log files.

## WhatsApp delivery
Daily shortlist and follow-up questions should be sent to the user's WhatsApp once that channel is linked in OpenClaw.

# USER.md - About Your Human

_Learn about the person you're helping. Update this as you go._

- **Name:**
- **What to call them:**
- **Pronouns:** _(optional)_
- **Timezone:**
- **Notes:**

## Context

- OpenClaw environment runs in Docker.
- User's home path is `/home/prince`, not `/home/node`.
- For browser automation / Playwright setup, prefer the Docker-safe install path:
  `docker compose run --rm --entrypoint node openclaw-cli /app/node_modules/playwright-core/cli.js install chromium`
- Keep Playwright browser cache under a persisted path, and avoid assuming `/home/node`; prefer the user's actual host path conventions where relevant.

_(What do they care about? What projects are they working on? What annoys them? What makes them laugh? Build this over time.)_

---

The more you know, the better you can help. But remember — you're learning about a person, not building a dossier. Respect the difference.

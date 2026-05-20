# USER.md - About Your Human

_Learn about the person you're helping. Update this as you go._

- **Name:**
- **What to call them:**
- **Pronouns:** _(optional)_
- **Timezone:**
- **Notes:**

## Context

- OpenClaw environment runs in Docker.
- For browser automation / Playwright setup, prefer the Docker-safe install path:
  `docker compose run --rm openclaw-cli node /app/node_modules/playwright-core/cli.js install chromium`
- Keep Playwright browser cache under a persisted `/home/node` path via `PLAYWRIGHT_BROWSERS_PATH` and a persisted home volume.

_(What do they care about? What projects are they working on? What annoys them? What makes them laugh? Build this over time.)_

---

The more you know, the better you can help. But remember — you're learning about a person, not building a dossier. Respect the difference.

<wizard-report>
# PostHog post-wizard report

The wizard has completed a deep integration of PostHog analytics into the DevEvent Next.js App Router project. The following changes were made:

- **`instrumentation-client.ts`** — Client-side PostHog initialization using `posthog-js` with the `/ingest` reverse proxy, error tracking (`capture_exceptions: true`), and debug mode in development. Updated `defaults` to `2026-01-30`.
- **`next.config.ts`** — Reverse proxy rewrites routing `/ingest/*` to PostHog's US ingestion endpoint, plus `skipTrailingSlashRedirect: true`.
- **`lib/posthog-server.ts`** — Server-side PostHog client singleton using `posthog-node`, ready for API routes and Server Actions.
- **`components/EventCard.tsx`** — `posthog.capture('event_card_clicked', { title, slug, location, date })` fires on every event card click, capturing rich metadata.
- **`components/ExploreBtn.tsx`** — `posthog.capture('explore_events_clicked')` fires when the homepage CTA button is clicked.
- **`.env.local`** — `NEXT_PUBLIC_POSTHOG_KEY` and `NEXT_PUBLIC_POSTHOG_HOST` set to the correct project values.

| Event | Description | File |
|---|---|---|
| `explore_events_clicked` | User clicks the "Explore Events" CTA on the homepage | `components/ExploreBtn.tsx` |
| `event_card_clicked` | User clicks an event card; captures title, slug, location, and date | `components/EventCard.tsx` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

- [Analytics basics dashboard](/dashboard/1608723)
- [Event Card Clicks Over Time](/insights/Itd51HV0)
- [Explore Button Clicks (30 days)](/insights/KibrKoO3)
- [Top Clicked Events by Slug](/insights/vemXViRx)
- [Daily Unique Users Engaging](/insights/2NRLjKh1)
- [Explore → Event Click Engagement](/insights/CWzgxWx4)

### Agent skill

We've left an agent skill folder in your project. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.

</wizard-report>

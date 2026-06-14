# Cal.com

Open-source scheduling infrastructure with a public REST API for managing calendars, event types, bookings, teams, and availability. Available as Cal.com Cloud or self-hostable via the open-source repository.

- **Website:** https://cal.com
- **API Docs:** https://cal.com/docs/api-reference/v2/introduction
- **GitHub:** https://github.com/calcom
- **LinkedIn:** https://www.linkedin.com/company/cal-com
- **Pricing:** https://cal.com/pricing

## API

Cal.com provides a REST API v2 with a base URL of `https://api.cal.com/v2`. Authentication is via OAuth (recommended) or API keys. The standard rate limit is 120 requests per minute on the Teams plan, with higher limits available for Organizations and Enterprise customers.

Key resource areas:
- Bookings
- Event Types
- Schedules
- Calendars
- Teams and Organizations
- Webhooks

## Plans

See [plans/calcom-plans.md](plans/calcom-plans.md) for a full breakdown of Free, Teams, Organizations, Enterprise, and self-hosted options.

## Rate Limits

See [rate-limits/calcom-rate-limits.md](rate-limits/calcom-rate-limits.md) for rate limit details by plan and authentication method.

## FinOps

See [finops/calcom-finops.md](finops/calcom-finops.md) for cost management guidance when building on Cal.com's API.

## Maintainer

Kin Lane — kin@apievangelist.com

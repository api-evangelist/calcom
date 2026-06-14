# Cal.com FinOps

This document covers cost management considerations when building on Cal.com's API, including plan selection, API usage costs, and strategies for optimizing spend.

## Cost Model

Cal.com uses a **per-user, per-month** subscription model. There are no API call charges on top of the subscription fee — API access is included with Teams and higher plans. Cost is driven by:

1. Number of seats (users) on your plan
2. Plan tier required for the features you need
3. Enterprise add-ons (EU data hosting, dedicated database, HIPAA, higher SLAs)

## Plan Cost Summary

| Plan          | Price (Annual) | API Access | Rate Limit       |
|---------------|---------------|------------|------------------|
| Free          | $0/user/mo    | No         | —                |
| Teams         | $12/user/mo   | Yes        | 120 req/min      |
| Organizations | $28/user/mo   | Yes        | ~200 req/min     |
| Enterprise    | Custom        | Yes        | Up to 800 req/min|
| Self-hosted   | $0 + infra    | Yes        | Unlimited        |

## FinOps Recommendations

### Minimize Seat Count

API access is gated at the Teams plan and above, but you pay per seat. If building an integration that only needs API access, consider whether a single-seat Teams plan at $12/month meets your needs before scaling to org-wide licensing.

### Self-Hosting for High-Volume / Cost-Sensitive Workloads

Cal.com is fully open source (AGPL-3.0). For high-volume internal tooling or applications where the per-seat cloud cost becomes prohibitive, self-hosting via [cal.diy](https://github.com/calcom/cal.diy) eliminates subscription costs entirely, replacing them with infrastructure costs (server, database, email delivery).

### Enterprise Add-On Costs

The pricing calculator at https://cal.com/pricing supports itemizing add-ons including:
- HIPAA compliance
- EU data hosting
- Dedicated database
- Custom SLAs

Request a PDF quote to compare cloud vs. self-hosted TCO before committing to enterprise tier.

### Rate Limit Headroom

The default 120 req/min limit is sufficient for most integrations. Before requesting a rate limit increase (which may trigger enterprise-tier upselling), audit your API call patterns:
- Batch API calls where possible
- Cache event type and schedule data (they change infrequently)
- Use webhooks instead of polling for booking state changes

### OAuth Token Lifecycle

Access tokens expire after 60 minutes. Implement proper token refresh logic to avoid unnecessary re-authentication overhead. Refresh tokens last 1 year, so a well-implemented OAuth flow has minimal overhead.

## References

- Pricing: https://cal.com/pricing
- API v2 Introduction: https://cal.com/docs/api-reference/v2/introduction
- Self-hosted repo: https://github.com/calcom/cal.diy

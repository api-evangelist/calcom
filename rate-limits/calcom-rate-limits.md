# Cal.com Rate Limits

Cal.com enforces rate limits on its REST API v2 to ensure platform stability. Limits vary by plan and authentication method.

## Standard Rate Limits

| Plan / Auth Method | Requests per Minute |
|--------------------|---------------------|
| API Key (Teams)    | 120                 |
| API Key (Orgs, on request) | ~200       |
| Enterprise         | Up to 800           |
| Self-hosted        | No enforced limit (operator-defined) |

## Authentication Methods and Their Limits

### API Key Authentication

- Default limit: **120 requests per minute**
- Limit increase to ~200 req/min available upon request to Cal.com support
- Keys are created in Settings > Security in the Cal.com dashboard
- Test mode keys are prefixed `cal_`; live mode keys are prefixed `cal_live_`

### OAuth Authentication

- Recommended for third-party integrations and platform customers
- Access tokens are valid for **60 minutes**
- Refresh tokens are valid for **1 year**
- Rate limits mirror those of the underlying account plan

### Platform OAuth (Deprecated)

- Deprecated as of December 15, 2025; enterprise support only
- Used legacy headers `x-cal-client-id` and `x-cal-secret-key`

## Rate Limit Headers

Cal.com follows standard HTTP rate limiting conventions. When you exceed the rate limit, the API returns a `429 Too Many Requests` response. Clients should implement exponential backoff and retry logic.

## Enforcement Notes

- All API requests must use HTTPS; HTTP calls fail
- Rate limits are per API key / OAuth token, not per IP
- Enterprise customers can negotiate higher limits with dedicated database and SLA options

## References

- API v2 Introduction: https://cal.com/docs/api-reference/v2/introduction
- OAuth setup: https://cal.com/docs/api-reference/v2/oauth

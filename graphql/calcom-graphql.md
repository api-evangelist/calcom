# Cal.com GraphQL API

Cal.com does not expose a native GraphQL endpoint. The platform's public-facing API is a REST API (v2, hosted at `https://api.cal.com/v2`), and its internal application layer uses tRPC for client-server communication. The GraphQL schema in this directory is derived from Cal.com's authoritative Prisma database schema at `packages/prisma/schema.prisma` in the open-source repository, which defines all core data models.

**Endpoint:** N/A - Cal.com provides a REST API, not a GraphQL endpoint. No hosted GraphQL endpoint exists.

**Documentation:** https://cal.com/docs/api-reference/v2/introduction

**Authentication:** API key (Bearer token via `Authorization: Bearer <api_key>` header) or OAuth 2.0. API keys are scoped to a user or team. Rate limits start at 120 requests per minute on free plans.

**References:**
- Documentation: https://cal.com/docs/api-reference/v2/introduction
- GitHub: https://github.com/calcom/cal.com
- Prisma Schema (canonical data model source): https://github.com/calcom/cal.com/blob/main/packages/prisma/schema.prisma
- tRPC Routers (internal API): https://github.com/calcom/cal.com/tree/main/packages/trpc/server/routers

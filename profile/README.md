<p align="center">
  <img src="https://raw.githubusercontent.com/stratum-hq/Stratum/master/assets/stratumlogo.png" alt="Stratum" width="120" />
</p>

<h2 align="center">Stratum HQ</h2>

<p align="center">
  <strong>Drop-in multi-tenancy for Node.js</strong> — from flat SaaS to deep enterprise hierarchies, in one library.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/TypeScript-100%25-3178c6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/PostgreSQL-16+-336791?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/License-MIT-blue?style=flat-square" alt="License" />
  <img src="https://img.shields.io/badge/npm-%40stratum--hq%2F*-cb3837?style=flat-square&logo=npm&logoColor=white" alt="npm" />
</p>

---

Every SaaS team starts with `tenant_id` on every table. It works until Month 6 (enterprise config), Month 12 (compliance audit), and Month 18 (data isolation). Stratum gives you all of it from day one — tenant hierarchy, config inheritance, permission delegation, three isolation strategies, ABAC, field-level encryption, audit logging, GDPR compliance, webhooks, and multi-region support.

### 30-Second Quickstart

```bash
npx @stratum-hq/create my-app   # scaffold a new project
cd my-app && npm run dev         # autoMigrate handles the rest
```

Or add to an existing project:

```bash
npm install @stratum-hq/lib pg
```

```typescript
const stratum = new Stratum({ pool: new Pool(), autoMigrate: true });
await stratum.initialize();

const org = await stratum.createOrganization({ name: "Acme Corp", slug: "acme" });
await stratum.setConfig(org.id, "seat_limit", { value: 25 });
```

### Repositories

| Repo | Description |
|------|-------------|
| [Stratum](https://github.com/stratum-hq/Stratum) | Core monorepo — 12 TypeScript packages, control plane, CLI, React components, docs site |
| [stratum-python](https://github.com/stratum-hq/stratum-python) | Python SDK (auto-generated from OpenAPI) |
| [stratum-go](https://github.com/stratum-hq/stratum-go) | Go SDK (auto-generated from OpenAPI) |

### Packages

| Package | What it does |
|---------|-------------|
| [`@stratum-hq/lib`](https://www.npmjs.com/package/@stratum-hq/lib) | Direct library — tenants, config, permissions, ABAC, audit, GDPR |
| [`@stratum-hq/sdk`](https://www.npmjs.com/package/@stratum-hq/sdk) | HTTP client with LRU cache, Express/Fastify middleware |
| [`@stratum-hq/nestjs`](https://www.npmjs.com/package/@stratum-hq/nestjs) | NestJS integration — guard, `@Tenant()` decorator, DI module |
| [`@stratum-hq/db-adapters`](https://www.npmjs.com/package/@stratum-hq/db-adapters) | PostgreSQL adapters — raw pg, Prisma, Sequelize, RLS, schema/DB isolation |
| [`@stratum-hq/react`](https://www.npmjs.com/package/@stratum-hq/react) | React components — tenant tree, config editor, permission editor |
| [`@stratum-hq/cli`](https://www.npmjs.com/package/@stratum-hq/cli) | CLI — `init`, `migrate`, `scaffold`, `doctor` |
| [`@stratum-hq/create`](https://www.npmjs.com/package/@stratum-hq/create) | Project scaffolding — `npx @stratum-hq/create my-app` |
| [`@stratum-hq/control-plane`](https://www.npmjs.com/package/@stratum-hq/control-plane) | Fastify v5 REST API with auth, scopes, OTel, Redis rate limiting |
| [`@stratum-hq/core`](https://www.npmjs.com/package/@stratum-hq/core) | Shared types, Zod schemas, error classes |

### Key Features

- **Tenant hierarchy** — tree structure with ltree, up to 20 levels deep
- **Config inheritance** — values flow root to leaf, parents can lock keys
- **Permission delegation** — LOCKED / INHERITED / DELEGATED with cascade revocation
- **ABAC** — attribute-based access control with 9 operators, hierarchical policy inheritance
- **Three isolation strategies** — shared RLS, schema-per-tenant, database-per-tenant
- **Field-level encryption** — AES-256-GCM with key rotation
- **Audit logging** — every mutation with before/after state and actor identity
- **GDPR compliance** — data export (Article 20) and hard purge (Article 17)
- **Webhooks** — HMAC-signed lifecycle events with retry and dead-letter queue
- **Multi-region** — region CRUD with tenant migration
- **310+ tests** — validated against real PostgreSQL 16

### Links

- [Documentation](https://docs.stratum-hq.org) — guides, API reference, package docs
- [Landing Page](https://stratum-hq.org) — product overview
- [npm](https://www.npmjs.com/org/stratum-hq) — all published packages
- [Contributing](https://github.com/stratum-hq/Stratum/blob/master/CONTRIBUTING.md) — setup, code style, PR guidelines

### License

MIT

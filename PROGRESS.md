# PROGRESS: URL Shortener API (10h plan)

Budget: 10h total (Day 1 = 5h, Day 2 = 5h). Flag at 75% of each step's budget.

## Environment
- [ ] Node 22 + Yarn ready, Nest CLI available, existing scaffold runs (`yarn start:dev`)
- [ ] Neon project created; pooled and direct connection strings saved

## Day 1 (5h)
1. [ ] Setup (45m):
   - [ ] scaffold runs (`yarn start:dev`)
   - [x] Prisma 7.10.1 + Neon, first migration (`init`, User table) applied
   - [ ] @nestjs/config with env validation
   - [ ] PrismaService
   - [ ] global ValidationPipe
1b. [ ] Docker for Postgres only (30m, taken from Day 2 buffer): docker-compose.yml (one Postgres service, named volume, port), update DATABASE_URL/DIRECT_URL in `.env` and `.env.example`, re-run migration. Neon stays as fallback. Done right after Step 1, before Step 2.
2. [ ] Users + Auth (1h45m): register, login (bcrypt), JWT strategy, global JwtAuthGuard, @CurrentUser(), @Public()
3. [ ] Links CRUD, owner-only (1h45m): `nest g resource`, create (random code or alias), list mine, get, update, delete, ownership check, DTO validation, HTTP exceptions
4. [ ] Redirect (45m): public GET /:code, reject expired/inactive, 302, unique index on code

- [ ] Day 1 quiz (3 questions)

## Day 2 (5h)
5. [ ] Click tracking (1h): direct write in service, then EventEmitter2 event + listener (timestamp, referrer, user-agent)
6. [ ] Analytics (1h15m): GET /links/:id/stats (total, clicks per day, top referrers) with Prisma groupBy/aggregate
7. [ ] Pagination (45m): page/limit query DTO with class-transformer on GET /links
8. [ ] Global exception filter OR response-wrapping interceptor (45m)
9. [ ] Buffer and review (1h15m): leftovers, final code review, learning summary, next-steps list

- [ ] Day 2 quiz (3 questions)

## Later (not in scope for these 10h)
- Caching (Redis cache store)
- Throttling (rate limiting)
- Cron jobs (@nestjs/schedule)
- Swagger / OpenAPI
- Unit and e2e tests
- Dockerize the Nest app (Dockerfile)
- Redis

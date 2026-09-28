# Manuel Reyes

Systems engineer. PostgreSQL, AWS, and the parts of production that fail quietly.

Most monitoring tells you when something is down. I build tools for the other case:
the plan that drifted, the index that stopped returning what it used to, the constraint
your schema claims and never enforced. No error, no alert, no log line — just a system
that is no longer doing what you believe it does.

## PostgreSQL extensions

Five, all published on [PGXN](https://pgxn.org/). All **pure SQL, no shared library**, so
they install on RDS, Aurora and Supabase, where extensions written in C cannot go.

| Extension | What it watches |
|---|---|
| [pg_plan_guard](https://github.com/Manuelreyesbravo/pg_plan_guard) | Detects when a query plan drifts away from the plan you approved. Built on `pg_plan_advice`, new in PostgreSQL 19. |
| [pg_recall_guard](https://github.com/Manuelreyesbravo/pg_recall_guard) | Watches vector indexes for recall drift against a baseline you approved. Works with pgvector, pgvectorscale and any index with distance ordering operators. |
| [pg_promise_guard](https://github.com/Manuelreyesbravo/pg_promise_guard) | Finds the guarantees your schema claims and silently does not enforce: invalid unique indexes, `NOT VALID` constraints, disabled triggers, RLS without `FORCE`. |
| [pg_grammar_guard](https://github.com/Manuelreyesbravo/pg_grammar_guard) | Compiles a token-level grammar from your live catalog, and watches it for drift. |
| [pg_living_assertions](https://github.com/Manuelreyesbravo/pg_living_assertions) | A registry of things you claim are true, with the SQL that proves them and the date they were last proven. |

Every one of them ships a regression suite that runs with `make installcheck`, and each
was tested against more than one PostgreSQL major version before release.

## Upstream

- Open pull request on **pgvector**.
- **BUG #19638** reported against the planner.
- Ported **pgvectorscale** to the PostgreSQL 19 beta. It runs in production here, behind
  30 vector and full-text indexes in daily use.

## In production

Around twenty applications on AWS across three accounts, on PostgreSQL 17 and 18:
multi-tenant Row Level Security, logical replication, backup and restore, query and
schema design, and SQL Server to PostgreSQL migrations.

## Also here

n8n community nodes published on npm — LATAM identity, shipping and e-signature,
WhatsApp, Square, Stability AI — and a fork of llama.cpp with an NPU backend.

## Available for contract work

Remote from Chile, with daily overlap with US hours. Performance and query work, schema
design, migrations, extension development, and fixed-price audits of slow queries or AWS
cost.

manuelreyesbravo@gmail.com

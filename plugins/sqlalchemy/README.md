# SQLAlchemy

Database plugin that helps AI agents write correct SQLAlchemy code using both
the Core SQL Expression Language and the ORM.

## What it does

Covers the full SQLAlchemy stack for working with relational databases in Python.

| Area | Examples |
|------|----------|
| Engine management | Connection strings, engine creation, connection pooling |
| Declarative mapping | Model definitions, column types, relationships |
| Sessions | Transaction management, unit of work, flushing |
| Queries | Select, filter, join, aggregation, subqueries |
| Async support | async sessions, async engine configuration |

## Skills

### `sqlalchemy`

Activated when working with databases in Python, defining models, building
queries, managing sessions, or interacting with SQL databases using Python
objects. Supports PostgreSQL, MySQL, SQLite, and other backends through
SQLAlchemy's database-agnostic API.

## Prerequisites

- Python with `sqlalchemy` (`pip install sqlalchemy`)
- For async support: `pip install sqlalchemy[asyncio]`

## Upstream Sources

| Local Path | Upstream URL |
|------------|--------------|
| `skills/sqlalchemy` | https://github.com/pavelzw/skill-forge/tree/main/recipes/sqlalchemy |

# Storage Stack — Speed-First Design

AKM uses a three-layer storage architecture optimized for speed, persistence, and human readability.

## The Stack

| Layer | Tool | Role | Speed | When to Use |
|---|---|---|---|---|
| Hot Cache | Redis | Active session working memory | < 1ms | Always, for current session |
| Persistent Graph (Personal) | Obsidian Vault | Human-readable, portable memory | File I/O | Single user / small teams |
| Persistent Graph (Production) | NebulaGraph | 1B+ edges at ~2ms traversal | ~2ms | Production deployments |
| Backup / Export | JSON / Parquet | Portability, debugging, snapshots | Batch | Never for live queries |

## Why Not JSON as Primary Store?

JSON is a flat file. Every read/write loads the **entire file** into memory.
No indexing. No traversal. No query engine.
JSON is for **exports and backups only** — never for live memory operations.

## Why NebulaGraph Over Neo4j?

| Benchmark | NebulaGraph | Neo4j |
|---|---|---|
| 1 billion edges query | < 22ms | 176 seconds |
| 8 billion edges query | < 5 seconds | > 6 minutes |
| License | Open source (Apache 2.0) | Commercial |
| Scaling | Horizontal | Vertical (limited) |

## Data Flow

```
User talks to AI
      ↓
[Redis] ← writes active session connections instantly (< 1ms)
      ↓  (every N seconds OR at session end)
[Obsidian / NebulaGraph] ← merges new connections into permanent graph
      ↓  (during sleep cycle)
[JSON/Parquet] ← exports snapshot for safety and portability
      ↓
[Obsidian Vault] ← synced as human-readable memory mirror
```

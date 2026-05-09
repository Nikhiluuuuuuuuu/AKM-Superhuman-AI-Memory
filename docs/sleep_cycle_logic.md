# Sleep Cycle — 7-Step Consolidation Logic

The AKM Sleep Cycle runs during low-activity periods to maintain memory graph health.

## Trigger Conditions

```
if (time_since_last_user_activity > 30 minutes)
    OR (scheduled nightly run at 03:00 local time)
    → trigger sleep cycle
```

## The 7 Steps

| Step | Operation | Big-O | Description |
|---|---|---|---|
| 1 | `apply_decay_all` | O(E) | Apply Ebbinghaus decay to all edges: `R(t) = e^(-t/S)` |
| 2 | `_prune` | O(E) | Remove edges below weight threshold. Infant protection (< 5 min) applies. |
| 3 | `_merge_duplicates` | O(V × deg) | Collapse near-identical nodes (Jaccard > 0.85 + semantic similarity). |
| 4 | `_strengthen_top_n` | O(V log V) | Replay LTP on top-N most accessed nodes. |
| 5 | `_promote_stable` | O(V) | Graduate Working Memory nodes to Long-Term. |
| 6 | `_resolve_contradictions` | O(E) | Remove logically opposing relations (e.g., causes vs prevents). |
| 7 | `_backup` | O(V+E) | Export to JSON/Parquet + sync to Obsidian vault. |

## Memory Protection Policies

- **Infant Protection**: Edges created < 5 minutes ago are never pruned.
- **Identity Protection**: Nodes with `importance_score > 0.6` are shielded from orphan pruning.
- **Semantic Safety**: Merging requires `Jaccard > 0.85` AND keyword similarity check.
- **Salience Shield**: Nodes with `emotional_salience > 0.7` are never auto-pruned.

## Obsidian Sync (Step 7)

After backup, the sleep cycle syncs all modified nodes to the Obsidian vault:
- Updated nodes → rewrite `.md` files with new frontmatter weights
- Pruned nodes → delete corresponding `.md` files
- Merged nodes → merge files and update all incoming wikilinks

# 🧠 AKM — Associative Keyword Memory
### The Ultimate Brain-Accurate Persistent Memory Architecture for AI

> *Conceived by Nikhil Sai Pagidimarri — Nellore, Andhra Pradesh, India — April 2026*

---

## What Is AKM?

**Associative Keyword Memory (AKM)** is a production-ready, brain-accurate persistent memory engine for AI systems. It solves the single biggest flaw in every AI today: **they forget everything the moment a conversation ends.**

AKM gives any AI a memory that works exactly like the human brain — and in several ways, surpasses it.

---

## ⚡ Key Highlights

- 🧠 **6 Brain-Mapped Memory Types** — Semantic, Episodic, Procedural, Priming, Emotional, Working
- 🔗 **Self-Growing Associative Graph** — Concepts connect, strengthen, and decay like real synapses
- 💾 **Obsidian Memory Graph** — Uses the Obsidian graph (`.obsidian/` vault) as the persistent memory graph layer instead of a new custom graph
- ⚡ **3-Layer Storage Stack** — Redis (hot cache) → NebulaGraph (persistent) → JSON/Parquet (backup)
- 🛡️ **Hippocampus Gatekeeper** — Filters noise before anything touches memory
- 😢 **Amygdala Emotional Tagging** — Emotional salience drives retention and decay rates
- 🌙 **Sleep Mode Consolidation** — Background process prunes, merges, and strengthens the graph
- 🔄 **Reconsolidation on Recall** — Memory evolves every time it is accessed
- 🎯 **Prefrontal Executive Controller** — Goal-directed attention and lateral inhibition
- 📈 **Dual-Rate Learning (CLS)** — Solves catastrophic forgetting with hippocampal + neocortical learning rates

---

## 🗂️ Repository Structure

```
AKM-Superhuman-AI-Memory/
├── README.md                        ← This file
├── AKM_Ultimate_Architecture.md     ← Full architecture specification
├── OBSIDIAN_INTEGRATION.md          ← Obsidian Memory Graph integration guide
├── docs/
│   ├── memory_node_schema.json      ← Memory node data structure
│   ├── sleep_cycle_logic.md         ← Sleep Mode 7-step consolidation
│   └── storage_stack.md             ← Speed-first storage design
├── src/
│   ├── hippocampus/                 ← Gatekeeper & encoding logic
│   ├── amygdala/                    ← Emotional salience scoring
│   ├── memory_graph/                ← Core AKM graph engine
│   ├── obsidian_bridge/             ← Obsidian vault ↔ AKM graph sync
│   ├── sleep_cycle/                 ← Background consolidation engine
│   ├── retrieval/                   ← Traversal-based retrieval
│   └── prefrontal/                  ← Executive controller
└── tests/
    └── ...                          ← Unit + integration tests
```

---

## 🔌 Obsidian Memory Graph — Key Design Decision

Instead of building a completely new graph database from scratch, **AKM uses the Obsidian vault's graph as its persistent memory layer.** This means:

- Every memory node = an Obsidian note (`.md` file)
- Every edge/connection = an `[[wikilink]]` between notes
- Edge weights are stored as frontmatter YAML metadata
- The Obsidian graph visualizer becomes a **live, human-readable view of the AI's memory**
- Memory is **portable** — just copy the vault folder
- No new graph infrastructure needed for individuals and small deployments

For production-scale deployments, **NebulaGraph** serves as the high-performance backend with the Obsidian vault kept as a human-readable sync layer.

See [`OBSIDIAN_INTEGRATION.md`](./OBSIDIAN_INTEGRATION.md) for full details.

---

## 🧬 Brain Components → Software Components

| Brain Region | Role | AKM Component |
|---|---|---|
| Hippocampus | Memory gatekeeper & encoder | `HippocampusLayer` — filters & scores incoming signals |
| Neocortex | Long-term semantic storage | NebulaGraph persistent keyword graph |
| Amygdala | Emotional tagging | `AmygdalaLayer` — salience scoring 0.0→1.0 |
| Prefrontal Cortex | Working memory & attention | Redis session store + `PrefrontalController` |
| Basal Ganglia | Procedural/habit memory | Action chain graph |
| Cerebellum | Error correction & fine-tuning | `CerebellumEngine` — retrieval error learning |

---

## 📊 Why AKM Beats Every Alternative

| Feature | Vector DB | Knowledge Graph | RAG | **AKM** |
|---|---|---|---|---|
| Persistent memory | ✅ | ✅ | ✅ | ✅ |
| Self-growing connections | ❌ | ❌ | ❌ | ✅ |
| Brain-like association | Partial | ❌ | ❌ | ✅ |
| Six memory types | ❌ | ❌ | ❌ | ✅ |
| Emotional salience | ❌ | ❌ | ❌ | ✅ |
| Memory decay + pruning | ❌ | ❌ | ❌ | ✅ |
| Reconsolidation on recall | ❌ | ❌ | ❌ | ✅ |
| Sleep-cycle consolidation | ❌ | ❌ | ❌ | ✅ |
| Obsidian graph integration | ❌ | ❌ | ❌ | ✅ |
| Forgets between sessions | ✅ (loses) | ✅ (loses) | ✅ (loses) | **❌ Never** |

---

## 📖 Full Architecture

See [`AKM_Ultimate_Architecture.md`](./AKM_Ultimate_Architecture.md) for the complete 25-section technical specification covering every layer, formula, and design decision.

---

## 📄 License & Attribution

*© Architecture & Idea — Nikhil Sai Pagidimarri, Nellore, Andhra Pradesh, India — April 2026*  
*Document compiled with assistance from Perplexity AI*

This repository is open for study, research, and collaboration. If you build on this architecture, please credit the original design.

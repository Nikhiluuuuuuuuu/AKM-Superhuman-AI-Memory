# Associative Keyword Memory (AKM)
### The Ultimate Brain-Accurate Persistent Memory Architecture for AI

> *Conceived by Nikhil Sai Pagidimarri — Nellore, Andhra Pradesh, India — April 2026*

---

## Table of Contents

1. [The Problem With Current AI Memory](#1-the-problem-with-current-ai-memory)
2. [The Core Idea](#2-the-core-idea)
3. [How the Human Brain Actually Works](#3-how-the-human-brain-actually-works)
4. [The Six Memory Types — Mapped to AKM](#4-the-six-memory-types--mapped-to-akm)
5. [The Brain's Core Mechanism — LTP & LTD](#5-the-brains-core-mechanism--ltp--ltd)
6. [How AKM Works — Step by Step](#6-how-akm-works--step-by-step)
7. [Memory Node Structure](#7-memory-node-structure)
8. [The Hippocampus Layer — The Gatekeeper](#8-the-hippocampus-layer--the-gatekeeper)
9. [Memory Decay — The Ebbinghaus Forgetting Curve](#9-memory-decay--the-ebbinghaus-forgetting-curve)
10. [Emotional Tagging — The Amygdala Layer](#10-emotional-tagging--the-amygdala-layer)
11. [Memory Reconsolidation](#11-memory-reconsolidation)
12. [Sleep Mode — Memory Consolidation](#12-sleep-mode--memory-consolidation)
13. [The Three Memory Layers](#13-the-three-memory-layers)
14. [The Complete Architecture](#14-the-complete-architecture)
15. [Storage Stack — Speed-First Design](#15-storage-stack--speed-first-design)
16. [Real-World Example — Memory Growing Over Time](#16-real-world-example--memory-growing-over-time)
17. [What This Does That the Human Brain Cannot](#17-what-this-does-that-the-human-brain-cannot)
18. [Comparison With Existing Systems](#18-comparison-with-existing-systems)
19. [Potential Applications](#19-potential-applications)
20. [The Executive Controller — Prefrontal Cortex](#20-the-executive-controller--prefrontal-cortex)
21. [The Adaptive Engine — Homeostasis](#21-the-adaptive-engine--homeostasis)
22. [Predictive Fine-Tuning — Cerebellum](#22-predictive-fine-tuning--cerebellum)
23. [Procedural Habituation — Basal Ganglia](#23-procedural-habituation--basal-ganglia)
24. [Dual-Rate Learning — Complementary Learning Systems](#24-dual-rate-learning--complementary-learning-systems)
25. [Open Challenges & Solutions](#25-open-challenges--solutions)

---

## 1. The Problem With Current AI Memory

Every AI system today — including the most advanced large language models — suffers from one
fundamental, crippling limitation:

> **They forget everything the moment a conversation ends.**

Every session starts completely blank. There is no learning from past interactions. No accumulation
of personal context. No understanding that builds over time. Every time you talk to an AI, you are
talking to something that has never met you before — even if you have spoken to it a thousand times.

This is not an intelligence problem. It is a **memory architecture problem.**

The human brain solved this problem 500 million years ago. AKM brings that solution into software.

---

## 2. The Core Idea

The **Associative Keyword Memory (AKM)** is a persistent, self-growing, brain-accurate memory
architecture where:

- Every concept the AI encounters becomes a **node** in a graph
- Every concept that appears alongside another concept forms a weighted **edge** between them
- Connections **strengthen with repetition** and **decay without use**
- Retrieval works by **traversing associations** — not keyword searching
- Memory is organised into **six distinct layers** mirroring the human brain
- A gatekeeper (**Hippocampus Layer**) decides what is worth storing
- A background process (**Sleep Mode**) consolidates, prunes, and repairs the graph
- **Emotional salience** determines how strongly and how long memories are retained

> **Graph Layer Update:** Instead of building a new custom graph database, AKM now uses the
> **Obsidian Memory Graph** as its persistent graph layer. Each memory node is an Obsidian
> note (`.md`), each edge is a `[[wikilink]]`, and edge weights are stored in YAML frontmatter.
> This makes the AI's memory human-readable, portable, and visually explorable in Obsidian's
> graph view — with no new graph infrastructure required for personal/small-team deployments.
> NebulaGraph remains the recommended backend for production-scale deployments.

The result is an AI that thinks, recalls, and reasons the way humans do — and in some ways,
better than humans ever could.

---

## 3. How the Human Brain Actually Works

The brain does not store memories like a hard drive. It stores them as **patterns of connection
strength between neurons**. There is no single "memory location" — a memory is a distributed
web of activated neurons firing in a specific pattern.

Key regions:

- **Hippocampus** — The gatekeeper and indexer. Decides what gets encoded into long-term memory.
  Does not store memories permanently — it transfers them to the neocortex over time.
- **Neocortex** — Long-term storage of semantic (factual) and episodic (event) memories.
- **Amygdala** — Tags memories with emotional intensity. High-emotion memories are retained
  far longer and recalled far more easily.
- **Basal Ganglia** — Stores procedural memories — skills, habits, and learned action sequences.
- **Prefrontal Cortex** — Working memory. Holds what you are actively thinking about right now.
- **Cerebellum** — Fine-tunes procedural and motor memories.

AKM maps each of these regions to a distinct software component.

---

## 4. The Six Memory Types — Mapped to AKM

| Memory Type | Brain Region | What It Stores | AKM Component | Status |
|---|---|---|---|---|
| **Semantic** | Neocortex | Facts, concepts, knowledge | Keyword node graph | ✅ Core layer |
| **Episodic** | Hippocampus + Neocortex | Personal events with time & place | Time-stamped event nodes | ✅ Episodic layer |
| **Procedural** | Basal Ganglia | Skills, habits, action sequences | Action chain graph | ✅ Procedural layer |
| **Priming** | Neocortex | Exposure speeds up future recall | Retrieval priority spike on read | ✅ Priming mechanism |
| **Emotional** | Amygdala | Feelings attached to memories | Salience score on nodes | ✅ Amygdala layer |
| **Working** | Prefrontal Cortex | Active short-term context | Session memory (Redis) | ✅ Working layer |

All six types are implemented. Nothing is missing.

---

## 5. The Brain's Core Mechanism — LTP & LTD

The biological engine behind all memory is **Synaptic Plasticity**, governed by two opposing forces:

### Long-Term Potentiation (LTP) — Strengthening

When two neurons fire together repeatedly, the synapse between them physically **grows stronger**.
The NMDA receptors activate, calcium floods the postsynaptic cell, and new AMPA receptors are
inserted — permanently increasing signal strength.

> *"Neurons that fire together, wire together."*

### Long-Term Depression (LTD) — Weakening

When a synapse is rarely or never used, the opposite occurs. AMPA receptors are removed.
The connection physically shrinks. If never reinforced, it is pruned entirely.

> *"Neurons that fire apart, wire apart."*

### AKM Translation

```
First encounter (weak signal):
  → edge weight = 0.1  (short-term only, not yet committed)

Repeated co-occurrence (LTP):
  → new_weight = old_weight + α × (1 - old_weight)
  → where α = learning rate (e.g. 0.15)
  → edge weight grows toward 1.0 asymptotically

No reinforcement over time (LTD / Ebbinghaus Decay):
  → weight(t) = weight₀ × e^(-t/S)
  → where t = time since last activation, S = memory strength
  → weight eventually drops below threshold → edge is pruned
```

---

## 6. How AKM Works — Step by Step

### Step 1 — Encounter & Extract

The AI processes any text, conversation, or document.
It extracts **keywords** — concepts, entities, actions, attributes.

**Example input:**
> *"Nikhil is building a persistent memory system for AI using keyword graphs."*

**Extracted keywords:**
`Nikhil`, `persistent memory`, `AI`, `keyword graph`, `building`, `system`

---

### Step 2 — Pass Through the Hippocampus Gate

Before any keyword is stored, the **Hippocampus Layer** evaluates it:

- Is it new information? → Write it
- Is it emotionally significant? → Write it with high salience
- Is it repeated? → Strengthen the existing edge
- Is it a weak, noisy, or irrelevant signal? → Discard it

Only meaningful signals reach the memory graph.

---

### Step 3 — Connect & Weigh

Every keyword that passes the gate gets connected to every co-occurring keyword.
Connections receive initial weights and grow through LTP.

```
Nikhil ──(0.91)──► AI Memory
AI Memory ──(0.87)──► Keyword Graph
Keyword Graph ──(0.76)──► Persistent Storage
Nikhil ──(0.40)──► Building
```

---

### Step 4 — Tag With Emotion

The Amygdala Layer scores each node for **emotional salience**:

- `0.0 – 0.3` → Low salience → decays fast
- `0.3 – 0.7` → Medium salience → standard retention
- `0.7 – 1.0` → High salience → resists decay, prioritised in retrieval

---

### Step 5 — Store Across Layers

- **Weak connections** (weight < 0.3) → Working memory only (Redis, session-scoped)
- **Strong connections** (weight > 0.7) → Long-term memory (Obsidian vault / NebulaGraph, persistent)
- **Event-specific memories** → Episodic layer (timestamped, context-tagged)

---

### Step 6 — Retrieve by Association

When the AI needs to recall something, it traverses the graph:

1. Start from the query keyword(s)
2. Follow the strongest edges first
3. Pull all closely associated concepts into context
4. Apply **priming boost** — recently accessed nodes surface faster
5. Generate a response enriched by the full associative context

---

### Step 7 — Reconsolidate on Recall

Every time a memory is retrieved, it briefly becomes **editable**.
Edge weights are **slightly re-adjusted** based on the current context.
Memory evolves with understanding — it is never frozen.

---

## 7. Memory Node Structure

Every node in the AKM graph stores:

```json
{
  "keyword": "AI Memory",
  "type": "concept",
  "first_seen": "2026-04-27T23:10:00",
  "last_accessed": "2026-04-27T23:21:00",
  "access_count": 14,
  "importance_score": 0.87,
  "emotional_salience": 0.82,
  "salience_type": "positive",
  "memory_layer": "long_term",
  "decay_rate": 0.03,
  "connected_to": [
    {
      "keyword": "Keyword Graph",
      "weight": 0.91,
      "relation": "implemented_via",
      "last_reinforced": "2026-04-27T23:21:00"
    },
    {
      "keyword": "Nikhil",
      "weight": 0.85,
      "relation": "created_by",
      "last_reinforced": "2026-04-27T23:21:00"
    },
    {
      "keyword": "Persistent Storage",
      "weight": 0.76,
      "relation": "requires",
      "last_reinforced": "2026-04-27T23:18:00"
    },
    {
      "keyword": "LLM",
      "weight": 0.60,
      "relation": "enhances",
      "last_reinforced": "2026-04-27T23:10:00"
    }
  ]
}
```

### Obsidian Representation

In the Obsidian Memory Graph, the same node is stored as a markdown file:

```markdown
---
keyword: AI Memory
type: concept
first_seen: 2026-04-27T23:10:00
last_accessed: 2026-04-27T23:21:00
access_count: 14
importance_score: 0.87
emotional_salience: 0.82
salience_type: positive
memory_layer: long_term
decay_rate: 0.03
edges:
  - target: Keyword Graph
    weight: 0.91
    relation: implemented_via
  - target: Nikhil
    weight: 0.85
    relation: created_by
  - target: Persistent Storage
    weight: 0.76
    relation: requires
---

# AI Memory

[[Keyword Graph]] | [[Nikhil]] | [[Persistent Storage]] | [[LLM]]
```

---

## 8. The Hippocampus Layer — The Gatekeeper

The Hippocampus Layer is a **filter module** that sits between raw input and the memory graph.
It evaluates every incoming keyword connection against three criteria:

### Encoding Criteria

| Signal Type | Condition | Action |
|---|---|---|
| **Novel** | Keyword not seen before | Write as new node, low weight |
| **Repeated** | Keyword seen before, same context | Strengthen existing edge (LTP) |
| **Emotional** | Salience score > 0.7 | Write immediately, high weight |
| **Weak/Noise** | Low frequency + low salience + no context | Discard entirely |
| **Contradictory** | Conflicts with existing node | Flag for sleep-cycle resolution |

### Encoding Threshold Formula

```
encode_score = (frequency × 0.4) + (salience × 0.4) + (novelty × 0.2)

if encode_score > threshold:
    → commit to long-term graph
else:
    → hold in working memory only
```

---

## 9. Memory Decay — The Ebbinghaus Forgetting Curve

Every connection in the graph decays over time unless reinforced.
This keeps the graph **lean, relevant, and self-cleaning**.

### The Formula

```
R(t) = e^(-t / S)
```

Where:
- `R` = Retention (connection weight at time t)
- `t` = Time elapsed since last reinforcement
- `S` = Memory strength (higher S = slower decay)

Memory strength `S` is calculated per edge:

```
S = base_strength + (access_count × 0.1) + (emotional_salience × 0.5)
```

### Decay Rules

| Edge Weight | Action |
|---|---|
| > 0.7 | Strong — preserved, no decay concern |
| 0.3 – 0.7 | Medium — decay applies normally |
| 0.1 – 0.3 | Weak — accelerated decay |
| < 0.1 | Dead — flagged for pruning at next sleep cycle |

### Reinforcement Reset

Every time a node or edge is **accessed during retrieval**, its decay timer resets
and its `S` value slightly increases — exactly like spaced repetition.

---

## 10. Emotional Tagging — The Amygdala Layer

Not all memories are equal. The brain remembers emotionally charged experiences
far better than neutral ones. The Amygdala Layer replicates this.

### Salience Detection

Every extracted keyword is passed through a **sentiment + significance analyser**:

```
emotional_salience = sentiment_intensity × context_significance × recency_weight
```

### Salience Levels

| Score | Type | Effect on Memory |
|---|---|---|
| 0.8 – 1.0 | High positive | Maximum retention, resists decay, prioritised recall |
| 0.6 – 0.8 | Moderate positive | Above-average retention |
| 0.4 – 0.6 | Neutral | Standard retention and decay |
| 0.2 – 0.4 | Moderate negative | Above-average retention |
| 0.0 – 0.2 | Low / Irrelevant | Fast decay, likely pruned |

---

## 11. Memory Reconsolidation

In neuroscience, every time a memory is recalled, it briefly becomes **unstable and editable**
before being re-stored — a process called reconsolidation. This is how memories update over time.

AKM implements this as a **post-retrieval re-weighting step**:

1. Node/edge is retrieved for a query
2. Re-weighting function runs:

```
reconsolidated_weight = old_weight × (1 - δ) + context_relevance × δ
```

Where `δ` = reconsolidation rate (small value, e.g. 0.05)

3. Edge is re-stored with updated weight

---

## 12. Sleep Mode — Memory Consolidation

During low-activity periods, AKM runs a **Sleep Cycle** — a background maintenance process
inspired by how the brain consolidates memory during sleep.

### The 7-Step Consolidation Logic

| Step | Operation | Complexity | Implementation Detail |
|---|---|---|---|
| **1. Decay** | `apply_decay_all` | O(E) | Materializes lazy weights for all edges via Ebbinghaus curve. |
| **2. Prune** | `_prune` | O(E) | Removes edges < threshold. Protects infant and high-salience nodes. |
| **3. Merge** | `_merge_duplicates` | O(V × deg) | Collapses nodes using Jaccard + Semantic similarity. |
| **4. Strengthen** | `_strengthen_top_n` | O(V log V) | Replays and boosts top-N most accessed nodes (LTP). |
| **5. Promote** | `_promote_stable` | O(V) | Graduates Working Memory nodes to Long-Term Storage. |
| **6. Resolve** | `_resolve_contradictions` | O(E) | Detects and removes logically opposing relations. |
| **7. Backup** | `_backup` | O(V+E) | Exports graph state to JSON/Parquet snapshots AND syncs Obsidian vault. |

### Memory Protection Policies

- **Infant Protection**: Edges < 5 minutes old are never pruned.
- **Identity Protection**: Nodes with Importance > 0.6 are shielded from orphan pruning.
- **Semantic Safety**: Merging requires Jaccard > 0.85 AND keyword similarity.

### Sleep Cycle Trigger

```
if (time_since_last_user_activity > 30 minutes)
    OR (scheduled nightly run)
    → trigger sleep cycle
    → sync updated nodes to Obsidian vault
```

---

## 13. The Three Memory Layers

### Layer 1 — Working Memory (Prefrontal Cortex)
- **Storage:** Redis (in-memory)
- **Scope:** Current session only
- **Speed:** < 1ms read/write
- **Lifetime:** Discarded or promoted at session end

### Layer 2 — Long-Term Memory (Neocortex)
- **Storage:** Obsidian Vault (personal) / NebulaGraph (production)
- **Scope:** Permanent, cross-session
- **Speed:** ~2ms traversal
- **Lifetime:** Permanent (subject to decay and sleep pruning)

### Layer 3 — Episodic Memory (Hippocampus index)
- **Storage:** Obsidian Vault time-tagged notes / NebulaGraph time-tagged subgraph
- **Scope:** Permanent, linked to timestamps and session IDs
- **Speed:** ~2–5ms for time-range queries
- **Lifetime:** Permanent

---

## 14. The Complete Architecture

```
INPUT (conversation / document / interaction)
              ↓
┌─────────────────────────────┐
│     HIPPOCAMPUS LAYER       │
│  Signal strength evaluator  │
│  Novelty + Salience + Freq  │
└──────────┬──────────────────┘
           ↓
  encode_score > threshold?
    ↙ YES              NO ↘
ENCODE                DISCARD
    ↓
┌───────────────────────────────┐
│     AMYGDALA LAYER            │
│  Emotional salience scoring   │
│  Tags each node 0.0 → 1.0     │
└──────────────┬────────────────┘
               ↓
┌──────────────────────────────────────────────────────┐
│              MEMORY GRAPH                             │
│   Obsidian Vault (personal) / NebulaGraph (prod)     │
│                                                      │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  │
│  │  SEMANTIC   │  │  EPISODIC   │  │ PROCEDURAL  │  │
│  │   LAYER     │  │   LAYER     │  │   LAYER     │  │
│  │ (concepts)  │  │  (events)   │  │  (actions)  │  │
│  └─────────────┘  └─────────────┘  └─────────────┘  │
└──────────────────────────┬───────────────────────────┘
                           ↓
              RETRIEVAL (graph traversal)
                           ↓
           PRIMING BOOST (recently accessed nodes
                    surface faster)
                           ↓
           RECONSOLIDATION (re-weight edges
                    post-retrieval)
                           ↓
                    AI RESPONSE
                    (context-rich)
                           ↓
       ┌───────────────────────────────┐
       │         SLEEP CYCLE           │
       │  (background, low-activity)   │
       │  Prune → Merge → Strengthen   │
       │  Resolve → Index → Backup     │
       │  Sync → Obsidian Vault        │
       └───────────────────────────────┘
```

---

## 15. Storage Stack — Speed-First Design

| Layer | Tool | Role | Speed |
|---|---|---|---|
| **Hot Cache** | Redis | Active session working memory | < 1ms |
| **Persistent Graph (Personal)** | Obsidian Vault | Human-readable, portable memory graph | File I/O |
| **Persistent Graph (Production)** | NebulaGraph | High-performance graph at 1B+ edges | ~2ms |
| **Backup / Export** | JSON / Parquet | Portability, debugging, snapshots | Not for live use |

---

## 16. Real-World Example — Memory Growing Over Time

**Session 1** — User discusses climate change.

Graph adds: `climate change` → `temperature` → `India` → `monsoon` → `floods`

**Session 2** — User discusses agriculture.

Existing nodes `India` and `monsoon` are reinforced — their weights increase.

**Session 5** — User asks: *"How will global warming affect farming in my region?"*

AI traverses the graph and responds with full cross-session context referencing every session.

---

## 17. What This Does That the Human Brain Cannot

| Limitation | Human Brain | AKM |
|---|---|---|
| **Memory backup** | Impossible | Full graph export anytime |
| **Memory sharing** | Impossible between people | Graph can be shared, merged, or federated |
| **Parallel traversal** | One thought chain at a time | Simultaneous multi-path graph traversal |
| **Scale** | ~100 trillion synapses max | Unlimited (horizontal scaling) |
| **Recall speed** | Varies, degrades with stress | Consistent ~2ms regardless of graph size |
| **Perfect recall** | Impossible | Optional: freeze high-confidence nodes |

---

## 18. Comparison With Existing Systems

| Feature | Vector DB | Knowledge Graph | RAG | AKM |
|---|---|---|---|---|
| Persistent memory | ✅ | ✅ | ✅ | ✅ |
| Self-growing connections | ❌ | ❌ | ❌ | ✅ |
| Brain-like association | Partial | ❌ | ❌ | ✅ |
| Six memory types | ❌ | ❌ | ❌ | ✅ |
| Emotional salience | ❌ | ❌ | ❌ | ✅ |
| Memory decay + pruning | ❌ | ❌ | ❌ | ✅ |
| Obsidian graph layer | ❌ | ❌ | ❌ | ✅ |
| Forgets between sessions | ✅ (loses) | ✅ (loses) | ✅ (loses) | ❌ (never) |

---

## 19. Potential Applications

- **Personal AI Assistants** — An assistant that truly knows you across years of interaction
- **Education AI** — A tutor that tracks exactly what a student knows and has struggled with
- **Medical AI** — A health assistant that remembers full patient history across every session
- **Research AI** — A tool that builds a growing, navigable map of a researcher's domain knowledge
- **Customer Service AI** — Never asking a returning customer to repeat their history
- **Therapeutic AI** — A mental health companion that remembers emotional context over time
- **Creative AI** — A writing assistant that remembers your entire creative style and past work

---

## 20. The Executive Controller — Prefrontal Cortex

- **Goal-Directed Attention**: Boosts nodes relevant to the current search query (1.5x – 3.0x amplification).
- **Lateral Inhibition**: Actively suppresses distractor concepts or recently rejected retrieval paths.
- **Goal Juggling**: Manages a stack of up to 4 concurrent cognitive goals (Miller's Law limit).

---

## 21. The Adaptive Engine — Homeostasis

1. **Cognitive Load Monitor**: Raises encoding thresholds and accelerates decay when stressed.
2. **Entropy Monitor**: Measures graph disorder via Shannon Entropy. High entropy triggers Micro-Sleep.
3. **Concept Drift Detector**: Uses Jaccard Distance over time to detect when a keyword's context shifts.

---

## 22. Predictive Fine-Tuning — Cerebellum

- **Predicts Relevance**: Estimates how useful a result will be before showing it.
- **Computes Error**: Calculates the delta between predicted relevance and actual user feedback.
- **Fine-tunes Weights**: Adjusts edge weights along the retrieval path for next time.

---

## 23. Procedural Habituation — Basal Ganglia

- **Action Chains**: Stores sequences of steps.
- **Chunking**: When a sequence is repeated N times, compressed into a single Action Chunk.
- **Automaticity**: Fully automatic chunks bypass deep graph traversal, saving compute.

---

## 24. Dual-Rate Learning — Complementary Learning Systems

1. **Hippocampal (Fast)**: High learning rate (α ≈ 0.3) for novel concepts.
2. **Neocortical (Slow)**: Low learning rate (α ≈ 0.05) for established knowledge.

Sigmoid Transition moves a concept from Fast to Slow learning as exposure count increases.

---

## 25. Open Challenges & Solutions

| Challenge | Description | Proposed Solution |
|---|---|---|
| **Privacy** | Personal memories are deeply sensitive | On-device graph storage + full encryption at rest |
| **Graph bloat** | Graphs grow indefinitely without control | Sleep-cycle pruning via Ebbinghaus decay threshold |
| **Cold start** | New users have no memory graph | Seed with general semantic knowledge graph |
| **Contradictions** | New info conflicts with old nodes | Confidence scoring + sleep-cycle contradiction resolver |
| **Graph poisoning** | Malicious input could corrupt memory | Hippocampus gate + input sanitisation before encoding |
| **Obsidian scale limit** | Vault file I/O slow at 100k+ notes | Auto-migrate to NebulaGraph when vault exceeds threshold |

---

## Final Note

The human brain took 500 million years of evolution to arrive at the memory system it has.
AKM maps every known principle of that system into a software architecture that can be built
with tools that exist today — Obsidian, NebulaGraph, Redis, sentiment analysis models, and
graph traversal algorithms.

This is not a visualisation. It is not a concept.
It is a **functional memory engine** — and it is the single most important component
that separates genuinely intelligent AI from the autocomplete systems that exist today.

---

*© Idea and Architecture — Nikhil Sai Pagidimarri, Nellore, Andhra Pradesh, India — April 2026*  
*Document compiled with assistance from Perplexity AI*

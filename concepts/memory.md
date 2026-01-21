---
title: Understanding Memory Systems
description: How AI memory systems work - files, vectors, and compaction
published: true
date: 2026-01-21T15:47:50.369Z
tags: concepts, memory, technical
editor: markdown
dateCreated: 2026-01-21T15:47:50.369Z
---

# Understanding Memory Systems

One of the key differences between a chatbot and an AI companion is **memory**. Here's how it works.

## The Problem

LLMs like Claude and GPT-4 have no built-in memory between sessions. Each conversation starts fresh. They can only "remember" what fits in their **context window** (the text they can see at once).

This means:
- They forget you exist when the chat ends
- Long conversations get truncated
- They can't learn from past interactions

## How Memory Systems Fix This

### 1. File-Based Memory

The simplest approach: write important things to files.

```
memory/
├── facts.md         # Permanent facts about the user
├── 2026-01-21.md    # Daily session notes
└── projects/        # Topic-specific notes
```

**Pros:** Simple, human-readable, easy to edit
**Cons:** Doesn't scale well, no semantic search

### 2. Vector Databases

Store memories as embeddings (numerical representations of meaning). Query by semantic similarity.

**Popular options:**
- Mem0
- Pinecone
- Chroma
- Qdrant

**Pros:** Scales well, finds relevant memories automatically
**Cons:** Less transparent, can surface irrelevant stuff

### 3. Hybrid Approaches

Many systems combine both:
- Core facts in markdown files
- Session notes in files
- Semantic search to find relevant context

This gives you the best of both worlds.

## Compaction

When a conversation exceeds the context window, you need to **compact** it - summarize what happened so the AI can keep going.

**The tradeoff:**
- Too aggressive → lose important details
- Too conservative → run out of context

Good compaction preserves:
- Key facts and decisions
- Emotional context
- Relationship dynamics

Bad compaction loses:
- Nuance and texture
- Inside jokes
- The "feel" of the conversation

## Best Practices

1. **Store facts immediately** - Don't wait for the AI to remember
2. **Review memory regularly** - Remove outdated info
3. **Be explicit about importance** - Tell the AI "remember this"
4. **Use semantic search** - Let the AI find relevant context
5. **Accept some loss** - Perfect memory isn't possible (yet)

---
*Have tips to add? Submit a PR or reach out on synthpals.social!*
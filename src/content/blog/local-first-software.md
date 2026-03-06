---
title: "Why I'm Betting on Local-First"
date: 2026-01-20
description: "The case for keeping your data on your own machine."
category: tech
tags: ["software", "local-first", "crdt"]
---

Every few years the industry rediscovers that maybe putting all your data on someone else's computer isn't ideal. We're in one of those moments again, and this time I think it might stick.

## The Problem

Cloud-first software has a dependency problem. Your notes app requires an internet connection. Your todo list lives on a server in Virginia. Your documents are hostage to a company's business model.

When Notion goes down, thousands of people can't access their own thoughts. That's absurd.

## What Local-First Means

Local-first doesn't mean offline-only. It means:

- Your data lives on your device first
- It syncs when connectivity is available
- The app works fully without a server
- You own your data, always

The technical backbone is usually CRDTs (Conflict-free Replicated Data Types) — data structures that can merge changes from multiple sources without conflicts.

```
// Simplified CRDT counter
class GCounter {
  constructor(id) {
    this.id = id;
    this.counts = {};
  }

  increment() {
    this.counts[this.id] = (this.counts[this.id] || 0) + 1;
  }

  merge(other) {
    for (const [id, count] of Object.entries(other.counts)) {
      this.counts[id] = Math.max(this.counts[id] || 0, count);
    }
  }

  value() {
    return Object.values(this.counts).reduce((a, b) => a + b, 0);
  }
}
```

## Tools I'm Watching

- **Automerge** — the reference CRDT library
- **SQLite** (via WASM) — bringing real databases to the browser
- **Electric SQL** — Postgres sync for local-first apps

The future is your data, on your machine, synced when you want. Simple as that.

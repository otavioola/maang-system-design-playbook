# Quick Reference Guide

> **Print this out and keep it next to you during practice interviews**

---

## The 11-Step Framework (Memorize This)

Every system design follows this structure:

1. **Problem Statement** — Restate the problem in your words
2. **Clarifying Questions** — Ask 3-5 targeted questions about scale, features, constraints
3. **Requirements** — Functional + Non-Functional (explicit)
4. **Scale Assumptions** — Users, QPS, storage (with numbers)
5. **High-Level Architecture** — Draw boxes: Client → LB → Services → DB
6. **Core Components** — List 4-6 key components
7. **Data Flow** — Explain write flow and read flow step-by-step
8. **Bottlenecks** — Identify 3-4 bottlenecks and solutions
9. **Trade-offs** — Explain key decisions and what you're giving up
10. **How to Explain This in an Interview** — Practice your narrative
11. **Common Mistakes** — What NOT to do

---

## Essential Numbers to Remember

**Units:**

- 1 KB = 10^3 bytes = 1,000 bytes
- 1 MB = 10^6 bytes = 1,000,000 bytes
- 1 GB = 10^9 bytes
- 1 TB = 10^12 bytes
- 1 PB = 10^15 bytes

**Latency:**

- L1 cache: 0.5 ns
- L2 cache: 7 ns
- RAM: 100 ns
- SSD: 150 μs (0.15 ms)
- HDD: 10 ms
- Network (same datacenter): 0.5 ms
- Network (cross-region): 50-100 ms

**Capacity:**

- QPS: 1K (small), 10K (medium), 100K (large), 1M+ (very large)
- Users: 1M (small), 10M (medium), 100M (large), 1B+ (very large)
- Replication factor: 3x (standard)
- Peak multiplier: 10x average

---

## Key Trade-offs (Know These Cold)

| Decision                   | Choose A                 | Choose B                      | Key Factor                                                  |
| -------------------------- | ------------------------ | ----------------------------- | ----------------------------------------------------------- |
| **SQL vs NoSQL**           | SQL (ACID, joins)        | NoSQL (scale, simple queries) | Need ACID? → SQL. Need 1M+ QPS writes? → NoSQL              |
| **Cache vs DB**            | Cache (latency)          | DB (consistency)              | Read-heavy? → Cache. Need strong consistency? → DB          |
| **Sync vs Async**          | Sync (simple, immediate) | Async (throughput, decoupled) | Fast (<100ms)? → Sync. Slow (>1s)? → Async                  |
| **Push vs Pull**           | Push (real-time)         | Pull (scalable)               | <100K users + real-time? → Push. >1M users? → Pull          |
| **Vertical vs Horizontal** | Vertical (simple)        | Horizontal (scalable)         | Small scale? → Vertical. Need unlimited scale? → Horizontal |

---

## Clarifying Questions Template

**Always ask these 3-5 questions:**

1. **Scale**: "What's the expected scale? Users and QPS?"
2. **Features**: "What features are must-haves? What's out of scope?"
3. **Constraints**: "What are the latency and availability requirements?"
4. **Patterns**: "What's the read vs write ratio?"
5. **Geographic**: "Is this global or single region?"

---

## Common Architecture Patterns (Quick Draw)

**Three-Tier:**

```
Client → LB → [App Servers] → DB (+ Read Replicas)
```

**With Cache:**

```
Client → LB → [App Servers] → Cache (Redis) → DB
```

**With Queue:**

```
Client → API → Queue → [Workers] → DB
```

**Microservices:**

```
Client → API Gateway → [Service A, Service B, Service C]
                           ↓         ↓         ↓
                        [DB A]   [DB B]   [DB C]
```

---

## Interview Time Management (45 minutes)

- **0-5 min**: Clarifying questions
- **5-15 min**: Requirements + scale assumptions
- **15-20 min**: High-level architecture (draw boxes)
- **20-35 min**: Deep dive into 2-3 components
- **35-40 min**: Trade-offs + bottlenecks
- **40-45 min**: Wrap-up, edge cases, monitoring

**Pro Tip**: If you're running out of time, skip to trade-offs. That's what matters most.

---

## Phrases That Signal Senior Thinking

Use these exact phrases in your interviews:

- "Let me clarify the scale first..."
- "I'm making a trade-off here: X for Y..."
- "The bottleneck will be..."
- "If we need to scale further, we could..."
- "The failure mode here is..."
- "I optimize for X because Y, accepting Z as a trade-off"
- "For this use case, X is more important than Y"

---

## Common Mistakes to Avoid

❌ **Jumping to solution**: "We need microservices!"
✅ **Fix**: Clarify requirements first

❌ **No numbers**: "Lots of users"
✅ **Fix**: "100M users, 10K QPS"

❌ **Forgetting trade-offs**: "We use Redis"
✅ **Fix**: "We use Redis for latency, trade-off is memory cost"

❌ **Over-complicating**: "We need 20 services"
✅ **Fix**: Start with 3-4, scale when needed

❌ **Not handling failures**: "It just works"
✅ **Fix**: "If DB fails, we serve from cache with stale data"

---

## Database Decision Tree

```
Need ACID transactions?
├─ YES → SQL (PostgreSQL, MySQL)
└─ NO → Need horizontal write scaling?
         ├─ YES → NoSQL (DynamoDB, Cassandra)
         └─ NO → Need complex queries?
                  ├─ YES → SQL
                  └─ NO → NoSQL or Key-Value (Redis)
```

---

## Caching Decision Tree

```
Read-heavy workload?
├─ YES → What's the consistency requirement?
│        ├─ Strong → Cache-aside with short TTL
│        └─ Eventual → Cache-aside with long TTL
└─ NO → Write-heavy?
         ├─ YES → Write-through or write-behind
         └─ NO → Maybe don't cache
```

---

## Final Checklist Before Interview

- [ ] Can you explain the 11-step framework from memory?
- [ ] Can you draw a three-tier architecture in 30 seconds?
- [ ] Can you explain SQL vs NoSQL trade-offs in 1 minute?
- [ ] Can you calculate storage for 100M users × 1KB/user?
- [ ] Can you explain cache-aside pattern?
- [ ] Can you justify sharding vs read replicas?
- [ ] Can you handle "what if traffic 10x overnight?"

If you answered YES to all, you're ready. Good luck!

---

**Remember**: Interviewers care more about your **thinking process** and **trade-off decisions** than perfect solutions. Show your work, explain your reasoning, and you'll do great.

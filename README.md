# 🧠 MAANG System Design Playbook (2026 Edition)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Interview Ready](https://img.shields.io/badge/Interview-Ready-blue.svg)]()

> **Written from the perspective of a Senior Staff Engineer who has interviewed 500+ MAANG candidates.**

This repository is a **high‑signal, interview‑first system design playbook** for engineers targeting **MAANG‑level roles in 2026**.

This is **not** a textbook.
This is **how to THINK, DECIDE, and COMMUNICATE** in real interviews.

---

## 🎯 Who This Is For

- Engineers with 2–10+ years of experience
- Preparing for **MAANG / Big Tech / Unicorn** system design rounds
- Tired of vague, academic explanations

---

## 🧠 How MAANG Interviews Actually Work (2026)

Interviewers do **not** care if you remember every component.
They care if you can:

- Ask the _right clarifying questions_
- Make _explicit trade‑offs_
- Justify decisions under constraints
- Communicate like a senior engineer

This repo trains exactly that.

---

## 📁 Repository Structure

```
maang-system-design-playbook/
│
├── README.md
│
├── fundamentals/
│   ├── scalability-basics.md
│   ├── latency-vs-throughput.md
│   ├── consistency-models.md
│   └── capacity-estimation.md
│
├── interview-frameworks/
│   ├── maang-interview-flow.md
│   ├── how-to-ask-clarifying-questions.md
│   └── how-to-explain-tradeoffs.md
│
├── components/
│   ├── load-balancers.md
│   ├── databases.md
│   ├── caches.md
│   ├── message-queues.md
│   └── cdn.md
│
├── tradeoffs/
│   ├── sql-vs-nosql.md
│   ├── push-vs-pull.md
│   ├── sync-vs-async.md
│   └── polling-vs-streaming.md
│
├── diagrams-as-text/
│   ├── common-architecture-patterns.md
│
└── case-studies/
    ├── url-shortener.md
    ├── chat-system.md
    ├── rate-limiter.md
    ├── notification-system.md
    ├── file-storage.md
    ├── news-feed.md
    └── search-autocomplete.md
```

---

## 🧩 Mandatory Case Study Format (Used Everywhere)

Every system design topic follows **this exact interview‑proven structure**:

1. Problem Statement (interviewer style)
2. Clarifying Questions
3. Requirements
   - Functional
   - Non‑Functional

4. Scale Assumptions
5. High‑Level Architecture
6. Core Components
7. Data Flow
8. Bottlenecks
9. Trade‑offs
10. How to Explain This in an Interview
11. Common Mistakes

---

## 🧪 Sample Case Study

# 🔗 URL Shortener (2026 MAANG Edition)

## 1. Problem Statement

Design a system like **bit.ly** that shortens long URLs and redirects users at scale.

---

## 2. Clarifying Questions (Ask First)

- Expected read vs write ratio?
- Custom aliases required?
- URL expiration needed?
- Global or regional traffic?

---

## 3. Requirements

### Functional

- Generate short URLs
- Redirect short URL → original URL
- Handle collisions

### Non‑Functional

- Low latency redirects (<50ms)
- Highly available
- Horizontally scalable

---

## 4. Scale Assumptions

- 100M URLs/day
- 10:1 read/write ratio
- Peak QPS: ~15K writes, ~150K reads

---

## 5. High‑Level Architecture

```
Client → Load Balancer → API Service
                       → Cache (Redis)
                       → Database
```

---

## 6. Core Components

- API Service
- Hash / ID Generator
- Cache (Redis)
- Persistent Store (NoSQL)

---

## 7. Data Flow

**Write Flow**

1. Client sends long URL
2. Generate unique ID
3. Store mapping
4. Return short URL

**Read Flow**

1. Client hits short URL
2. Check cache
3. Fallback to DB
4. Redirect

---

## 8. Bottlenecks

- ID generation collisions
- Cache misses
- Hot keys

---

## 9. Trade‑offs

- Base62 vs Hashing
- SQL vs NoSQL
- Cache eviction strategy

---

## 10. How to Explain This in an Interview

> "I optimize for read latency using cache because traffic is read‑heavy. I accept eventual consistency for better scalability."

This sentence matters more than the diagram.

---

## 11. Common Mistakes

- Skipping scale assumptions
- Not justifying database choice
- Forgetting cache invalidation

---

## 🚀 How to Use This Repo

**For Interview Prep (Recommended Path):**

1. **Start Here**: Read `interview-frameworks/maang-interview-flow.md` to understand the 45-minute structure
2. **Learn the Format**: Memorize the 11-step framework (Problem → Clarifying → Requirements → ... → Common Mistakes)
3. **Master Fundamentals**: Read all files in `fundamentals/` to build your foundation
4. **Study Components**: Understand `components/` (load balancers, databases, caches, etc.)
5. **Practice Case Studies**: Work through `case-studies/` one by one, speaking your answers aloud
6. **Internalize Trade-offs**: Study `tradeoffs/` to learn decision-making frameworks
7. **Simulate Interviews**: Pick a random case study, set a 45-minute timer, and design it end-to-end

**Pro Tips:**

- Practice **speaking answers aloud** — writing is not enough
- Focus on **trade‑offs, not just components** — this is what separates senior engineers
- Use the **numbered 1-11 format** for every system design problem
- Time yourself — 45 minutes goes fast in real interviews
- **Print out [QUICK-REFERENCE.md](QUICK-REFERENCE.md)** and keep it next to you during practice

---

## 🏁 Final Note

This playbook is optimized for **MAANG interviews in 2026** — where clarity, decision‑making, and communication matter more than buzzwords.

If this helps you crack your dream company, ⭐ the repo and pass it forward.

Good luck — think like a Staff Engineer.

---

## 📚 Additional Resources

**Quick Links:**

- [QUICK-REFERENCE.md](QUICK-REFERENCE.md) — Print this for practice sessions
- [PRACTICE-CHECKLIST.md](PRACTICE-CHECKLIST.md) — Track your progress
- [CONTRIBUTING.md](CONTRIBUTING.md) — Help improve this playbook
- [LICENSE](LICENSE) — MIT License

**Recommended Reading:**

- Designing Data-Intensive Applications by Martin Kleppmann
- System Design Interview by Alex Xu (Volumes 1 & 2)
- AWS Well-Architected Framework

**Practice Platforms:**

- [Pramp](https://www.pramp.com/) — Free mock interviews
- [Interviewing.io](https://interviewing.io/) — Anonymous practice
- [Exponent](https://www.tryexponent.com/) — System design courses

---

## 🤝 Contributing

Found a mistake? Want to add a case study? See [CONTRIBUTING.md](CONTRIBUTING.md).

This is a community-driven project. PRs are welcome!

---

## ⭐ Star History

If this repo helped you land your dream job, consider:

1. ⭐ Starring the repo
2. 🔄 Sharing it with friends preparing for interviews
3. 💬 Opening an issue to share your success story

---

## 📝 License

MIT License - see [LICENSE](LICENSE) for details.

---

**Built with ❤️ by engineers, for engineers preparing for MAANG interviews.**

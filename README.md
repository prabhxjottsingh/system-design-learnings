# 📚 system-design-learnings

My personal knowledge base for **System Design** — notes, summaries, and takeaways from videos, blogs, and books I study, written in my own words so the concepts actually stick.

> The goal isn't to collect resources, it's to _understand_ them. Every note here is something I've watched/read end-to-end and distilled.

---

## 🗂️ Repository Structure

Each folder is a broad topic area. Inside, every `.md` file covers one concept — with a TL;DR at the top, detailed notes, trade-offs, and a link back to the original source.

```
system-design-learnings/
├── Databases Concepts/
│   └── Sharding and Partitioning.md
├── Designing Data Intensive Applications/
│   └── Chapter 1/
│       ├── README.md
│       └── images/
├── Fundamentals/
│   └── How to Approach System Design.md
└── README.md
```

## 📖 Topics Covered

### Fundamentals

| Note                                                                                      | What it covers                                                                                                                                                                                                                    | Source                                                                           |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [How to Approach System Design](./Fundamentals/How%20to%20Approach%20System%20Design.md) | Two practical approaches to any design problem — the Spiral Approach and the Incremental MVP Approach — plus three pointers (fence the scope, seek clarifications, ask critical questions) to keep any design discussion crisp | [Arpit Bhayani — Asli Engineering](https://www.youtube.com/watch?v=1r9bPisYaOQ) |

### Databases Concepts

| Note                                                                                 | What it covers                                                                                                                                                                            | Source                                                                          |
| ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| [Sharding and Partitioning](./Databases%20Concepts/Sharding%20and%20Partitioning.md) | How databases scale from a single server to horizontal scaling; the real difference between sharding (splitting across servers) and partitioning (splitting the data); trade-offs of each | [Arpit Bhayani — Asli Engineering](https://www.youtube.com/watch?v=wXvljefXyEo) |

### Designing Data-Intensive Applications (book read-through)

| Note                                                                                                       | What it covers                                                                                                                                                     | Source                                                                    |
| ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [Chapter 1 — Chai aur Book Reading (Live Notes)](./Designing%20Data%20Intensive%20Applications/Chapter%201/README.md) | What "data-intensive" really means, front-end/back-end & stateless architecture, OLTP vs. OLAP, data warehouses & ETL & the data engineer role, an intro to distributed systems via IRCTC's overselling problem, and data privacy/compliance law (GDPR, DPDP, SOC2, HIPAA) | [Chai aur Book Reading — Chai aur Code](https://www.youtube.com/watch?v=mSeGdryJdcc) |

_(More topics coming as I go — caching, message queues, load balancing, consistent hashing, etc.)_

## 📝 Note Format

Every note follows the same structure:

1. **TL;DR** — the concept in 3-4 bullets
2. **Detailed notes** — section-by-section breakdown
3. **Advantages / Disadvantages** — trade-offs, because system design is all about trade-offs
4. **Source + timestamps** — so I can revisit the exact part of the video/article

## 🎯 Why This Repo Exists

- Writing notes in my own words forces real understanding, not passive watching
- A single searchable place to revise before interviews
- Tracking my system design journey over time

---

_Maintained by [Prabhjot Singh](https://github.com/prabhxjottsingh) · Suggestions and corrections welcome via issues/PRs._

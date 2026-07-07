# Database Sharding and Partitioning

**Video:** [Database Sharding and Partitioning](https://www.youtube.com/watch?v=wXvljefXyEo) — Arpit Bhayani (Asli Engineering), Apr 2022

---

## TL;DR

- **Partitioning** = splitting data into smaller, mutually exclusive chunks.
- **Sharding** = distributing those chunks across multiple database servers.
- A **database is sharded**; the **data is partitioned**. The terms are often used interchangeably, but they are not the same thing.

---

## 1. How a database is progressively scaled

A database server is just a DB process (MySQL, MongoDB, etc.) running on a machine (e.g., an EC2 instance). Scaling evolves in stages as load grows:

1. **Launch** — a single server comfortably handles the initial load (~100 writes/sec).
2. **Steady growth** — the box starts choking, so you **scale vertically**: more CPU, RAM, and disk. Now it handles ~200 WPS.
3. **Read-heavy growth** — add a **read replica** and divert read traffic to it, leaving the primary free to absorb writes.
4. **Viral growth** — load jumps 5x (~1000 WPS). Scale up vertically again.
5. **Insane growth** — you need ~1500 WPS, but the cloud console has no bigger instance to offer. **Vertical scaling has a hard ceiling.**

## 2. Scaling beyond vertical limits (horizontal scaling)

- One server maxes out at ~1000 WPS, but you need 1500 WPS.
- Solution: split the data into two halves across **two database servers**. Each server _owns_ its half of the data, and all writes for that data go only to that instance.
- Each server now sees ~750 WPS — well within its capacity.
- Adding more servers this way lets total throughput exceed what any single machine could ever handle.

## 3. Sharding vs Partitioning — the actual difference

| Concept             | What it means                                                                    |
| ------------------- | -------------------------------------------------------------------------------- |
| **Partition**       | A logical, mutually exclusive subset of the data                                 |
| **Shard**           | A physical database server that hosts one or more partitions                     |
| **Key distinction** | Partitions can live inside a _single_ DB instance; shards are _separate_ servers |

- Partitioning answers: _how do we split the data?_
- Sharding answers: _how do we spread that data across machines?_
- **Vertical partitioning** splits by columns/tables; **horizontal partitioning** splits by rows (this is what typically gets distributed across shards).

## 4. Partitions and shards are independent (many-to-few mapping)

You don't need a 1:1 mapping between partitions and shards:

- Example: 100 GB of data split into **5 partitions**, hosted on **2 shards** → one shard owns 3 partitions, the other owns 2.
- More partitions than shards gives flexibility: as load grows, you can _move_ partitions to new shards instead of re-splitting the data.
- A single server holding the full dataset in one piece is technically 1 shard with 1 partition.

## 5. Advantages and disadvantages

### Advantages of sharding

- Handles **more reads and writes** than any single machine could
- **Increases total storage capacity** of the system
- Improves **overall availability** — one shard going down doesn't take everything with it

### Disadvantages of sharding

- **Operationally complex** — rebalancing, routing, backups, and monitoring all get harder
- **Cross-shard queries are very expensive** — joins/aggregations spanning shards require scatter-gather across the network

### Practical takeaway

Don't introduce this complexity prematurely. Exhaust vertical scaling and read replicas first; shard only when a single node genuinely can't keep up.

---

## Video outline (timestamps)

| Time  | Topic                                        |
| ----- | -------------------------------------------- |
| 00:00 | Introduction and agenda                      |
| 03:05 | How a database is progressively scaled       |
| 08:10 | Scaling beyond the limit of vertical scaling |
| 11:57 | Sharding vs Partitioning                     |
| 12:43 | Example of data partitioning                 |
| 17:15 | Sharding and partitioning together           |
| 20:20 | Advantages and disadvantages                 |

## Related resources

- Arpit's blog: [Data partitioning strategies (range vs hash)](https://arpitbhayani.me/blogs/some-data-partitioning-strategies-for-distributed-data-stores/)
- Arpit's blog: [Local vs Global indexes on partitioned data](https://arpitbhayani.me/blogs/how-indexes-work-on-partitioned-and-sharded-data/)

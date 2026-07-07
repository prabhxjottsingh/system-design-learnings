# How to Approach System Design

**Video:** [How to approach System Design?](https://www.youtube.com/watch?v=1r9bPisYaOQ) — Arpit Bhayani (Asli Engineering), Apr 2022

---

## TL;DR

- System Design = translating **customer needs and business requirements** into something tangible — an application, a microservice, a library, or even hardware.
- There are two practical approaches: the **Spiral Approach** (build outward from a core you know well) and the **Incremental MVP Approach** (start with a Day 0 design, find bottlenecks, iterate).
- Whichever approach you pick, three pointers keep the discussion crisp: **fence the scope**, **seek clarifications**, and **ask critical questions** that challenge design decisions.

---

## 1. What System Design actually is

- It is not about drawing boxes — it's about solving a real customer/business problem with a tangible system.
- The output can take many forms: a full application, a microservice, a shared library, or hardware.
- Which design approach you use depends on the company you work at and how much flexibility it gives you (e.g., a startup shipping fast vs. a large org investing in upfront architecture).

## 2. The Spiral Approach

- Start with a **core component you are confident about** — the database, the communication protocol, a queue, etc.
- Build the system **outward around that core**, like a spiral, layer by layer.
- Every new component you add is something you understand well, so you can confidently handle the complexity it introduces.
- Works well when you have strong conviction about one central piece of the system and want the rest of the design to grow around it.

## 3. The Incremental MVP Approach

- Start with a bare-bones **Day 0 design** — just enough to serve the requirement.
- **Dry-run each component at scale**: mentally simulate what happens when traffic/data grows and identify which component breaks first.
- Fix the bottleneck, then **re-iterate**. Stop when you're happy with the final design.
- Typical evolution of a system under this approach:
  1. Day 0: users → API servers → DB
  2. Add a load balancer and more API servers
  3. Add a read replica on the DB to support more reads
  4. Split the service into a couple of microservices
  5. Partition the DB to handle more scale
- This approach is common in **startups** that don't want to over-invest in architecture upfront and prefer rolling out features quickly.

## 4. Three key pointers while designing any system

1. **Every system is infinitely buildable — fence it well.** You can keep adding features and components forever; explicitly scope what you're designing (and what you're not) so the discussion stays focused.
2. **Seek clarifications.** Don't design against assumptions — ask your seniors (or interviewer) to clarify requirements before committing to decisions.
3. **Ask critical questions that challenge design decisions.** Interrogate your own choices — why this database, why this protocol, what breaks at 10x — instead of accepting the first design that works.

### Interview takeaway

Stick to the functional requirements agreed upon at the start. Don't burn time designing components (e.g., an analytics service) that were never in scope — depth on the agreed scope beats breadth on everything.

---

## Video outline (timestamps)

| Time  | Topic                                         |
| ----- | --------------------------------------------- |
| 00:00 | Introduction — what System Design is          |
| —     | The Spiral Approach                           |
| 07:27 | The Incremental MVP Approach                  |
| 09:47 | Key pointers to remember during System Design |

## Related resources

- Companion write-up: [How to approach System Design? — Arpit's newsletter](https://arpit.substack.com/p/how-to-approach-system-design)
- Next in this repo: [Sharding and Partitioning](../Databases%20Concepts/Sharding%20and%20Partitioning.md) — how a database in the Incremental MVP flow is actually scaled

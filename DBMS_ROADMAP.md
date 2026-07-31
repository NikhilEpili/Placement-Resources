# DBMS Interview Prep — Structured Guide

A depth-first walkthrough of the topics SDE interviews actually test. Work through it in order — each section builds on the last. For each topic: **core concept → why it matters → common questions → gotchas**.

---

## 1. Fundamentals & Data Models

**Core concepts**
- DBMS vs RDBMS vs File System
- Three-schema architecture: external, conceptual, internal
- Data independence: logical vs physical
- ER Model: entities, attributes, relationships, cardinality (1:1, 1:N, M:N), weak entities, participation constraints

**Common questions**
- Why use a DBMS over flat files?
- Convert an ER diagram into relational tables (esp. handling M:N relationships and weak entities).
- What's the difference between a strong and weak entity?

**Gotcha:** M:N relationships always need a separate junction/bridge table with both foreign keys (and possibly its own key) — this trips people up in schema design questions.

---

## 2. Keys & Constraints

**Core concepts**
- Super key, candidate key, primary key, alternate key, foreign key, composite key
- Surrogate key vs natural key (when to prefer each)
- Constraints: NOT NULL, UNIQUE, CHECK, DEFAULT, referential integrity

**Common questions**
- Difference between candidate key and primary key?
- Why prefer a surrogate key over a natural key (e.g., email as PK)?
- What happens on DELETE/UPDATE with foreign keys — explain CASCADE, SET NULL, RESTRICT, NO ACTION.

---

## 3. Normalization

**Core concepts**
- Functional dependencies (X → Y)
- 1NF (atomic values), 2NF (no partial dependency), 3NF (no transitive dependency), BCNF (every determinant is a candidate key)
- Denormalization — when and why you'd intentionally break normal form (read-heavy systems, reporting/analytics)

**Common questions**
- Given a table with anomalies (insertion/update/deletion), identify which normal form it violates and fix it.
- Difference between 3NF and BCNF (classic trick question — give an example where a table is in 3NF but not BCNF).
- When would you denormalize a production schema?

**Gotcha:** Interviewers love giving you a messy table and asking you to normalize it step by step — practice this hands-on, not just definitions.

---

## 4. SQL Deep Dive

**Core concepts**
- Joins: INNER, LEFT, RIGHT, FULL OUTER, SELF, CROSS — and what happens with NULLs in each
- Subqueries vs correlated subqueries vs CTEs
- Window functions: RANK, DENSE_RANK, ROW_NUMBER, LAG/LEAD, running totals
- GROUP BY + HAVING vs WHERE
- Set operations: UNION vs UNION ALL, INTERSECT, EXCEPT
- Views (and updatable views), materialized views

**Common questions**
- Find the 2nd/Nth highest salary (multiple approaches: subquery, window function, LIMIT/OFFSET).
- Find duplicate rows in a table.
- Employees earning more than their manager (self-join).
- Difference between RANK() and DENSE_RANK() when there are ties.
- Difference between WHERE and HAVING.
- Difference between a view and a materialized view (refresh behavior, storage).

**Practice tip:** Don't just memorize syntax — be ready to write these on a whiteboard/editor without autocomplete. This is usually the highest-weight section in interviews.

---

## 5. Transactions & ACID

**Core concepts**
- Atomicity, Consistency, Isolation, Durability — with a concrete example for each
- Transaction states: active, partially committed, committed, failed, aborted
- Schedules: serial vs concurrent, serializability (conflict vs view serializability)

**Common questions**
- Explain ACID with a bank transfer example.
- What is a serializable schedule and why does it matter?
- Difference between COMMIT and CHECKPOINT?

---

## 6. Concurrency Control

**Core concepts**
- Problems: dirty read, non-repeatable read, phantom read, lost update
- Isolation levels: Read Uncommitted, Read Committed, Repeatable Read, Serializable — which problems each prevents
- Locking: shared vs exclusive locks, 2PL (two-phase locking), deadlocks
- Optimistic vs pessimistic concurrency control
- MVCC (Multi-Version Concurrency Control) — how Postgres/MySQL InnoDB actually implement isolation without heavy locking

**Common questions**
- Map each isolation level to which anomalies it allows/prevents (make a mental table).
- What is a deadlock and how is it detected/resolved (wait-for graph, timeout)?
- Explain MVCC — why does it let readers not block writers?
- Optimistic vs pessimistic locking — when would you choose each?

**Gotcha:** "What isolation level prevents phantom reads?" (Serializable — and only some DBs enforce true serializability by default; MySQL's Repeatable Read actually prevents phantoms via gap locks, which is a common follow-up trap.)

---

## 7. Indexing & Storage

**Core concepts**
- B-Tree vs B+ Tree (why B+ Tree is preferred for disk-based DBs — all data at leaf level, linked leaves for range queries)
- Clustered vs non-clustered index
- Composite indexes and column order (leftmost prefix rule)
- Hash index vs B-tree index — when each is better
- Covering index
- How indexes speed up reads but slow down writes (insert/update/delete overhead)

**Common questions**
- Why B+ Tree over B-Tree for databases?
- Difference between clustered and non-clustered index — how many of each can a table have?
- If you have an index on (a, b, c), does a query filtering only on `b` use it? (No — leftmost prefix rule.)
- How does adding an index affect INSERT/UPDATE performance?

---

## 8. Query Processing & Optimization

**Core concepts**
- Query execution plan / EXPLAIN output
- Join algorithms: nested loop, hash join, sort-merge join — when the optimizer picks each
- Cost-based optimization basics
- Common performance killers: missing indexes, SELECT *, functions on indexed columns in WHERE, implicit type conversion

**Common questions**
- How would you debug a slow query? (Walk through EXPLAIN, look for full table scans, check indexes.)
- Why does `WHERE YEAR(date_col) = 2024` not use an index on `date_col`?

---

## 9. Transactions in Distributed Systems (good to know, often asked at mid-senior level)

**Core concepts**
- CAP theorem (Consistency, Availability, Partition tolerance — pick 2 during a partition)
- 2PC (two-phase commit) — coordinator/participant flow, blocking problem
- Sharding vs replication, read replicas
- Eventual consistency vs strong consistency

**Common questions**
- Explain CAP theorem with a real system example (e.g., DynamoDB is AP, traditional RDBMS is CP).
- How does sharding differ from partitioning within a single DB?

---

## 10. SQL vs NoSQL

**Core concepts**
- When to choose NoSQL (schema flexibility, horizontal scale, high write throughput) vs SQL (strong consistency, complex joins/transactions)
- Types: key-value, document, column-family, graph — one example DB each
- BASE vs ACID

**Common questions**
- Design a schema for [X] — would you use SQL or NoSQL and why?
- What is denormalization's role in NoSQL document design (embedding vs referencing)?

---

## Suggested Study Order (given you know basics, want depth)

1. **Days 1–2:** Normalization + Keys (nail this cold — it's foundational and shows up as a discussion + practical exercise)
2. **Days 3–4:** SQL deep dive — actually write queries daily (LeetCode Database section, HackerRank SQL)
3. **Days 5–6:** Transactions, ACID, Isolation levels, Concurrency control (this is where "know basics" candidates usually get exposed — go deep here)
4. **Day 7:** Indexing & query optimization
5. **Day 8:** Distributed systems basics + SQL vs NoSQL (lighter, conceptual)
6. **Day 9–10:** Mixed mock questions, whiteboard practice, revisit weak spots

---

## How I can help next
- Drill you with rapid-fire Q&A on any section above
- Give you SQL problems to solve live and review your queries
- Do a mock interview round (I ask, you answer, I critique)
- Explain any topic above in more depth with diagrams

Just tell me where you want to start.
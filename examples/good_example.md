# Example: Database Selection Decision Support

This is a reference report generated using the `decision-lens` framework with the **Endnote Citation System**.

## 1. Research Scope & Parameters

### 1.1 Hard Constraints
- **Constraint 1**: Must support distributed horizontal scaling.
- **Constraint 2**: Must be open-source with OSI-compliant licensing.

### 1.2 Initial Candidate Screening
Scanned initial candidates via GitHub Topics `topic:database` [^1] and DB-Engines rankings [^2].
*(Note: Single-node databases like SQLite were silently excluded for failing Constraint 1).*

---

## 2. Domain Cognitive Map

### 2.1 One-Sentence Definition
Selecting an optimal database architecture under high-throughput write workloads and strict availability requirements [^3].

### 2.2 Core Tension Model
**Consistency vs. Availability (CAP Theorem)**
Distributed databases must make explicit trade-offs between strong data consistency and high system availability during network partitions [^4].

---

## 3. Deep-Dive Candidate Specifications

### Option A: Apache Cassandra
- **Architecture**: Peer-to-peer ring topology with no single point of failure [^5].
- **Customization & Setup**: Supports CQL interface, tuneable consistency levels per query [^6].
- **Multi-Node Mechanics**: Automatic data sharding via consistent hashing [^7].

---

## 4. Option Comparison Matrix & Weighted Scoring

### 4.1 Option Comparison Matrix

| Factor | Cassandra | MongoDB |
|--------|-----------|---------|
| Overview | Distributed wide-column NoSQL [^5] | Document-oriented NoSQL [^8] |
| Core Advantage | Exceptional write throughput [^9] | Flexible JSON schema [^10] |
| Critical Flaw | Complex tombstone & compaction tuning [^11] | High operational cost for sharding [^12] |

### 4.2 Transparent Weighted Scoring Matrix

| Key Variable | Weight | Weight Origin | Cassandra | MongoDB |
|--------------|--------|---------------|-----------|---------|
| Write Throughput | 50% | User Spec | 5 | 3 |
| Operational Ease | 30% | Team Size | 2 | 5 |
| ACIDs / Transactions | 20% | Use Case | 1 | 4 |
| **Weighted Score** | | | **3.3** | **3.8** |

---

## 5. Decision Guidance
- If extreme write throughput is the primary bottleneck → Choose Cassandra.
- If rapid iteration and rich querying matter more under moderate write pressure → Choose MongoDB.

---

## 6. References & Endnotes

[^1]: [GitHub Topic: Database](https://github.com/topics/database) - Primary open-source database topic listing.
[^2]: [DB-Engines Ranking](https://db-engines.com/en/ranking) - Official DBMS popularity and category index.
[^3]: [ACM SIGMOD Overview on Modern Storage Systems](https://dl.acm.org) - Database classification paper.
[^4]: [Brewer's CAP Theorem Proof (Lynch et al.)](https://glassbeam.com/wp-content/uploads/2017/04/Brewer-CAP-Theorem.pdf) - Formal CAP theorem paper.
[^5]: [Cassandra Ring Topology Paper (Facebook 2010)](https://www.cs.cornell.edu/projects/ladis2009/papers/lakshman-ladis2009.pdf) - Original Cassandra whitepaper.
[^6]: [Cassandra Query Language (CQL) Guide](https://cassandra.apache.org/doc/latest/cassandra/cql/) - Protocol specifications.
[^7]: [Consistent Hashing in Distributed Systems](https://dl.acm.org/doi/10.1145/258533.258660) - Consistent hashing paper.
[^8]: [MongoDB Licensing & Core Overview](https://www.mongodb.com/licensing/server-side-public-license) - SSPL open-core model details.
[^9]: [Apache Cassandra Architecture Docs](https://cassandra.apache.org/_/doc/latest/cassandra/architecture/) - Details on write path and ring topology.
[^10]: [MongoDB Document Model Manual](https://www.mongodb.com/docs/manual/core/document/) - Schema flexibility details.
[^11]: [Cassandra Compaction Pitfalls & Tombstone Issues](https://cassandra.apache.org/doc/latest/cassandra/operating/compaction/) - Official troubleshooting guide.
[^12]: [MongoDB Sharding Complexity & Operational Costs](https://www.mongodb.com/docs/manual/sharding/) - Production operational manual.

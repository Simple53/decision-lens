# Example: Database Selection Decision Support

This is a reference report generated using the `decision-lens` Skill.

## 1. Domain Cognitive Map

### One-Sentence Definition
Selecting an optimal database architecture under high-throughput write workloads and strict availability requirements.

### Core Tension Model
**Consistency vs. Availability (CAP Theorem)**
Distributed databases must make explicit trade-offs between strong data consistency and high system availability during network partitions.

### Key Variables vs. Marketing Noise
- **Key Variables**: Write throughput ceiling, partition tolerance, operational complexity, schema flexibility.
- **Marketing Noise**: Serverless billing buzzwords.

## 2. Option Comparison Matrix

| Factor | Cassandra | MongoDB |
|--------|-----------|---------|
| Overview | Distributed wide-column NoSQL | Document-oriented NoSQL |
| Core Advantage | Exceptional write throughput | Flexible JSON schema |
| Critical Flaw | Complex tombstone & compaction tuning | High operational cost for sharding |
| References | [Official Docs](https://cassandra.apache.org) | [Official Docs](https://www.mongodb.com) |

## 3. Decision Assistance (Weighted Scoring)

| Key Variable | Weight | Weight Origin | Cassandra | MongoDB |
|--------------|--------|---------------|-----------|---------|
| Write Throughput | 50% | User Spec | 5 | 3 |
| Operational Ease | 30% | Team Size | 2 | 5 |
| ACIDs / Transactions | 20% | Use Case | 1 | 4 |
| **Weighted Score** | | | **3.3** | **3.8** |

## 4. Conditional Guidance
- If extreme write throughput is the primary bottleneck → Choose Cassandra.
- If rapid iteration and rich querying matter more under moderate write pressure → Choose MongoDB.

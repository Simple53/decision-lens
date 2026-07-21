# 示例：数据库选型决策支持

这是使用 `decision-lens` 框架生成的示范报告，展示了**静默剔除否决项**与**标准尾注引用系统**的应用。

## 1. 研究边界与筛选参数

### 1.1 硬性条件 (Hard Constraints)
- **硬性条件 1**：必须支持横向扩展（Horizontal Scaling）。
- **硬性条件 2**：必须符合开源或开源核心协议。

### 1.2 初始候选池广度扫描与初筛
扫描来源：GitHub Topics `topic:database` [^1] 与 DB-Engines 数据库排行榜 [^2]。
*(注：单节点架构的 SQLite 因违反硬性条件 1，已在初筛阶段静默剔除，不入表格)*。

---

## 2. 领域认知地图

### 2.1 一句话定义
在海量写入和高可用场景下选择合适的数据库系统 [^3]。

### 2.2 核心张力模型
**一致性 vs 可用性 (CAP定理)**
分布式数据库必须在数据强一致性和系统高可用性之间做出取舍 [^4]。

---

## 3. 核心方案深度技术卡片

### 方案 A：Apache Cassandra
- **架构与形态**：无主节点（Peer-to-Peer）环形拓扑，无单点故障 [^5]。
- **自定义配置**：支持 CQL 交互，可配置查询级别的一致性等级 [^6]。
- **多节点协同**：基于一致性哈希（Consistent Hashing）自动分片 [^7]。

---

## 4. 方案对比矩阵与加权评分

### 4.1 方案维度对比矩阵

| 维度 | Cassandra | MongoDB |
|------|-----------|---------|
| 简述 | 分布式宽列 NoSQL [^5] | 文档型 NoSQL [^8] |
| 核心优势 | 极高的写入性能 [^9] | 灵活的 JSON Schema [^10] |
| 致命弱点 | 复杂的墓碑机制与 Compacting 调优 [^11] | 分片运维成本高 [^12] |

### 4.2 透明加权评分表

| 关键变量 | 权重 | 权重来源 | Cassandra | MongoDB |
|----------|------|----------|-----------|---------|
| 写入性能 | 50% | 需求说明 | 5 | 3 |
| 易用性 | 30% | 团队规模 | 2 | 5 |
| 事务支持 | 20% | 业务场景 | 1 | 4 |
| **加权总分**| | | **3.3** | **3.8** |

---

## 5. 决策提示与动作建议
- 如果极限吞吐量是唯一瓶颈 → 选 Cassandra。
- 如果需要快速迭代且写入压力一般 → 选 MongoDB。

---

## 6. 参考文献与索引 (References)

[^1]: [GitHub Topic: Database](https://github.com/topics/database) - 开源数据库项目汇总列表。
[^2]: [DB-Engines Ranking](https://db-engines.com/en/ranking) - 全球数据库流行度与分类索引。
[^3]: [ACM SIGMOD Storage Survey](https://dl.acm.org) - 现代存储系统分类研讨论文。
[^4]: [Brewer's CAP Theorem Proof](https://glassbeam.com/wp-content/uploads/2017/04/Brewer-CAP-Theorem.pdf) - 证明分布式一致性取舍的学术论文。
[^5]: [Facebook Cassandra Paper (2010)](https://www.cs.cornell.edu/projects/ladis2009/papers/lakshman-ladis2009.pdf) - Cassandra 创世论文。
[^6]: [Cassandra CQL Reference](https://cassandra.apache.org/doc/latest/cassandra/cql/) - 协议与一致性等级说明。
[^7]: [Consistent Hashing Paper](https://dl.acm.org/doi/10.1145/258533.258660) - 一致性哈希算法论文。
[^8]: [MongoDB Licensing Guide](https://www.mongodb.com/licensing/server-side-public-license) - SSPL 协议与文档模型详解。
[^9]: [Apache Cassandra Architecture Docs](https://cassandra.apache.org/_/doc/latest/cassandra/architecture/) - 官方写入路径与拓扑架构说明。
[^10]: [MongoDB Document Model Manual](https://www.mongodb.com/docs/manual/core/document/) - Schema 灵活性说明。
[^11]: [Cassandra Compaction Pitfalls](https://cassandra.apache.org/doc/latest/cassandra/operating/compaction/) - 官方运维排坑指南。
[^12]: [MongoDB Sharding Architecture](https://www.mongodb.com/docs/manual/sharding/) - 分片运维复杂度说明。

---
name: decision-lens-zh
description: 深度领域研究与决策支持（中文规范版 V1.2.0）。包含真实 Python 生成 Excel (.xlsx) 文档导出能力、金字塔结构领域解析、专有名词词典板块、真实长 URL [1] 数字超链接规程、全量候选池表格、10-15 主对比矩阵与硬性否决机制。
---

# 领域研究与决策支持工作流

## 核心定位

**AI 负责：** 明确硬性筛选条件、全量扫描候选池、**运行 Python 脚本生成可下载的真实 Excel (.xlsx) 文档**、编写**金字塔结构领域解析**与**专有名词词典板块**、在正文和文末使用**真实精确的长 URL 数字超链接 `[1]`**（严禁只使用主页域名）、在 Phase 1 强制调用系统提问/暂停工具等待用户确认、编写方案对比矩阵与深度技术卡片。

**AI 默认不负责：** 推荐最佳方案、替用户做价值取舍。如果用户明确要求推荐，可以给出带理由的倾向性建议，但必须标注"这是基于当前证据的倾向性判断"。

---

## 铁律

1. **真实 Excel (.xlsx) 文档生成规程 (Python Excel Generation)**：
   - 绝不依赖单纯的 Markdown 表格。
   - AI **必须编写并运行 Python 脚本**（使用 `pandas` / `openpyxl`），在 Artifacts 目录下生成包含全量候选池与加权评分矩阵的真实可下载 `.xlsx` Excel 文件（如 `domain_research_<topic>_candidates.xlsx`）。
   - 在 Artifact 报告中提供可直接点击下载/打开的绝对路径超链接 `[下载全量 Excel 表格](file:///path/to/file.xlsx)`。
2. **金字塔领域结构解析与专有名词词典 (Pyramid Structure & Terminology Glossary)**：
   - 报告中必须设立独立的 **【领域金字塔结构解析】** 章节，采用芭芭拉·金字塔原理（顶层目标 → 中层核心机制/分类 → 底层基础设施/技术栈）进行系统性剖析。
   - 报告中必须设立独立的 **【核心专有名词字典】** 章节，集中列出该领域的所有专业缩写、术语及技术名词解释（如：VLM, MCP, BYOK, TUI, Docked Sandbox, Headless Browser 等）。
3. **真实精确长 URL 数字超链接系统 [1] (Exact Specific URL Citations)**：
   - 正文中全量使用方括号数字 **`[1]`**、**`[2]`** 作为引用角标（替换 `[^1]`）。
   - **绝不允许使用泛泛的根主页域名**（如 `https://bilibili.com` 或 `https://youtube.com`）！文末参考文献必须使用 `search_web` 或 `read_url_content` 返回的**具体文章/视频/仓库的完整精确长 URL**（如包含视频 BV 号或文章 Path 的真实链接）：
     ```markdown
     [1] [B站实测视频: OpenCode桌面版部署教程](https://www.bilibili.com/video/BV1xx411c7xx) - 详细测试说明
     [2] [GitHub 仓库: Agent-Zero](https://github.com/agent0ai/agent-zero) - 官方源码说明
     ```
4. **无限制候选池扫描与全量表格 (Unconstrained Pool & Full Table)**：
   - 在 Artifact 报告中，必须以类 Excel 格式的 Markdown 大表格输出**所有扫描到的候选项目全量清单**，列出项目名称、软件形态、Hard Constraint 否决/通过状态及判定原因。
5. **正文与矩阵保留 10–15 个核心方案 (Top 10–15 Core Candidates)**：
   - 从全量候选池中筛选并保留 **10–15 个最符合条件的核心方案**，深入展开至主方案维度对比表、加权评分表与深度技术剖析卡片中。
6. **硬性条件一票否决 (Hard Constraint Filtering)**：
   - 不符合硬性条件的候选项目在全量表中标注 `[一票否决]`，且不占入主 10-15 个核心方案对比矩阵中。
7. **强制交互暂停等待确认 (Mandatory Interactive Pause)**：
   - 在 Phase 1 完成后，AI **必须调用 `ask_question` 工具**，向用户弹出包含硬性限制、评估权重及动态信源清单的确认菜单。等待用户回复后再启动 Phase 3。
8. **移除装饰性 Note 提示块**：
   - 在生成的 Artifact 报告开篇，**不得添加 `> [!NOTE]` 等装饰性提示块**。
9. **Artifact 为主要载体**：创建 `domain_research_<主题>.md` 作为研究报告，对话框只输出简要摘要和需要用户决策的问题。
10. **评分诚实**：使用 1-5 整数定性评分，杜绝虚假小数精度。

---

## 阶段工作流 (Phases)

### Phase 1：研究边界、动态信源探索与参数锁定
明确 Hard Constraints 与 Soft Preferences；探索发现可靠信源；**强制调用 `ask_question` 工具弹出确认菜单**，等待用户确认。

### Phase 2：候选池扫描、金字塔地图与 Python Excel 文件生成
扫描构建不限数量候选池全量表；**运行 Python 脚本生成 `.xlsx` Excel 文件**；编写**金字塔结构解析**与**专有名词词典**；挑选 10-15 个核心方案。

### Phase 3：定向深挖与真实网页提取 (`read_url_content`)
在用户批准信源内使用独立 `search_web` 检索并调用 `read_url_content` 提取真实长 URL；编写深度技术剖析卡片。

### Phase 4：10-15 核心方案矩阵与透明评分矩阵
构建 10-15 核心方案对比表；构建 1-5 分定性加权评分表。

### Phase 5：决策交付与真实长 URL 索引
交付已知事实、未确定项与验证建议；附带 Excel 文件下载链接；文末输出使用具体精确长 URL 的 `[1] [标题](https://exact-url)` 参考文献列表。

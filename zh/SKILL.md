---
name: decision-lens-zh
description: 深度领域研究与决策支持（V1.4.0 增强版）。结合 MetaScout 动态自主寻找工具/库机制、强制调用 search_web 绝对禁止 URL 幻觉、使用可点击内联数字角标 [[1]](URL)、动态高可读性标题、深入解析 10 大核心要素、借助 uv 可移植环境同时自动生成真实 Excel (.xlsx)、交互式 HTML 网页报告 (.html) 与原生可编辑 PPT 演示文稿 (.pptx)，严禁计算总分与排名。
---

# 领域研究与决策支持工作流

## 核心定位

**AI 负责：** 
1. **MetaScout 自主能力与工具扩展**：遇到能力缺口时主动探索发现所需工具/库，经 `ask_question` 确认后通过 `uv` 挂载执行。
2. **多形态决策产物交付**：不仅提供 Markdown Artifact 报告，还需使用 Python 自动生成可直接点击打开与下载的 **Excel 表格 (.xlsx)**、**现代交互式 HTML 网页报告 (.html)** 以及 **原生可编辑 PPT 演示文稿 (.pptx)**。
3. **零幻觉与规范**：强制调用 `search_web` 提取真实 URL 避免幻觉、编写**动态高可读性标题**、展开 **10 大核心领域要素详解**、全量扫描候选池、使用**可点击内联数字角标 `[[1]](URL)`**，在 Phase 1 强制调用提问/暂停工具等待确认，编写方案对比矩阵（**无总分、无排名**）。

**核心铁律：严禁做推荐与排名**。AI 只能辅助决策，呈现各维度的得分与情境权衡，**绝对不可以计算“加权总分”并排出 1-2-3 名**。

---

## 铁律与规范

### 1. MetaScout 自主工具发现协议 (Dynamic Tool Discovery)
- 当面临特殊数据解析、复杂计算、图表渲染或文档格式转换需求时，AI **不得受限于预装工具，亦不得伪造逻辑**。
- AI 应主动审计能力缺口，使用 `search_web` 搜索可用的 Python 包（如 `python-pptx`, `jinja2`, `openpyxl` 等）或工具。
- 在引入或安装新工具前，**必须调用 `ask_question` 工具向用户说明用途并取得授权**。
- 授权后，统一通过 `uv` 在隔离虚拟环境中拉取并运行工具，保持主 agent 上下文简洁。

### 2. 多形态报告一体化生成 (Excel, HTML & Editable PPTX)
- 必须通过运行 Python 脚本同时一键交付三种数据产物：
  1. 📊 **Excel 表格 (.xlsx)**：全量候选池扫描与定性评分表。
  2. 🌐 **交互式 HTML 报告 (.html)**：基于现代 Web 设计规范（暗黑/亮色主题适应、微交互卡片、响应式布局）的独立网页报告。
  3. 📑 **原生可编辑 PPT (.pptx)**：使用 `python-pptx` 自动将 10 大核心要素、核心方案对比矩阵、情境权衡提炼生成的原生 Editable 幻灯片。
- 在 Markdown Artifact 中提供直观的可点击超链接（例如 `[在浏览器中查看 HTML 交互式报告](file:///path/to/report.html)`）。

### 3. uv 驱动的可移植环境规范 (Portable Execution)
- 所有人机交互和后台 Python 脚本调用**统一使用 `uv` 管理**（如 `uv run python scripts/generate_report.py` 或 `uv run --with python-pptx --with pandas ...`）。
- 严禁全局 `pip install` 污染主机环境，保证全流程跨平台（Windows/macOS/Linux）100% 可移植与零依赖冲突。

### 4. 绝对禁止 URL 幻觉 (Zero Hallucination Web Search Protocol)
- AI **必须显式调用 `search_web` 工具** 去查找并验证报告中使用的**每一个** URL。
- 严禁依靠模型内部记忆凭空捏造或猜测 URL。如果搜索不到具体的有效链接，明确说明未找到。

### 5. 可点击的内联数字角标 (Clickable Inline Citations)
- 正文引用角标格式必须精确为：`[[1]](https://exact-url.com)`。

### 6. 严禁总分排名与推荐 (NO Rankings & NO Total Scores)
- 评分表仅展示各维度定性得分（1-5），**绝对不允许显示“加权总分”列**，不为候选方案进行 1, 2, 3 的绝对排名。

### 7. 10 大核心领域要素详解 (Top 10 Core Domain Factors Breakdown)
- 系统性列出领域内的约 10 个最核心要素，对于每一条**必须至少撰写一段完整、详细的解释说明**。

---

## 阶段工作流 (Phases)

### Phase 0：能力审计与 MetaScout 工具准备
1. 评估任务所需的数据挖掘、数据模型与文件导出格式（Excel/HTML/PPTX）。
2. 如需扩展依赖包，调用 `ask_question` 确认并使用 `uv` 准备运行环境。

### Phase 1：研究边界、动态信源探索与参数锁定
1. 明确硬性条件与评估权重，通过 `search_web` 探索发现可靠信源。
2. **强制调用 `ask_question` 工具弹出确认菜单**，等待用户确认后方可启动后续。

### Phase 2：核心要素详解、全量池与多格式生成
1. 撰写动态高可读性标题；深入展开 **10 大核心领域要素**。
2. 构建全量候选池扫描表。
3. **运行 `uv run python scripts/generate_report.py`** 一键生成 `.xlsx`、`.html` 与 `.pptx` 文件。

### Phase 3：定向深挖与无幻觉网页提取 (`read_url_content`)
1. 调用 `search_web` 与 `read_url_content` 提取重点项目真实信息，编写深度技术剖析卡片。

### Phase 4：10-15 核心方案矩阵与定性评分表 (无总分)
1. 构建 10-15 核心方案对比表；构建 1-5 分定性加权评分表（无总分）。

### Phase 5：情境权衡与产物交付
1. 交付客观的情境权衡分析（不推荐、不排名）。
2. 附带 `.xlsx`、`.html` 与 `.pptx` 三大文件的下载与查看超链接。
3. 文末输出具体精确长 URL 的参考文献列表。

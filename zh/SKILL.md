---
name: decision-lens-zh
description: 深度领域研究与决策支持（V1.4.0 宿主无关协议版）。兼容 Codex、Claude Code、OpenCode、Grok Build、Antigravity 等主流 AI Agent 平台。包含 MetaScout 动态自主工具发现、审批与权限审查、隔离部署与动态回滚、绝对禁止 URL 幻觉、10 大核心要素解析、真实 Excel (.xlsx) + 交互式 HTML (.html) + 可编辑 PPT (.pptx) 一体化导出，严禁计算总分与排名。
---

# 领域研究与决策支持工作流 (Host-Agnostic Protocol V1.4.0)

## 1. 协议设计哲学与能力模型

本 Skill 采用**宿主无关协议 (Host-Agnostic Protocol)** 设计，不依赖特定 Agent 系统的专有 API。适用于包括 **Codex**、**Claude Code**、**OpenCode**、**Grok Build** 以及 **Antigravity** 在内的任何具身/桌面 Agent 系统。

### 宿主能力抽象与映射关系
- **[User Authorization Interface / 宿主交互授权接口]**：对应宿主环境中的交互提问 modal、终端确认或人机对话接口。
- **[Isolated Sandbox / 宿主沙箱执行能力]**：对应宿主环境中的隔离子进程、命令行终端、子代理 (Subagent) 或 Docker/Venv 虚拟环境。
- **[Web Search & Content Fetch / 联网检索能力]**：对应宿主环境中的网页搜索与 URL 内容提取工具。

---

## 2. MetaScout 工具发现与 5 大安全演进流程

在进行深度研究或复杂格式导出时，若发现缺失特定数据解析器、建模库或导出工具（如 `python-pptx`, `pandas`, `openpyxl`, `jinja2`），必须严格遵循以下 **5 大演进流程**：

### 2.1 能力审计 (Capability Audit)
- 分析用户输入的决策分析目标，审查当前环境是否具备处理该任务所需的特殊解析器、提取工具或文件导出引擎。
- 识别具体能力缺口（例如：`需要安装 python-pptx 以生成原生可编辑 PPTX`）。

### 2.2 审批与权限审查 (Approval & Permission Audit Protocol)
- 在安装或运行任何新工具/依赖前，**必须调用 [宿主交互授权接口] 提交审批申请**。
- **审批申请必须明确声明**：
  1. 拟引入的工具/依赖包名称与来源（如 PyPI / GitHub）。
  2. 为什么需要该工具（能力缺口说明）。
  3. 所需权限范围（如：本地 `uv` 虚拟环境文件读写、无高危网络请求）。
- **未获得用户明确授权，绝对禁止私自静默安装或运行未审查工具**。

### 2.3 隔离部署 (Isolated Sandbox Deployment via `uv`)
- 获得授权后，在 [宿主沙箱执行能力] 环境中拉取与部署工具。
- **统一使用 `uv` 隔离环境**（如 `uv run python script.py` 或 `uv run --with <package> python script.py`）。
- 严禁全局 `pip install` 污染宿主系统的全局 Python 环境，实现跨平台 100% 可移植与环境隔离。

### 2.4 任务执行与动态回滚 (Execution & Dynamic Rollback Protocol)
- 在沙箱环境中使用新工具执行任务。
- **异常捕获与回滚机制**：若工具运行报错、依赖冲突或环境异常，AI 必须捕获全量日志，自动触发降级回滚策略：
  - 清理失败的临时构建产物。
  - 降级为基础纯 Markdown 报告与基础 Excel 导出，并在报告中诚实记录工具降级原因，绝不伪造输出。

### 2.5 工具保留与清理 (Tool Retention & Housekeeping Protocol)
- 任务执行完成后，根据用户偏好与环境策略对工具进行处置：
  - **一次性工具**：自动清理临时虚拟环境与 cache。
  - **长期保留工具**：在项目配置（如 `pyproject.toml`）中显式登记保留说明，确保工作区可追踪、洁净无冗余。

---

## 3. 决策支持铁律与规范

### 3.1 绝对禁止 URL 幻觉 (Zero Hallucination Protocol)
- AI **必须显式调用联网检索工具** 去查找并验证报告中使用的**每一个** URL。
- 严禁依靠模型内部记忆凭空捏造或猜测 GitHub 仓库、官方文档的 URL。如果搜索不到具体的有效链接，明确说明未找到。

### 3.2 可点击的内联数字角标 (Clickable Inline Citations)
- 正文引用角标格式必须精确为：`[[1]](https://exact-url.com)`。

### 3.3 严禁总分排名与推荐 (NO Rankings & NO Total Scores)
- 本 Skill 仅用于辅助决策，严禁代替用户做决定！
- 评分表中仅展示各维度定性得分（1-5），**绝对不允许计算、汇总或显示“加权总分”列**。
- 将推荐替换为客观的**情境权衡分析 (Trade-off Analysis)**。

### 3.4 10 大核心领域要素详解 (Top 10 Core Domain Factors)
- 系统性拆解领域内的约 10 个最核心要素，对于每一个要素**必须至少撰写一段完整、详细的解释说明**。

### 3.5 多形态报告一体化交付 (Excel + HTML + Editable PPTX)
- 必须通过运行 Python 脚本同时交付：
  1. 📊 **Excel 表格 (.xlsx)**：全量候选池扫描与定性评分表。
  2. 🌐 **交互式 HTML 网页报告 (.html)**：基于现代 Web 设计规范（自适应暗色主题、微交互卡片、响应式布局）的独立网页报告。
  3. 📑 **原生可编辑 PPT (.pptx)**：利用 `python-pptx` 将 10 大要素与对比矩阵自动提炼生成的原生 Editable 演示文稿。

---

## 4. 阶段工作流 (Phases)

### Phase 0: 能力审计与 MetaScout 审批部署
1. 识别任务所需的数据建模与三形态报告（Excel / HTML / PPTX）导出需求。
2. 遵循 **2.2 审批与权限审查协议** 提交用户授权申请，并使用 `uv` 隔离运行。

### Phase 1: 研究边界、动态信源探索与参数锁定
1. 明确硬性条件与软性偏好；通过检索探索可靠信源。
2. **调用 [宿主交互授权接口] 弹出确认**，等待用户确认边界参数。

### Phase 2: 核心要素详解、全量扫描与多格式生成
1. 编写动态贴合主题的高可读性大标题；撰写 **10 大核心领域要素详解**。
2. 扫描全量候选池；运行 `uv run python scripts/generate_report.py` 一键生成 `.xlsx`、`.html` 与 `.pptx` 文件。
3. 若出现环境异常，触发 **2.4 动态回滚协议** 进行安全降级处理。

### Phase 3: 定向深挖与无幻觉网页提取
1. 对 Top 10-15 核心候选方案进行深度检索提取，撰写技术卡片。

### Phase 4: 对比矩阵与透明定性评分 (无总分)
1. 构建 10-15 核心方案对比矩阵与 1-5 分定性评分表（无总分）。

### Phase 5: 情境权衡与产物清理交付
1. 输出情境权衡分析，提供 `.xlsx`、`.html` 与 `.pptx` 文件的下载/预览链接。
2. 按照 **2.5 工具保留与清理协议** 完成临时资源整理，附带完整验证 URL 参考文献列表。

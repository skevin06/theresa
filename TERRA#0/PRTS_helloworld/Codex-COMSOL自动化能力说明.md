# Codex-COMSOL 自动化能力说明

## 结论

Codex 可以通过本机 COMSOL 命令行和本地 Help/案例库，完成一部分“脚本化、可验证、可迭代”的 COMSOL 建模工作。最适合的方式不是让 Codex 凭记忆直接写复杂模型，而是：

1. 先搜索本机 COMSOL 官方案例库。
2. 再搜索本机 COMSOL Help/PDF 手册。
3. 生成 COMSOL Java API 或 M-file 脚本。
4. 用 COMSOL batch 跑仿真。
5. 读取日志、导出结果，再迭代修正。

当前已配置的 Codex 工具包括：

- `comsol_info`：检查 COMSOL 路径、工作目录、文档目录、案例目录。
- `comsol_example_search`：搜索本机 COMSOL Application Library 案例说明。
- `comsol_read_example`：读取命中的官方案例说明。
- `comsol_doc_search`：搜索本机 COMSOL PDF Help/说明书，并返回页级片段。
- `comsol_batch`：运行 `.java` 或 `.m` 批处理仿真脚本。
- `comsol_run`：运行明确的 COMSOL 命令行参数。

## 已接入的本机资料

- COMSOL 主程序：
  `C:\Program Files\COMSOL\COMSOL64\Multiphysics\bin\win64\comsol.exe`

- COMSOL 工作目录：
  `C:\Users\admin\Desktop\comsol-workdir`

- 官方案例库：
  `C:\Program Files\COMSOL\COMSOL64\Multiphysics\applications`

- Help/PDF 说明书：
  `C:\Program Files\COMSOL\COMSOL64\Multiphysics\doc\pdf`

- PDF 文本缓存：
  `C:\Users\admin\Desktop\comsol-workdir\.codex-comsol-cache`

本机案例库中已观察到大量官方资源，包括约 2081 个 `.mph` 文件和约 1700 个 `.txt` 案例说明。核心说明书包括：

- `ApplicationProgrammingGuide.pdf`
- `COMSOL_ProgrammingReferenceManual.pdf`
- `COMSOL_ReferenceManual.pdf`
- 各模块 Users Guide，例如 Heat Transfer、ACDC、CFD、RF、Wave Optics 等。

## Codex 擅长完成的 COMSOL 功能

### 1. 从需求生成最小可运行模型

适合任务：

- 简单几何建模。
- 参数化尺寸和材料。
- 基础物理场设置。
- 基础边界条件。
- 粗网格和初始求解。
- 保存 `.mph` 文件。

依据：

- COMSOL Java API 可脚本化创建参数、几何、材料、物理场、网格、研究和结果。
- Codex 可以通过 `comsol_doc_search` 查 API 片段，通过 `comsol_batch` 验证脚本是否能运行。

### 2. 官方案例改造

适合任务：

- 根据官方案例修改参数。
- 将类似案例迁移到新的尺寸、材料或边界条件。
- 从案例说明中提取建模步骤。
- 复用案例的物理场和求解器思路。

依据：

- 本机 `applications` 目录包含大量模块化官方案例。
- `comsol_example_search` 能先找到相近案例，降低 API 和物理场 tag 猜错概率。

### 3. 参数扫描和批量仿真

适合任务：

- 批量改变几何参数、材料参数或边界载荷。
- 导出 CSV、表格、关键指标。
- 自动保存多组结果。
- 根据日志判断哪组失败。

依据：

- COMSOL 支持 batch 模式。
- Codex 可以生成参数化脚本，并通过 `comsol_batch` 自动运行。

### 4. 日志排错和迭代修正

适合任务：

- 处理 Java API 报错。
- 修正缺失路径、错误 tag、选择集错误。
- 根据日志定位几何、网格、求解器阶段的问题。
- 多轮微调脚本。

依据：

- `batchlog` 会暴露明确的失败阶段。
- Codex 对结构化日志、堆栈、命令行错误有较强修复能力。

### 5. 后处理和结果导出

适合任务：

- 导出表格。
- 导出图片。
- 定义派生值。
- 保存结果文件。
- 整理仿真报告草稿。

依据：

- COMSOL 后处理也可通过 Java API 设置。
- Codex 可以搜索 `Postprocessing`、`export plot`、`table csv` 等手册片段，再写脚本。

## Codex 难以完成或风险较高的 COMSOL 功能

### 1. 完全未知领域的复杂物理建模

困难点：

- 物理假设需要专家判断。
- 边界条件可能不唯一。
- 材料模型、湍流模型、非线性模型选择依赖专业经验。

Codex 可辅助，但不应独立定稿。需要用户提供论文、公式、边界条件或目标结果。

### 2. 高度复杂几何和 CAD 修复

困难点：

- 复杂 CAD 导入、几何修补、布尔失败常依赖 GUI 观察。
- 小缝隙、重合面、非流形结构不容易仅靠日志判断。

Codex 可尝试参数化简单几何；复杂 CAD 更适合用户先在 COMSOL GUI 或 CAD 软件中整理。

### 3. 许可证或模块不可用的模型

困难点：

- 某些物理场需要特定模块。
- 本机许可证没有对应模块时 batch 会失败。

Codex 不会也不能绕过许可证。只能根据日志换用可用模块或建议替代建模路线。

### 4. 大规模、高精度、长时间仿真

困难点：

- 求解时间长。
- 内存占用高。
- 网格和求解器设置需要多轮工程调参。

推荐先做粗网格、小范围、低维验证，再提高精度。

### 5. 结果物理正确性的最终判断

困难点：

- 数值收敛不等于物理正确。
- 量纲、边界条件、材料参数、参考实验都需要领域审查。

Codex 可以检查脚本一致性、日志成功、结果是否导出、数量级是否异常；最终物理解释需要用户或领域专家确认。

## 优化后的推荐工作流

### 新模型

1. 用户描述目标、物理场、几何、边界条件、输出指标。
2. Codex 调用 `comsol_example_search` 找类似官方案例。
3. Codex 调用 `comsol_doc_search` 查 API 和模块说明。
4. Codex 生成最小 Java API 脚本。
5. Codex 调用 `comsol_batch` 运行。
6. Codex 读取日志和导出结果。
7. 若失败，按日志定位并小步修正。
8. 若成功，再增加精度、参数扫描或后处理。

### 复现论文

1. 先提取论文中的几何、材料、方程、边界、求解器和验证图。
2. 搜索官方相似案例。
3. 先做简化版模型。
4. 输出与论文相同或相近的观测量。
5. 比较趋势，再逐步补齐复杂项。

### 参数扫描

1. 明确扫描参数、范围、步长和输出指标。
2. 生成参数化脚本。
3. 导出 CSV。
4. 批处理运行。
5. Codex 汇总成功/失败组和结果趋势。

## 检验这个优化是否生效

### 标准 1：MCP 工具完整

让 Codex 调用 `comsol_info`，应看到：

- `COMSOL_BIN_EXISTS=True`
- `COMSOL_WORKDIR_EXISTS=True`
- `COMSOL_APPLICATIONS_DIR_EXISTS=True`
- `COMSOL_DOC_PDF_DIR_EXISTS=True`

### 标准 2：案例检索可用

测试查询：

```json
{
  "query": "heat transfer parameter sweep",
  "module": "Heat_Transfer_Module",
  "limit": 2
}
```

成功表现：

- 返回 `Heat_Transfer_Module` 下的官方案例说明。
- 结果包含 `relative_path`、`snippet`、可能的 `.mph` 文件路径。

### 标准 3：Help/PDF 搜索可用

测试查询：

```json
{
  "query": "java api create geometry mesh study",
  "limit": 2,
  "max_pdfs": 3,
  "max_pages_per_pdf": 40
}
```

成功表现：

- `searched_pdfs` 优先包含：
  - `ApplicationProgrammingGuide.pdf`
  - `COMSOL_ProgrammingReferenceManual.pdf`
- 返回页码和片段。
- 首次搜索后缓存目录出现 PDF 文本缓存。

### 标准 4：建模行为改变

让 Codex 做一个新的 COMSOL 模型时，合格行为是：

- 先搜索官方案例。
- 再搜索相关 API/Help。
- 然后才生成 Java/M 脚本。
- 运行 `comsol_batch` 后根据日志迭代。

如果 Codex 直接凭记忆写复杂模型、没有搜索案例/说明书，说明没有正确触发 `comsol-automation` skill 或需要手动提醒它“先查 COMSOL 本地案例和 Help”。

## 推荐提示词

```text
用 COMSOL 自动化流程完成这个模型。先搜索本机 COMSOL 官方案例和 Help 文档，再生成最小可运行 Java API 脚本，用 comsol_batch 运行，读取日志后迭代修正。
```

```text
帮我复现这个论文里的 COMSOL 仿真。请先找相似官方案例，说明采用哪些假设，再生成脚本并跑一个粗网格版本。
```

```text
帮我做 COMSOL 参数扫描，输出 CSV。先查本地案例和 API 文档，不要直接凭记忆写复杂模型。
```

#codex 

## 今日项目内容

- 在 Obsidian vault `TERRA#0` 中完成 AI 协作环境的初步搭建。
- 安装并启用社区插件：
  - BRAT：用于从 GitHub 仓库安装/更新测试版插件。
  - Claudian：将 Claude Code、Codex 等 coding agents 嵌入 Obsidian vault。
- 通过 BRAT 添加插件来源 `YishenTu/claudian`，并安装 Claudian `2.0.18`。
- 生成并更新 Claudian 本地配置目录 `.claudian/`，包含会话记录与插件设置。
- 配置 Codex 作为可用 provider，并保留 Claude/Codex 的模型、权限、推理等基础设置。
- 现有笔记包括：
  - [[codex（弃用）]]：记录 Codex CLI、ModelScope provider、模型与 API key 配置思路。
  - [[codex-bosidian 关联]]：用于记录项目总结与后续 Git 工作流。

## 简述工作流程

1. **准备 vault**：打开 Obsidian 项目目录 `TERRA#0`，确认基础文件与配置目录。
2. **安装插件管理工具**：安装 BRAT，并在社区插件列表中启用。
3. **添加 AI 协作插件**：通过 BRAT 添加 `YishenTu/claudian`，安装并启用 Claudian。
4. **配置 AI provider**：在 Claudian 设置中启用 Codex，确认 Claude/Codex 的模型、权限与工作目录设置。
5. **记录配置说明**：在 [[codex（弃用）]] 中整理 Codex CLI、ModelScope、API key 等配置要点。
6. **沉淀项目文档**：在当前笔记中记录当天完成内容，便于后续继续配置、提交 Git 或复盘。

## 后续建议

- 补充 Git 初始化、提交、远程仓库绑定与推送流程。
- 将 Codex/ModelScope 的配置步骤整理为可复用清单。
- 定期记录每日改动，形成项目日志。

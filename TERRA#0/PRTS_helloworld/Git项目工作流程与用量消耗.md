# Git 项目工作流程与用量消耗

> 记录时间：2026-05-25 17:27:32 +08:00  
> 项目位置：Obsidian vault `TERRA#0`  
> 关联笔记：[[codex（弃用）]]、[[codex-bosidian 关联]]、[[## Git 项目工作内容总结]]

## 1. 当前 Git 项目状态

当前目录尚未初始化为 Git 仓库。

执行检查结果：

```bash
git status
# fatal: not a git repository (or any of the parent directories): .git

git log --oneline --decorate -10
# fatal: not a git repository (or any of the parent directories): .git
```

因此，目前这个项目还处于 **Git 准备阶段**：已经整理了 Obsidian + Codex/Claudian 的项目内容，但还没有形成正式的 Git 提交历史。

## 2. 已完成的项目工作内容

- 整理 Obsidian vault `TERRA#0` 的基础项目资料。
- 记录 Codex CLI、ModelScope provider、模型与 API key 配置思路，见 [[codex（弃用）]]。
- 搭建 Obsidian 内部 AI 协作环境：
  - 安装并启用 BRAT 插件。
  - 通过 BRAT 添加 `YishenTu/claudian`。
  - 安装 Claudian 插件，当前版本为 `2.0.18`。
  - 在 Claudian 中启用 Codex provider。
- 生成本地配置与会话记录：
  - `.claudian/claudian-settings.json`
  - `.claudian/sessions/conv-1779699852531-c7sapxz8r.meta.json`
- 已建立项目说明类笔记：
  - [[codex-bosidian 关联]]：记录 Obsidian 与 Codex/Claudian 的关联配置。
  - [[## Git 项目工作内容总结]]：记录 Git 项目工作内容与建议流程。

## 3. Git 项目建议工作流程

### 第一步：初始化仓库

```bash
git init
```

作用：让当前 vault 成为 Git 仓库，开始记录版本历史。

### 第二步：创建 `.gitignore`

建议忽略：

```gitignore
# Obsidian workspace state
.obsidian/workspace.json
.obsidian/workspace-mobile.json

# AI / local session records
.claudian/sessions/
.claude/

# Secrets / local environment
.env
*.key
*.pem
```

注意：`.obsidian/plugins/` 是否提交，要看目标：

- 如果想完整复现当前 Obsidian 环境，可以提交插件文件。
- 如果只想管理笔记内容，建议忽略插件主体，只记录插件清单与配置说明。

### 第三步：检查文件状态

```bash
git status
```

作用：确认哪些文件会进入版本控制，避免误提交敏感配置或临时会话。

### 第四步：添加文件

```bash
git add .
```

作用：把准备提交的笔记、配置说明、项目文档加入暂存区。

### 第五步：提交初始版本

```bash
git commit -m "初始化 Obsidian AI 协作项目"
```

作用：保存第一个稳定版本，作为后续修改的起点。

### 第六步：绑定远程仓库

```bash
git remote add origin <远程仓库地址>
```

作用：将本地项目与 GitHub / GitLab / Gitee 等远程仓库关联。

### 第七步：推送到远程仓库

```bash
git branch -M main
git push -u origin main
```

作用：完成远程备份，后续可以多设备同步与版本回溯。

## 4. 推荐的日常工作流

1. 在 Obsidian 中编辑笔记与项目文档。
2. 用 AI 助手总结、整理、重构内容。
3. 执行 `git status` 检查变化。
4. 执行 `git diff` 查看具体改动。
5. 执行 `git add` 暂存确认后的文件。
6. 执行 `git commit` 保存一个清晰版本。
7. 执行 `git push` 同步到远程仓库。

一句话版本：

> 先写内容，再检查变化；先确认无误，再提交推送。

## 5. 本次 Codex / Claudian 用量消耗

### Claudian 会话元数据记录

来源：`.claudian/sessions/conv-1779699852531-c7sapxz8r.meta.json`

- Provider：`codex`
- Model：`gpt-5.5`
- Context window：`258400`
- Context tokens：`29828`
- Context 使用比例：`12%`
- Input tokens：`29828`
- Cache read input tokens：`28544`
- Cache creation input tokens：`0`

### Codex 会话日志最新 token_count

来源：Codex session jsonl 最新 `token_count` 事件。

- Total input tokens：`537177`
- Cached input tokens：`447104`
- Output tokens：`3976`
- Reasoning output tokens：`1020`
- Total tokens：`541153`
- Model context window：`258400`

### Rate limit 状态

- 主要窗口使用量：`8%`
- 主要窗口：`300` 分钟
- 主要窗口重置时间：2026-05-25 21:15:30 +08:00
- 次级窗口使用量：`1%`
- 次级窗口：`10080` 分钟
- 次级窗口重置时间：2026-06-01 16:15:30 +08:00

## 6. 小结

当前项目已经完成了 **Obsidian + Claudian + Codex** 的协作环境搭建与基础文档沉淀，但还没有正式进入 Git 版本管理。

下一步最值得做的是：

1. 创建 `.gitignore`。
2. 执行 `git init`。
3. 完成第一次 `git add` 与 `git commit`。
4. 绑定远程仓库并推送。

这样，当前 vault 就会从“配置中的项目”变成一个可以追踪、回滚、同步的正式 Git 项目。



- 整理 Obsidian vault `TERRA#0` 的项目资料。
- 记录 Codex CLI、ModelScope、API key 等配置思路，见 [[codex（弃用）]]。
- 搭建 AI 协作环境：
  - 安装 BRAT 插件。
  - 通过 BRAT 安装 Claudian。
  - 启用 Codex 作为 AI provider。
- 建立项目说明文档，当前总结内容已在 [[codex-bosidian 关联]] 中记录。
- 准备后续 Git 工作流，包括：
  - 初始化 Git 仓库。
  - 添加 `.gitignore`。
  - 提交项目初始版本。
  - 绑定远程仓库。
  - 推送到 GitHub 或其他代码托管平台。

## 建议的 Git 工作流程

1. `git init` 初始化仓库  
2. 创建 `.gitignore`，排除缓存、插件临时文件、敏感配置  
3. `git add .` 添加文件  
4. `git commit -m "初始化 Obsidian AI 协作项目"`  
5. 绑定远程仓库  
6. `git push` 推送项目  


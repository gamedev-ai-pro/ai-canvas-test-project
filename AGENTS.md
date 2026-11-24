# 静物与光影

这是一个 AI Canvas 项目目录。`project.json` 保存项目名称，`project-store/` 保存画布、对话和同步记录。

通过运行中的本机服务读取工作状态。先用 `GET /api/projects` 按目录查找项目 ID，再用 `GET /api/projects/:projectId/local-state` 读取画布和本机对话。请勿手工改写 ProjectStore 日志。

本机素材按用途保存在 `assets/`、`generated/` 和 `videos/` 下。协作媒体按需从资产库读取。

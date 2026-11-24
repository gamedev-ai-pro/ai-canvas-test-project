# ai-canvas-test-project

[AI Canvas](https://github.com/gamedev-ai-pro/ai-canvas) 的共享测试项目，供人验与新 e2e 复用。
主仓以 submodule `fixtures/test-project` 钉住版本，`bun run wt create` 时复制一份给 worktree，不直接改这里。

## 约定

- **公开仓库**：素材、提示词、模型名与生成参数全部公开；不放凭据、私人或授权不明的素材。
- 媒体走 Git LFS（见 `.gitattributes`）。已有主仓 `.githooks` 时，用 `git lfs install --skip-repo` 配置 LFS。
- 项目格式变更时，主仓同一 PR 用迁移脚本升级本项目并更新 submodule 指针。

## 覆盖清单

从主仓运行 `bun run wt create <issue> <slug>`，在该 worktree 里用 `bun run dev` 打开「静物与光影」。

- [x] 三个画布页。「静物图集」含 8 张真实生成图片与两个组，「形色研究」含 4 张真实生成图片。
- [x] 视频与音频。「光影与声音」含带合成音轨的 5 秒 MP4，`refs/` 中另存同一音调的 3 秒 WAV 原件。
- [x] 蒙版与项目模板。「形色研究」左上图片带 RLE 蒙版。模板库有「柔光静物」和带参考图的「纸质色块变体」。
- [x] 会话历史。三个会话共 30 条消息，包括 12 轮成功的 Codex 图片生成和 3 轮未产出结果的请求。其中一轮图片生成带参考图，视频请求保留 WAV 引用。

本项目用当前新建项目的 `project.json` 版本 2 与 ProjectStore。60 条消息上限适用于旧会话接口
（主仓 `server/app.ts` 的 `sessionSchema`）。ProjectStore 的 `applyGenerationSettled` 会追加完整轮次
（`server/projects/projectStore.ts`）。

「对话历史」可查看各页的历史。`GET /api/projects/test-project/local-state` 返回完整会话，包括用于重放的图片
提示词、供应商、模型、尺寸、质量和参考图。当前本机历史弹窗未提供「重新生成」操作。音频引用可在同一响应中找到，
通过 `GET /api/projects/test-project/media-references/<id>` 读取 WAV。

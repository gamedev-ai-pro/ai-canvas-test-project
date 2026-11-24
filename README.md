# ai-canvas-test-project

[AI Canvas](https://github.com/gamedev-ai-pro/ai-canvas) 的共享测试项目，供人验与新 e2e 复用。
主仓以 submodule `fixtures/test-project` 钉住版本，`bun run wt create` 时复制一份给 worktree，不直接改这里。

## 约定

- **公开仓库**：素材、提示词、模型名与生成参数全部公开；不放凭据、私人或授权不明的素材。
- 媒体走 Git LFS（见 `.gitattributes`），克隆前先 `git lfs install`。
- 项目格式变更时，主仓同一 PR 用迁移脚本升级本项目并更新 submodule 指针。

## 覆盖清单（搭建中）

- [ ] 多页 + 图片 + 组
- [ ] 视频 / 音频
- [ ] 蒙版 + 项目模板
- [ ] 会话历史（真实生成，接近 60 条上限）

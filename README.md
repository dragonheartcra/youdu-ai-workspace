# youdu-ai-workspace

有度 AI 工作台汇报页（纯静态，单文件 `index.html`）。由 Netlify 从本仓库自动部署。

- 生产：https://youdu-ai-workspace.netlify.app
- 客户预览：https://client-preview--youdu-ai-workspace.netlify.app

---

## 部署纪律（为了控制 Netlify credits）

- 日常改动一律 push 到 `client-preview` 分支，客户在这里看：
  `https://client-preview--youdu-ai-workspace.netlify.app`
  该分支的部署 **不消耗 credits**。
- 只有客户确认后，才把 `client-preview` 合并到 `main`。每次合并消耗 **15 credits**，不要一天合十次。
- 小改动先攒着，一次合并。改 10 次合并 1 次 = 15 credits；改 10 次合并 10 次 = 150 credits。
- 纯文档 / 注释类改动，commit message 加 `[skip ci]` 或 `[skip netlify]`，不触发构建。
- 不要再使用拖拽上传或 `netlify deploy --prod`。这两种方式每次都是 15 credits，且会覆盖 Git 部署的结果。
- 需要紧急回滚时：在 Netlify Deploys 列表里对旧的成功部署点 **Publish Deploy**，回滚本身不消耗 credits。
  注意：回滚后如果 `main` 又有新 push，会自动覆盖你回滚的版本。要保住回滚结果，去 Deploys 页面点 **Lock to stop auto publishing**。

## 目录

- `index.html` 站点唯一页面
- `netlify.toml` 构建配置（`publish = "."`、无构建命令）
- `robots.txt` 全站 noindex（预览与生产都不希望被搜索引擎收录）
- `.gitignore` 忽略 `.netlify/`（Netlify 本地关联状态，绝不能提交）

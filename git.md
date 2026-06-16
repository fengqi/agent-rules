<!-- 本文件维护不同类型项目中的 Git 分支、MR 和 push 习惯。 -->

# Git 使用习惯

- `git` 提交时除非特殊说明，必须使用中文
- `git` 提交时拆分辅助函数、不同功能的修改
- 不得在 `dev`、`stage`、`pre`、`master`、`main` 等具有独特意义的分支直接提交
- 新 git 项目使用 `master` 作为主分支名，禁止使用 `main`。
- 项目名称带有 `csgo`、`blued`、`unsolo` 字样的为公司项目
- 公司项目热修复和即时性优化分支名模板：`lyf/hotfix/<bug-or-optimization-name>`。
- 公司项目跟随版本发布的功能和非即时性优化分支名模板 `lyf/feature/<year>/<date>-<version>`，例如 `lyf/feature/2026/0519-7.46.5`。
- 个人项目，例如 `github.com/fengqi` 这类仓库，通常可以直接在 `master` 上开发。

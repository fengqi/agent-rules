<!-- 本文件维护不同类型项目中的 Git 分支、MR 和 push 习惯。 -->

# Git 使用习惯

- 新 git 项目使用 `master` 作为主分支名。
- 公司项目通常包括 `csgo`、`social`、`unsolo` 等 GitLab 项目；不要默认直接在 `master` 上开发。
- 公司项目开始编码前，先创建空 GitLab merge request，再基于 MR 分支改代码。
- 热修复和即时性优化使用 `lyf/hotfix/<bug-or-optimization-name>`。
- 跟随版本发布的功能和非即时性优化使用 `lyf/feature/<year>/<date>-<version>`，例如 `lyf/feature/2026/0519-7.46.5`。
- 公司项目每完成一组相对独立的修改，可以 push 到远端并合并到 `dev`，然后切回原开发分支继续。
- 对个人项目，尤其是 `github.com/fengqi` 这类仓库，通常可以直接在 `master` 上开发。

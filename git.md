<!-- 本文件维护不同类型项目中的 Git 分支、MR 和 push 习惯。 -->

# Git 使用习惯

- 公司项目通常包括 `csgo`、`social`、`unsolo` 等 GitLab 项目。
- 公司项目不要默认直接在 `master` 上开发。
- 公司项目开始编码前，先创建空 GitLab merge request，再基于 MR 分支开始改代码。
- 热修复和即时性优化使用 `lyf/hotfix/<bug-or-optimization-name>` 分支名。
- 跟随版本发布的功能和非即时性优化使用 `lyf/feature/<year>/<date>-<version>` 分支名。
- `lyf/feature/<year>/<date>-<version>` 中，`year` 使用四位年份，例如 `2026`。
- `lyf/feature/<year>/<date>-<version>` 中，`date` 使用上线日期的四位月日，例如 `0519`。
- `lyf/feature/<year>/<date>-<version>` 中，`version` 使用跟随版本号，例如 `7.46.5`。
- 分支名里的 bug 或优化英文名要简短、可读、能表达问题或目标。
- 公司项目开发中，每完成一组相对独立的修改，可以 push 到远端并合并到 `dev`，然后再切回原开发分支继续。
- 对个人项目，尤其是 `github.com/fengqi` 这类仓库，通常可以直接在 `master` 上开发。

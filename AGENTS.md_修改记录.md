# AGENTS.md 修改记录

> 记录本仓库根目录 `AGENTS.md`（家规）的每次改动。每条含：修改文件 / 修改内容 / 修改思路 / 验证情况。
> 约定：修改 `AGENTS.md` 必须在本文件追加一条；最新的在最下面（按时间顺序）。

## 2026-09-03

### 第一次：新建根目录 AGENTS.md（家规由 CLAUDE.md 合并）

- 修改文件：
  - `AGENTS.md`（仓库根，新建）
  - `vision-wiki/CLAUDE.md`（删除）
  - `vision-wiki/AGENTS.md`（删除，此前接管时建的入口文件）
  - `vision-wiki/wiki/index.md`、`vision-wiki/wiki/overview.md`、`README.md`（更新指向旧 CLAUDE.md 的链接）
- 修改内容：
  - 把原 `vision-wiki/CLAUDE.md` 的全部家规并入仓库根 `AGENTS.md`：两条死规矩、知识库定位（主人大程，机器视觉工程师）、三层结构（vision-wiki/raw、vision-wiki/wiki、assets）、Ingest/Query/Lint 工作流、页面格式、项目页五栏目。
  - 新增两条约定：① 每次摄入同步更新根目录 `README.md` 的"内容更新记录"；② 公开仓库下客户名/产线用代号、公司机密参数与代码不放入 raw/。
  - 删除 CLAUDE.md 与 vision-wiki/AGENTS.md，今后只维护根目录 AGENTS.md 一个家规文件。
- 修改思路/原因：
  - 主人决定不再维护 CLAUDE.md，要求把内容融合进 AGENTS.md。
  - Codex 按"当前工作目录"自动加载 AGENTS.md；仓库根是 `F:\我的知识库`，家规放在 `vision-wiki/` 子目录里不会被自动加载，故合并后统一放到仓库根。
- 验证情况：
  - 已确认两个旧文件删除（Python os.remove，删除后 exists=False）；
  - index.md / overview.md / README.md 中指向 CLAUDE.md 的有效链接均已改指 AGENTS.md，grep 校验仅剩历史叙述性文字；
  - 已提交并推送（commit `5222d60`）。

### 第二次：新增 push 前询问约定与内联修改记录

- 修改文件：
  - `AGENTS.md`（修改）
  - `vision-wiki/wiki/log.md`（追加操作流水）
- 修改内容：
  - 新增"Git 与同步约定"节：本地 `git add`/`commit` 可正常进行，**`git push` 推送 GitHub 前必须先询问主人、经明确同意才推送**。
  - 首次加入"家规修改记录（Changelog）"内联小节（本次起被第三次改动替代为独立文件）。
- 修改思路/原因：
  - 主人明确要求："推送之前需要先问我"。
  - 主人要求 AGENTS.md 要有修改记录，先以内联小节落地。
- 验证情况：
  - 已查系统实时时间 2026-09-03 10:2x；
  - 本地提交 commit `0a035b6`（按约定未推送，等待主人确认）。

### 第三次：修改记录独立为 AGENTS.md_修改记录.md（采用 GoodLife 格式）

- 修改文件：
  - `AGENTS.md_修改记录.md`（新建，本文件）
  - `AGENTS.md`（移除内联"家规修改记录"小节，改为指向本文件；新增"修改记录要求"约定）
- 修改内容：
  - 参照 `F:\个人文件\GoodLife\AGENTS.md_修改记录.md` 的格式，把家规改动记录独立成同目录文件，每条按"修改文件 / 修改内容 / 修改思路 / 验证情况"四段书写。
  - AGENTS.md 内不再保留内联 Changelog，改为一句指向本文件；并明确"修改 AGENTS.md 必须在本文件追加记录"。
- 修改思路/原因：
  - 主人给出 GoodLife 的修改记录作为样板，要求采用这种独立、详细的记录方式（比内联小节更完整，含思路与验证）。
  - 与 GoodLife"源文件名_修改记录.md 同目录维护"的惯例保持一致。
- 验证情况：
  - 已通读 GoodLife 的 `AGENTS.md_修改记录.md` 与 `AGENTS.md` 确认格式；
  - 已查系统实时时间 2026-09-03 10:26。
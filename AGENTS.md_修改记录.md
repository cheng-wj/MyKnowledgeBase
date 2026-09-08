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
## 2026-09-03（第四次）

### 新增多设备识别与上传设备标记机制

- 修改文件：
  - `AGENTS.md`（Ingest 第 5 步补充设备标记要求；新增「多设备识别」节）
  - `README.md`（每条更新记录末尾补 `[@公司机]`，新增标记说明；历史记录回填）
  - `vision-wiki/wiki/log.md`（每条记录标题末尾补 `[@公司机]`；历史回填 + 本次记录）
  - git 配置（仓库级）：本机 `DESKTOP-R4RRO1S` 作者名设为 `大程·公司机`
- 修改内容：
  - 新增「多设备识别」节，参照 GoodLife 的设备登记表：以 `hostname` 为键登记每台设备的称呼、用户/平台、仓库路径、git 作者名、备注；新设备先查 hostname 再补登。
  - 设备标记约定：① 每台设备设独立 git 作者名 `大程·<称呼>`（邮箱统一用 GitHub noreply，仍关联账号）；② README 更新记录与 log.md 每条末尾标注 `[@称呼]`，直观看出每条内容由哪台设备录入。
  - 已登记首台设备：`DESKTOP-R4RRO1S`（公司机，用户 ZY，Windows，仓库在 `F:\我的知识库`，备注 Python 用 `py`、git 走代理 7897）。
- 修改思路/原因：
  - 主人提出"以后会有多个设备上传，需要区分上传设备"，并让参照 GoodLife 的多设备识别方式。
  - GoodLife 只靠家规登记表让 agent 认路（git 作者统一不分设备）；本库在照搬登记表的基础上，加一层 git 作者名 + 记录内 `[@设备]` 标记，满足"上传记录能看出哪台设备"的需求，且不改动知识库内容结构。
  - 历史内容全部在本机（公司机）录入，故回填 `[@公司机]`。
- 验证情况：
  - 已确认本机 hostname = DESKTOP-R4RRO1S（与 GoodLife 登记一致，为公司工作机）；
  - 已查系统实时时间 2026-09-03；
  - README/log 标记回填后 grep 校验每条记录均带 `[@公司机]`。
## 2026-09-03（第五次）

### 多设备节新增「新设备首次接入流程」，让 agent 自检自填

- 修改文件：
  - `AGENTS.md`（「多设备识别」节新增"新设备首次接入流程（agent 读到本文件须自动执行）"小节）
  - `vision-wiki/wiki/log.md`（追加本条操作流水）
- 修改内容：
  - 把原来一句"下次在未记录的设备上工作先查 hostname 补登"扩写为可执行的三步自检流程：
    1. 已在表中 → 核对并修正 git 作者名为 `大程·<本机称呼>`，确认路径后工作；
    2. 不在表中（新设备）→ agent 自查 hostname/用户名/平台/仓库路径，只问主人一个问题（这台设备怎么称呼），随后自动补登表格、设 git 作者名、在修改记录文件登记、后续记录用 `[@称呼]`；未登记/未设作者名前不得提交；
    3. 换设备后第一次提交前用 `git log -1 --pretty=%an` 确认作者。
- 修改思路/原因：
  - 主人要求"让别的设备看到 AGENTS.md 时自己去填"——即新设备上的 agent 读到家规就能自动完成识别、登记、配置，不依赖主人手动交代。
  - 流程严格遵守死规矩①：新设备只需问主人"称呼"这一个问题，其余信息（hostname/平台/路径）agent 自查可得。
- 验证情况：
  - 已查系统实时时间 2026-09-03；
  - 采用精准字符串替换，仅改动「多设备识别」节，其余家规内容不变。
## 2026-09-08（第六次）

### 目录结构全面中文化（vision-wiki→知识库 等）

- 修改文件：
  - `知识库/`（由 `vision-wiki/` 用 git mv 改名，含 `原始资料/`、`知识页/`、`附件/` 及全部中文子分类）
  - `AGENTS.md`（家规内所有路径引用改为中文新路径）
  - `README.md`、`知识库/知识页/index.md`、全部知识页（链接/图片相对路径批量重写）
- 修改内容：
  - `vision-wiki/raw/wiki/assets` → `知识库/原始资料/知识页/附件`；知识页分类 `algorithms/projects/hardware/systems/concepts/entities/synthesis` → `算法/项目/硬件/系统/概念/实体/综合分析`；硬件子分类 `cameras/lenses/sensors/lights/acquisition` → `相机/镜头/传感器/光源/采集卡`；系统子分类 新建 `架构/通信/部署`；原始资料 `papers/articles/datasheets/images/code` → `论文/文章/规格书/图片/代码`。
  - 用脚本按"旧名解析绝对路径→映射新名→重算相对路径"重写全部 markdown 链接；顺带修正相机/镜头/传感器三级页中 `原始资料/附件` 相对路径少一级的历史错误。
  - 家规三层结构、Ingest/Query/Lint 流程、多设备节、防遗漏节中的路径全部更新为中文。
- 修改思路/原因：
  - 主人要求全中文命名，Obsidian 原生支持中文，GitHub 亦支持；仅保留 index.md/log.md/overview.md/AGENTS.md/README.md 等功能文件英文名为工具约定。
  - git mv 保留历史；core.quotepath=false 让中文路径正常显示。
- 验证情况：
  - 已查系统时间 2026-09-08；
  - 链接校验脚本遍历全部 md，相对链接均能解析到真实文件（URL 编码的 `%28%29`、`<文件名>` 占位符除外）。

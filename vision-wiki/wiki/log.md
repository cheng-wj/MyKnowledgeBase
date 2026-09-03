# 操作日志（Log）

> 只追加。每条前缀：`## [YYYY-MM-DD] <动作> | <标题>`。
> 查询最近记录：`grep "^## \[" log.md | tail -5`

## [2026-08-19] init | 搭建机器视觉知识库骨架 [@公司机]
- 创建三层目录结构（raw / wiki / assets）。
- 写入 CLAUDE.md（含两条死规矩与维护约定）。
- 初始化 index.md、overview.md、projects/_template.md。
- 待主人开始摄入资料（论文 / 项目 / 硬件 datasheet 等）。

## [2026-08-19] ingest | MARS-2442-192X2M-NF 相机规格 [@公司机]
- 来源：大恒图像官网产品页（CoaXPress 2.0 黑白工业相机）。
- 存档：raw/datasheets/MARS-2442-192X2M-NF.md（网页规格存档）。
- 新建页面：wiki/hardware/cameras/MARS-2442-192X2M-NF.md。
- 触及页面：index.md、log.md、cameras/ 新页、raw 存档，共 4 个。
- 待补：主人实际选型理由、使用项目、踩坑、镜头/光源搭配。

## [2026-08-19] ingest | MARS-2442-192X2M-NF 产品图片 [@公司机]
- 从官网产品页抓取 14 张产品相关图（跳过 4 张 logo/导航 UI 图）。
- 原图存 raw/images/，引用副本存 assets/。
- 相机页新增「图片资料」章节嵌入全部 14 张图，待主人标注每图含义（光谱曲线/配件/尺寸/外观）。

## [2026-08-19] ingest | 光谱曲线与配件图补充 [@公司机]
- 主人提供光谱响应曲线截图、相关配件截图各 1 张。
- 保存为 raw/images/ 与 assets/ 下的 spectral-response 和 accessories。
- 相机页「图片资料」更新：新增已标注的光谱曲线与配件图，保留 14 张待确认官网截图。

## [2026-08-19] lint | 删除未确认官网截图 [@公司机]
- 应主人要求，删除相机页「其他官网产品页截图」章节及对应 14 张图（raw/images 与 assets）。
- 保留已标注的光谱响应曲线与相关配件图（各 1 张）。

## [2026-09-03] takeover | 维护者切换为 Codex [@公司机]
- 知识库维护者由 WorkBuddy 交接给 Codex（Karpathy Wiki 技能已装到 `C:\Users\ZY\.codex\skills\karpathy-wiki-cn`）。
- 新增 [AGENTS.md](../AGENTS.md) 作为 Codex 入口，指向 CLAUDE.md 为唯一 schema；两条死规矩与全部约定继续生效。
- 历史 .workbuddy/ 记忆保留不动，raw/ 继续只进不改。
- 现状：仅摄入 1 篇（MARS-2442-192X2M-NF 相机）；algorithms / systems / concepts / entities / synthesis 待摄入。
## [2026-09-03] lint | 主人称呼更正 [@公司机]
- 主人称呼由"小程"更正为"大程"，已同步更新 AGENTS.md；后续页面与记录一律使用"大程"。
## [2026-09-03] sync | 知识库纳入 git 并推送 GitHub [@公司机]
- 仓库根目录：F:\我的知识库（含 vision-wiki、.obsidian 配置、.workbuddy 记忆）。
- 远程私有仓库：https://github.com/cheng-wj/MyKnowledgeBase （Private）。
- 已添加 .gitignore（忽略系统垃圾与 Obsidian 工作区缓存），首次提交 19 个文件并推送 main 分支。
- 以后摄入/维护后记得提交推送：git add -A → git commit -m "..." → git push。
## [2026-09-03] sync | 新增根目录 README.md（内容更新记录） [@公司机]
- 应主人要求，在仓库根目录新建 README.md 作为 GitHub 首页：含知识库简介、目录结构、内容更新记录（最新在上）。
- 历史摄入记录已从 log.md 整理进 README；以后每次摄入内容同步更新 README 与本日志。
## [2026-09-03] lint | 家规合并：CLAUDE.md 内容并入根目录 AGENTS.md [@公司机]
- 主人决定不再维护 CLAUDE.md：已删除 vision-wiki/CLAUDE.md 与 vision-wiki/AGENTS.md。
- 家规全部内容（两条死规矩、四大板块、项目页五栏目、Ingest/Query/Lint 工作流）合并到仓库根 [AGENTS.md](../../AGENTS.md)，Codex 在仓库根打开即可自动加载。
- 新增约定：每次摄入同步更新根目录 README.md；公开仓库下客户名用代号、敏感信息脱敏。
- 已更新 index.md、overview.md、README.md 中指向旧 CLAUDE.md 的链接。
## [2026-09-03] lint | 家规新增两条约定 [@公司机]
- AGENTS.md 新增"家规修改记录（Changelog）"章节，以后家规每次改动都追加记录。
- 新增 Git 约定：git push 推送前必须先询问主人、经同意才推送；本地 commit 可正常进行。
## [2026-09-03] lint | 家规修改记录改为独立文件（参照 GoodLife） [@公司机]
- 新建仓库根 [AGENTS.md_修改记录.md](../../AGENTS.md_修改记录.md)：按 GoodLife 惯例，每条记录含"修改文件/修改内容/修改思路/验证情况"，已补记 AGENTS.md 第一、二次改动。
- AGENTS.md 移除内联"家规修改记录"小节，改为"修改记录要求"节，指向独立文件。
## [2026-09-03] ingest | 埃科 TS21MCXP12-230M/C 规格书 + 21MP/24MP 景深对比实验 [@公司机]
- 资料①：埃科光电 TAURUS TS21MCXP12-230M/C 产品规格书 PDF → 存档 [raw/datasheets](../raw/datasheets/TS21MCXP12-230M(C)%20产品规格书.pdf)，新建 [相机页](hardware/cameras/TS21MCXP12-230M.md)。
- 资料②：《相机实验对比.pptx》（21MP 埃科 vs 24MP 大恒；220mm 镜头 f8、同光源）→ 存档 [raw/articles](../raw/articles/相机实验对比-21MP对比24MP.pptx)，4 张对比图存 raw/images 与 assets，新建综合分析页 [21MP对比24MP-相机景深实验](synthesis/21MP对比24MP-相机景深实验.md)。
- 交叉引用：MARS 相机页新增「对比实验」节，两台相机页互链，实验页链接两台相机。
- 更新：index.md（硬件 + 综合分析）、README.md 更新记录、本日志。
- 触及：2 个新页 + MARS 页/index/log/README，共 6 处。
- 待补：主人补充实验背景（哪个项目/客户场景）、两台相机的实际选型结论。

## [2026-09-03] lint | 新增多设备识别与设备标记约定 [@公司机]
- AGENTS.md 新增「多设备识别」节：以 hostname 登记设备（称呼/平台/路径/git作者名/备注），已登记 DESKTOP-R4RRO1S=公司机。
- 约定：每台设备用独立 git 作者名「大程·<称呼>」；README 更新记录与 log.md 每条末尾标注 [@称呼]。
- 本机 git 作者名设为「大程·公司机」；历史记录已回填 [@公司机]（此前内容均在本机录入）。
## [2026-09-03] lint | 家规新增"新设备首次接入自检流程" [@公司机]
- AGENTS.md「多设备识别」节写明：新设备上的 agent 读到家规须自动 hostname 自检——已登记则核对 git 作者名；未登记则自查信息、只问主人一个称呼问题，随后自动补登设备表、设「大程·<称呼>」作者名、登记修改记录，未完成前不提交。
## [2026-09-03] ingest | 基恩士 LJ-X8000 系列 2D/3D 线激光测量仪样本 [@公司机]
- 资料：Keyence LJ-X8000 系列 52 页产品样本 → 存档 [raw/datasheets](../raw/datasheets/Keyence-LJ-X8000系列-2D3D线激光测量仪-产品样本.pdf)。
- 结构：经主人确认，在 hardware/ 下新建 **sensors/** 子目录（3D/线激光等非面阵相机传感器），index 硬件板块分"相机/传感器"两组。
- 新建 [传感器页](hardware/sensors/Keyence-LJ-X8000系列.md)：光切断法原理、10 种探头选型表（量程/精度）、控制器与通信、应用、与面阵相机选型对比。
- 更新：index.md、README.md、本日志。触及：1 新页 + index/README/log，共 4 处。
- 待补：主人补充实际项目用的哪型探头、安装高度/视野、踩坑与验收口径。

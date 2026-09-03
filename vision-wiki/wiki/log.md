# 操作日志（Log）

> 只追加。每条前缀：`## [YYYY-MM-DD] <动作> | <标题>`。
> 查询最近记录：`grep "^## \[" log.md | tail -5`

## [2026-08-19] init | 搭建机器视觉知识库骨架
- 创建三层目录结构（raw / wiki / assets）。
- 写入 CLAUDE.md（含两条死规矩与维护约定）。
- 初始化 index.md、overview.md、projects/_template.md。
- 待主人开始摄入资料（论文 / 项目 / 硬件 datasheet 等）。

## [2026-08-19] ingest | MARS-2442-192X2M-NF 相机规格
- 来源：大恒图像官网产品页（CoaXPress 2.0 黑白工业相机）。
- 存档：raw/datasheets/MARS-2442-192X2M-NF.md（网页规格存档）。
- 新建页面：wiki/hardware/cameras/MARS-2442-192X2M-NF.md。
- 触及页面：index.md、log.md、cameras/ 新页、raw 存档，共 4 个。
- 待补：主人实际选型理由、使用项目、踩坑、镜头/光源搭配。

## [2026-08-19] ingest | MARS-2442-192X2M-NF 产品图片
- 从官网产品页抓取 14 张产品相关图（跳过 4 张 logo/导航 UI 图）。
- 原图存 raw/images/，引用副本存 assets/。
- 相机页新增「图片资料」章节嵌入全部 14 张图，待主人标注每图含义（光谱曲线/配件/尺寸/外观）。

## [2026-08-19] ingest | 光谱曲线与配件图补充
- 主人提供光谱响应曲线截图、相关配件截图各 1 张。
- 保存为 raw/images/ 与 assets/ 下的 spectral-response 和 accessories。
- 相机页「图片资料」更新：新增已标注的光谱曲线与配件图，保留 14 张待确认官网截图。

## [2026-08-19] lint | 删除未确认官网截图
- 应主人要求，删除相机页「其他官网产品页截图」章节及对应 14 张图（raw/images 与 assets）。
- 保留已标注的光谱响应曲线与相关配件图（各 1 张）。

## [2026-09-03] takeover | 维护者切换为 Codex
- 知识库维护者由 WorkBuddy 交接给 Codex（Karpathy Wiki 技能已装到 `C:\Users\ZY\.codex\skills\karpathy-wiki-cn`）。
- 新增 [AGENTS.md](../AGENTS.md) 作为 Codex 入口，指向 CLAUDE.md 为唯一 schema；两条死规矩与全部约定继续生效。
- 历史 .workbuddy/ 记忆保留不动，raw/ 继续只进不改。
- 现状：仅摄入 1 篇（MARS-2442-192X2M-NF 相机）；algorithms / systems / concepts / entities / synthesis 待摄入。
## [2026-09-03] lint | 主人称呼更正
- 主人称呼由"小程"更正为"大程"，已同步更新 AGENTS.md；后续页面与记录一律使用"大程"。
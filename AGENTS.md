# AGENTS.md — 机器视觉知识库维护说明（家规）

> 本文件是知识库的 schema：告诉维护者（LLM，当前为 Codex）如何组织、维护和扩展这个 wiki。
> 它不是一成不变的——主人和 LLM 在使用过程中共同演化它。
> （2026-09-03 起，原 `vision-wiki/CLAUDE.md` 内容已并入本文件，CLAUDE.md 不再维护。）

## 死规矩（主人要求，不可违反）

1. **先别动手构建**——和主人交互时一次只问一个问题，像真实对话伙伴，不一次性甩一堆。
2. **结构级改动先给方案等确认**——需求收集完、目录/结构方案给主人确认，主人明确回复"行"才动手搭建；任何结构级改动都先给方案等确认。

## 知识库定位

- 主人：**大程**，机器视觉工程师（图像处理 / 算法 / 软件开发 / 视觉系统搭建）。
- 目标：让工作更轻松——做项目时快速复用已有方案、选型、踩坑经验，避免重复劳动。
- 形态：Karpathy Wiki 模式（持久化、持续复利的个人知识库）。用 Obsidian 打开本文件夹（`F:\我的知识库`）即为 vault。
- 远程：GitHub 私有/公开仓库 `cheng-wj/MyKnowledgeBase`，本文件夹即仓库根。

## 三层结构（知识库主体在 `vision-wiki/`）

- **`vision-wiki/raw/`**：原始资料（论文 papers / 文章 articles / datasheet / 图片 images / 代码 code）。**只进不改**，是真相来源。
- **`vision-wiki/wiki/`**：LLM 生成维护的 markdown 知识层。LLM 全权负责，主人只读不写。
  - `algorithms/` 算法与算子 ｜ `projects/` 项目经验与踩坑 ｜ `hardware/` 硬件资料
  - `systems/` 视觉系统搭建 ｜ `concepts/` 核心概念 ｜ `entities/` 实体 ｜ `synthesis/` 综合分析
  - `index.md` 内容目录 ｜ `log.md` 详细操作流水（只追加）｜ `overview.md` 知识总览
- **`vision-wiki/assets/`**：图片附件。
- **`AGENTS.md`（本文件，仓库根）**：结构、约定与工作流说明。
- **`README.md`（仓库根）**：GitHub 首页，含"内容更新记录"。

## 核心工作流

### Ingest（摄入新资料）
1. 资料存到 `vision-wiki/raw/` 对应子目录。
2. 读内容，与主人讨论要点。
3. 在 `vision-wiki/wiki/` 对应分类下建/更新页面（算法→algorithms/，项目→projects/，硬件→hardware/，系统→systems/）。
4. 更新 `wiki/index.md`、追加 `wiki/log.md`（格式：`## [YYYY-MM-DD] ingest | 标题`，链接用相对 wiki/ 的路径）。
5. **同步更新根目录 `README.md` 的"内容更新记录"**（最新的在最上面，带页面链接）。
6. 提醒或直接帮主人提交推送：`git add -A` → `git commit -m "..."` → `git push`。
7. 汇报触及了多少页面。

### Query（提问）
先读 `wiki/index.md` 找相关页 → 深入阅读 → 综合回答并引用来源 → 有持续价值的产物（对比分析、主题梳理）存回 `wiki/synthesis/`，并追加 `wiki/log.md`。

### Lint（健康检查）
扫描矛盾、过时声明、孤立页、文中提到但未建页的概念、缺失交叉引用；自动修能修的，报告需人工判断的；追加 `wiki/log.md`。

## 页面格式

- 论文/算法/概念/项目页用 YAML frontmatter（title/authors/year/tags/ingested 等）。
- 页面间用 Obsidian `[[wikilinks]]` 互链。
- `index.md` 每行：`[页面名](相对路径) — 一行摘要`。
- `log.md` 每条前缀：`## [YYYY-MM-DD] <动作> | <标题>`，文件链接用 Markdown 标准链接（VSCode/Obsidian 预览可点击）。

## 防遗漏（项目页强制栏目）

每个 `vision-wiki/wiki/projects/*.md` 必须包含 `_template.md` 的五个栏目：
**关键参数与标定结果、硬件选型 BOM、踩坑与 root cause、客户/产线特殊约定、相关代码/算子**。

## 公开仓库注意事项

- 本仓库当前为公开。摄入真实项目资料时：**客户名/产线/验收口径一律用代号**（如"客户A-锂电产线"），公司机密参数与代码不放入 `raw/`。

## Obsidian 提示

- 打开仓库根文件夹即为 vault。
- 启用 Dataview 插件，可对页面 frontmatter 跑查询，生成动态表格。
- 图片放 `vision-wiki/assets/`，页面用标准相对链接引用。
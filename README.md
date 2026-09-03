# 我的知识库 · MyKnowledgeBase

机器视觉工程师的个人工作知识库，采用 **Karpathy LLM Wiki** 模式（[原始方法](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)）：
原始资料只进不改，由 LLM 持续整理成互相链接的 wiki 页面。用 **Obsidian** 打开本文件夹即可作为 vault 浏览。

## 目录结构

- **`vision-wiki/`** —— 知识库主体
  - `raw/` —— 原始资料（论文 papers / 文章 articles / datasheet / 图片 images / 代码 code），**只进不改**，是真相来源
  - `wiki/` —— LLM 维护的知识页：
    - `algorithms/` 算法与算子 ｜ `projects/` 项目经验与踩坑 ｜ `hardware/` 硬件资料
    - `systems/` 视觉系统搭建 ｜ `concepts/` 核心概念 ｜ `entities/` 实体 ｜ `synthesis/` 综合分析
    - `index.md` 内容目录 ｜ `log.md` 详细操作流水 ｜ `overview.md` 知识总览
  - `assets/` —— 图片附件
  - [AGENTS.md](AGENTS.md) —— 维护约定（家规，仓库根，Codex 自动加载）
- `.obsidian/` —— Obsidian 配置（换电脑克隆后插件与外观设置都在）

## 内容更新记录

> 每次摄入资料、新增内容都记在这里，**最新的在最上面**。
> 完整操作流水（含维护、同步等）见 [vision-wiki/wiki/log.md](vision-wiki/wiki/log.md)。
> 每条记录末尾 `[@设备]` 标注录入/上传设备。

### 2026-09

- **09-03 ｜ 摄入 · 硬件（传感器）**：基恩士 **LJ-X8000 系列 2D/3D 线激光测量仪**（光切断法 3D 轮廓，3200 点/轮廓，10 种探头量程 X 8~720mm）[@公司机]
  - 传感器页：[Keyence-LJ-X8000系列](vision-wiki/wiki/hardware/sensors/Keyence-LJ-X8000系列.md)
  - 原始存档：[产品样本 PDF（52页）](vision-wiki/raw/datasheets/Keyence-LJ-X8000系列-2D3D线激光测量仪-产品样本.pdf)

- **09-03 ｜ 摄入 · 硬件 + 综合分析**：埃科光电 **TS21MCXP12-230M/C** 相机（CXP-12 ／ 2100 万像素 ／ 231fps 全局快门）+《相机实验对比》PPT（21MP vs 24MP 景深实拍） [@公司机]
  - 相机页：[TS21MCXP12-230M](vision-wiki/wiki/hardware/cameras/TS21MCXP12-230M.md)
  - 对比实验：[21MP对比24MP-相机景深实验](vision-wiki/wiki/synthesis/21MP对比24MP-相机景深实验.md)（结论：小像元 + 低倍率景深更大，拍 PCB 高处元件/丝印更清晰）
  - 原始存档：[规格书 PDF](vision-wiki/raw/datasheets/TS21MCXP12-230M%28C%29%20产品规格书.pdf) ｜ [实验 PPT](vision-wiki/raw/articles/相机实验对比-21MP对比24MP.pptx)

- **09-03 ｜ 同步**：知识库纳入 git 并推送 GitHub（本仓库），配置 `.gitignore`，Obsidian 设置随仓库同步。 [@公司机]
- **09-03 ｜ 维护**：知识库维护者切换为 Codex，新增 [AGENTS.md](vision-wiki/AGENTS.md) 入口，家规与工作流不变。 [@公司机]

### 2026-08

- **08-19 ｜ 摄入 · 硬件**：大恒图像 **MARS-2442-192X2M-NF** 工业相机（CoaXPress 2.0 ／ 2440 万像素 ／ 192 fps 全局快门黑白） [@公司机]
  - 内容：核心规格表、选型要点、适用场景、配套清单，附光谱响应曲线与配件图
  - 知识页：[MARS-2442-192X2M-NF.md](vision-wiki/wiki/hardware/cameras/MARS-2442-192X2M-NF.md)
  - 原始存档：[datasheet](vision-wiki/raw/datasheets/MARS-2442-192X2M-NF.md)
- **08-19 ｜ 建库**：搭建 `vision-wiki/` 三层结构（raw / wiki / assets），写入家规 CLAUDE.md、知识总览、项目页五栏目模板（关键参数 / 硬件 BOM / 踩坑 root cause / 客户约定 / 代码位置）。 [@公司机]

---

*待摄入：算法与算子笔记、项目经验、视觉系统搭建、论文与 datasheet……*
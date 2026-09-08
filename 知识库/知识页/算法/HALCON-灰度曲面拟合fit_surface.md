---
title: "HALCON 灰度曲面拟合算子 fit_surface_first/second_order"
type: 算法/算子
tool: HALCON（Foundation 模块）
tags: [算法, 算子, HALCON, 曲面拟合, 平面度, 灰度矩, 基准面, 去倾斜]
ingested: 2026-09-08
---

# HALCON 灰度曲面拟合 — fit_surface_first_order / fit_surface_second_order

对区域内灰度值（高度/深度图可当 real 图传入）拟合曲面，最小化灰度与曲面距离，输出曲面系数。常用于**基准面拟合、平面度、去倾斜、翘曲/弯曲分析**。

## 两个算子
| 算子 | 阶数 | 曲面方程 | 输出参数 |
|---|---|---|---|
| `fit_surface_first_order` | 一阶（平面） | f(r,c) = Alpha·(r−R) + Beta·(c−C) + Gamma | Alpha, Beta, Gamma |
| `fit_surface_second_order` | 二阶（曲面） | f = Alpha·(r−R)² + Beta·(c−C)² + Gamma·(r−R)(c−C) + Delta·(r−R) + Epsilon·(c−C) + Zeta | Alpha…Zeta（6 个） |

- R、C = 输入区域与图像域相交部分的**中心坐标**。
- 签名：`fit_surface_first_order(Regions, Image : : Algorithm, Iterations, ClippingFactor : Alpha, Beta, Gamma)`（二阶多 Delta/Epsilon/Zeta）。
- 配套 `gen_image_surface_first_order` / `gen_image_surface_second_order`：由系数生成曲面图，可用来做背景/基准面减除。

## 拟合算法 Algorithm
| 取值 | 方法 | 适用 |
|---|---|---|
| `regression` | 标准最小二乘，所有点等权 | 数据干净、无离群 |
| `huber` | 加权最小二乘，降低离群点影响 | 有少量毛刺/异常 |
| `tukey` | 加权，直接忽略离群点 | 离群多、有缺陷点/焊锡尖刺干扰 |

- `ClippingFactor`：截断因子（标准差缩放），**越小剔除离群越多**；默认 2.0，可选 1.0/1.5/2.0/2.5/3.0。
- `Iterations`：离群检测迭代次数，默认 5；`regression` 时忽略。

## 一阶 vs 二阶怎么选
- **基准面 / 安装倾斜校正 / 平面度**（工件基本是平面）→ `first_order` 拟合平面，相减看残差。
- **工件本身弯曲/翘曲、弧形面、来料有曲面趋势** → `second_order`。
- 原则：**能用一阶不用二阶**——二阶会把真实缓慢起伏也拟合掉，可能掩盖缺陷；先看残差再定阶数。
- 参数物理意义：一阶 Alpha/Beta = 行/列方向斜率（倾斜量）；二阶 Alpha/Beta/Gamma = 曲率（翘曲/弯曲）。

## 典型应用（机器视觉）
- **3D/高度图基准面**：高度图转 real 传入 → 拟合平面/曲面后减除 → 平面度、共面度、焊锡/元件相对高度。
- **光照背景不均校正**：拟合灰度渐变面后相减。
- **倾斜/翘曲量化**：直接读斜率、曲率系数。

## 注意
- **只考虑传入的 Regions，忽略 Image 上已设的 domain**（`reduce_domain` 不算，要显式传 region）。
- 图像类型：byte / uint2 / direction / cyclic / real；高度图用 **real**。
- 可重入、全局多线程安全；tuple 层与内部数据层自动并行。
- 相关算子：`moments_gray_plane`（灰度矩平面，更简更快）、`gen_image_surface_*`。

## 原始文档
- [fit_surface_first_order 算子中文文档](../../原始资料/文章/fit_surface_first_order.zh.md)
- [fit_surface_second_order 算子中文文档](../../原始资料/文章/fit_surface_second_order.zh.md)

# fit_surface_second_order（算子）

**Name（名称）**

`fit_surface_second_order` — 计算灰度矩并用二阶曲面进行逼近。

**Signature（签名）**

```hdevelop
fit_surface_second_order(Regions, Image : : Algorithm, Iterations, ClippingFactor : Alpha, Beta, Gamma, Delta, Epsilon, Zeta)
```

> 其他语言绑定（C / C++ / .NET / Python）的重载形式此处略，参数顺序与含义一致。

---

**Description（描述）**

算子 `fit_surface_second_order` 计算输入区域的**灰度矩**，并计算用于逼近这些灰度值的二阶曲面参数。计算方法为**最小化灰度值与曲面之间的距离**。

二阶曲面由下式给出：

$$
f(r, c) = \text{Alpha} \cdot (r - R)^2 + \text{Beta} \cdot (c - C)^2 + \text{Gamma} \cdot (r - R)(c - C) + \text{Delta} \cdot (r - R) + \text{Epsilon} \cdot (c - C) + \text{Zeta}
$$

其中 `r`、`c` 是图像坐标，`R`、`C` 是输入区域与完整图像域相交部分的**中心坐标**。通过上述最小化过程即可求得从 `Alpha` 到 `Zeta` 的六个参数。

**拟合算法**可通过 `Algorithm` 参数选择：

- **`'regression'`**：标准的"最小二乘"拟合。
- **`'huber'`**：加权"最小二乘"拟合，按 Huber 方法降低离群点的影响。
- **`'tukey'`**：加权"最小二乘"拟合，按 Tukey 方法直接忽略离群点。

参数 `ClippingFactor`（标准差的一个缩放因子）控制对离群点的抑制程度：`ClippingFactor` 越小，识别出的离群点越多。离群点的检测是**迭代进行**的，`Iterations` 参数指定迭代次数。如果 `Algorithm` 设为 `'regression'`，则 `Iterations` 参数被忽略。

---

**Attention（注意）**

注意：算子 `fit_surface_second_order` **仅考虑给定的 `Regions`**，而**忽略**输入图像 `Image` 上先前设置的 domain（定义域）。

---

**Execution Information（执行信息）**

- 多线程类型：可重入（可与非排他算子并行运行）。
- 多线程作用域：全局（可从任意线程调用）。
- 在 tuple 层级上自动并行。
- 在内部数据层级上自动并行。

---

**Parameters（参数）**

| 名称 | 类型 | 说明 |
|---|---|---|
| `Regions`（input_object） | region(-array) → object | 要处理的区域。 |
| `Image`（input_object） | singlechannelimage → object（byte / uint2 / direction / cyclic / real） | 对应的灰度值图像。 |
| `Algorithm`（input_control） | string | 拟合算法。**默认：** `'regression'`。**取值列表：** `'huber'`、`'regression'`、`'tukey'`。 |
| `Iterations`（input_control） | integer | 最大迭代次数（`'regression'` 时不使用）。**默认：** 5。**限制：** `Iterations >= 0`。 |
| `ClippingFactor`（input_control） | real | 用于消除离群点的截断因子。**默认：** 2.0。**取值列表：** 1.0、1.5、2.0、2.5、3.0。**限制：** `ClippingFactor > 0`。 |
| `Alpha`（output_control） | real(-array) → (double) | 逼近曲面的参数 Alpha（对应 $(r-R)^2$ 项系数）。 |
| `Beta`（output_control） | real(-array) → (double) | 逼近曲面的参数 Beta（对应 $(c-C)^2$ 项系数）。 |
| `Gamma`（output_control） | real(-array) → (double) | 逼近曲面的参数 Gamma（对应 $(r-R)(c-C)$ 项系数）。 |
| `Delta`（output_control） | real(-array) → (double) | 逼近曲面的参数 Delta（对应 $(r-R)$ 项系数）。 |
| `Epsilon`（output_control） | real(-array) → (double) | 逼近曲面的参数 Epsilon（对应 $(c-C)$ 项系数）。 |
| `Zeta`（output_control） | real(-array) → (double) | 逼近曲面的参数 Zeta（常数项）。 |

---

**Result（结果）**

如果输入的是带定义灰度值（`'byte'`）的图像，且参数正确，算子 `fit_surface_second_order` 返回值 `2`（`H_MSG_TRUE`）。如有必要会抛出异常。

---

**Possible Successors（可能的后续算子）**

- `gen_image_surface_second_order`

**See also（参见）**

- `moments_gray_plane`
- `fit_surface_first_order`

---

**Module（模块）**

Foundation

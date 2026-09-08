---
title: "线扫相机采集卡配置（CameraLink Full + Matrox Grablink/MultiCam）"
type: 硬件/采集卡
tags: [硬件, 采集卡, 线扫相机, CameraLink, Matrox, Grablink, MultiCam]
ingested: 2026-09-08
---

# 线扫相机采集卡 — CameraLink Full + Matrox Grablink（配置要点）

华睿（hqvision）线扫相机 + Matrox Grablink 采集卡（MultiCam 驱动）配置记录。

## 相机端参数
| 参数 | 设置 | 说明 |
|---|---|---|
| OutputMode | Full8Outputs8bit | 采集卡分 base/Medium/full，行频从低到高；≥25K 行频用 full |
| SensorMode | SensorMode2S | 2 线型号选 2S；2SB = binning（分辨率降低） |
| MultiLineGain | X1 | 提 Gain 可增亮度但牺牲画质 |
| SynchroMode | ExtTrigExpVar | 外触发 + 曝光定时（ExposureTime 设曝光）；ExtTrigExpMax = 按触发脉宽曝光 |
| 参数保存 | UserSetSave / Load | currentuserset 显示当前用户组 |

## 采集卡端（Matrox MultiCam）
| 参数 | 设置 | 说明 |
|---|---|---|
| Hactive_Px | 8192 | 图像宽度 |
| LineRate_HZ | 80K | 相机最大行频 |
| TapConfiguration | full_8T8 | tap 数须与采集卡一致 |
| TapGeometry | 8X | — |

## 硬件接线（CameraLink Full 卡，外部 I/O 为 3 排 26pin）
- **IIN1+/IIN1−**：4 组，TTL 电平（5/12/24VDC）→ 任一组作**帧信号**
- **DIN1+/DIN1−**：2 组，差分信号 → 任一组作**行信号**（接编码器）

## 中文操作文档
- [线扫相机采集卡参数设置](../../../原始资料/规格书/Matrox采集卡手册/线扫相机采集卡参数设置.pdf)
- [线扫相机的硬件接线](../../../原始资料/规格书/Matrox采集卡手册/线扫相机的硬件接线.pdf)
- [Multicam Studio 操作说明](../../../原始资料/规格书/Matrox采集卡手册/Multicam%20Studio%20操作说明.docx)

## Matrox 官方手册（MultiCam / Grablink，英文）
- [MultiCam User Guide 用户指南](../../../原始资料/规格书/Matrox采集卡手册/D402EN-MultiCam_User_Guide-6.18.0.4039.pdf)
- [Acquisition Principles 采集原理](../../../原始资料/规格书/Matrox采集卡手册/D405EN-MultiCam_Acquisition_Principles-6.18.0.4039.pdf)
- [Grablink Functional Guide 功能指南](../../../原始资料/规格书/Matrox采集卡手册/D411EN-Grablink_Functional_Guide-6.18.0.4039.pdf)
- [Grablink Parameters 参数](../../../原始资料/规格书/Matrox采集卡手册/D412EN-Grablink_Parameters-6.18.0.4039.pdf)
- [Grablink Hardware Manual 硬件手册](../../../原始资料/规格书/Matrox采集卡手册/D413EN-Grablink_Hardware_Manual-6.18.0.4039.pdf)
- [MultiCam API References 接口](../../../原始资料/规格书/Matrox采集卡手册/D403EN-MultiCam_API_References-6.18.0.4039.pdf) ｜ [Sample Programs 示例](../../../原始资料/规格书/Matrox采集卡手册/D404EN-MultiCam_Sample_Programs-6.18.0.4039.pdf)

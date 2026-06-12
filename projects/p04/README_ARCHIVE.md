# P04 项目存档说明

> 项目已终止。本文档说明存档内容、研究历程和终止原因。
> 封存时间：2026-06-12

---

## 项目概要

**标题**: 南极海冰骤降对南大洋涡动能的调制作用——τ_eff 机制

**核心问题**: 2016 年南极海冰骤降后，海冰屏蔽效应减弱是否导致有效风应力（τ_eff）和南大洋涡动能（EKE）系统性增强？

**结果**: 假说未被验证。因数据时间跨度的根本性限制，因果链无法建立。

**合作者**: Tim（执行人）、张肚肚（合作人）

---

## 研究结论（诚实摘要）

| 问题 | 答案 |
|------|------|
| τ_eff 是否增加？ | 是（+16%，放大因子 2.3×）——机制有物理合理性 |
| W 是否预测 EKE？ | 是（Granger p=0.0004）——风能做功确实传递到涡流 |
| τ_eff 是否预测 EKE？ | 否（Granger p=0.064）——直接因果路径不显著 |
| EKE 和海冰突变时序？ | EKE在2013年，SIC在2016年——**因果倒挂** |
| 回归中τ_eff系数符号？ | **负（β=-0.18）**——与假设相反 |
| 能量循环（CK→EKE）？ | 不成立（Granger p=0.93） |
| 临界点不可逆性？ | 无法验证——仅8年后数据 |

**终止根本原因**: 后 2016 仅 8 年数据 + EKE 突变早于 SIC 突变 + 87% 方差未解释。

---

## 存档内容

```
P04_ARCHIVE/
├── README_ARCHIVE.md           ← 本文件
│
├── analysis/                   ← 分析代码与输出
│   ├── p04_phase1_regression.py    # Phase 1: EKE多元回归归因
│   ├── p04_taueff_spatial.py       # τ_eff 空间分析
│   ├── p04_phase2_mdt.py           # Phase 2: MDT Lorenz能量循环
│   ├── p04_tipping_point.py        # 临界点检测（Pettitt+CSD+PCA）
│   ├── p04_final_chain.py          # 证据链闭合（Granger+分段趋势）
│   ├── p04_analysis.py             # 旧版D0分析（保留备查）
│   ├── P04-Phase2-Summary-CN.md    # 能量循环总结
│   ├── P04_TippingPoint_Chain_CN.md# 完整证据链报告
│   ├── DATA_MANIFEST.md            # 数据来源清单
│   ├── p04_timeseries.pkl/.csv     # Phase 1 输出
│   ├── p04_energy_cycle.pkl/.csv   # Phase 2 输出
│   ├── p04_mdt_fields.npz          # MDT梯度场
│   ├── p04_regression_results.txt  # 回归结果
│   └── p04_rolling_regression.npz  # 滚动回归
│
├── figures/                    ← 全部图表（22张PNG）
│   ├── p04_fig_timeseries.png       # EKE/W/τ_eff 时序
│   ├── p04_fig_regression_coeffs.png# 回归系数
│   ├── p04_fig_taueff_spatial.png   # τ_eff空间分布
│   ├── p04_fig_energy_timeseries.png# Lorenz能量循环
│   ├── p04_fig_tipping_point.png   # 临界点证据（3面板+CSD）
│   ├── p04_fig_evidence_chain.png  # 证据链合成图
│   └── ...（共22张）
│
├── data/                       ← 原始数据（需另行下载或复制）
│   ├── CMEMS-SSH/                  # CMEMS L4 SLA (.nc)
│   ├── ERA5/                       # ERA5风场+海冰 (.nc/.zip)
│   ├── NSIDC Sea Ice Index/        # 南极海冰范围 (.csv)
│   └── climate-indices/            # AAO/Niño3.4/PDO/SOI (.txt)
│
├── manuscript/                 ← 手稿草稿
│   └── v1_ai_draft/                # LaTeX初稿 + PDF + 字体
│
├── methodology/                ← 方法设计文档 (.pdf)
├── refs/                       ← 文献整理（notes.md）
└── logs/                       ← 运行日志（空）
```

---

## 复现说明

如要复现分析，需要：

1. **下载原始数据**（参见 `analysis/DATA_MANIFEST.md` 获取下载链接）：
   - CMEMS DUACS L4 SSH（1993-2024，月均，0.125°）
   - ERA5 月平均风场 + 海冰浓度（1940-2024）
   - CNES-CLS18 MDT
   - NSIDC 海冰指数 + CPC 气候指数

2. **运行分析脚本**（按顺序）：
   ```
   p04_taueff_spatial.py      → τ_eff空间分析
   p04_phase1_regression.py   → EKE回归
   p04_phase2_mdt.py          → Lorenz能量循环
   p04_tipping_point.py       → 临界点检测
   p04_final_chain.py         → 证据链闭合
   ```

3. **运行环境**：Python 3.7+，依赖 numpy / xarray / scipy / matplotlib / pandas / h5netcdf

---

## 关键文件说明

| 文件 | 说明 |
|------|------|
| `DIRECTION.md` | 研究方向定义与终止原因详细说明 |
| `README.md` | GitHub 仓库 README（含状态和评估） |
| `COLLABORATION.md` | 合作者协议（Tim + 张肚肚） |
| `refs/notes.md` | 结构化文献整理（15+篇，按类别） |

---

## 存档元数据

| 项 | 内容 |
|---|---|
| 存档日期 | 2026-06-12 |
| GitHub 分支 | `p04-d1` (github.com/Lujunkui/OpenSCI-Oceanone) |
| 项目总大小 | 约 3.5 GB（含原始数据） |
| 许可证 | CC-BY 4.0 |
| 免责声明 | 本研究结论为基于现有数据和方法的阶段性发现，不构成对"南极海冰临界点"假说的最终判定 |

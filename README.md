# SigContour Pro · 流速处理与湍流参数化工作台

[![Latest Release](https://img.shields.io/badge/release-v2.1.0-0071E3)](https://github.com/hurys20/SigContour-Pro/releases/latest)
[![Platform](https://img.shields.io/badge/platform-macOS%20(Apple%20Silicon%20arm64)-1D1D1F)](https://github.com/hurys20/SigContour-Pro/releases/latest)

**SigContour Pro** 是面向声学多普勒流速剖面仪（Nortek Signature AD2CP / ADCP）的数据处理、质量控制、多尺度频谱解算与水动力湍流参数化桌面软件。

---

## 下载与安装（macOS）

请前往本仓库 **[Releases 页面](https://github.com/hurys20/SigContour-Pro/releases/latest)** 下载最新版本的 macOS 磁盘镜像安装包：

- **最新安装包**：[`SigContour-Pro-v2.1.0-macOS-arm64.dmg`](https://github.com/hurys20/SigContour-Pro/releases/download/v2.1.0/SigContour-Pro-v2.1.0-macOS-arm64.dmg)
- **安装步骤**：双击挂载 `.dmg` 镜像，将 **`SigContour Pro.app`** 拖入 **`Applications`（应用程序）** 文件夹即可启动。

---

## 核心功能模块（M1 – M6 递进工作流）

1. **M1 · 数据导入与配置**
   - 支持 `.ad2cp`（支持多分卷自动拼接）、`.mat` 与 `.nc` 原始数据导入及 `.cfg` 采样配置解析；
   - 支持波束坐标（BEAM）、仪器坐标（XYZ）与地理坐标（ENU）双向正交变换及 WMM2025 磁偏角（$\delta$）地磁校正；
   - 内置**地图主流测角**工具（默认 $\theta = 0^\circ$，测角应用后自动在仪器与采样参数栏更新主流方位角 $\theta$）。
2. **M2 · 传感器与质控**
   - 展示全周期压力水深、旁瓣物理上限、纵横摇倾角、罗盘航向与四波束仰角余弦 $\cos\theta_z$；
   - 一键对全时段各脉冲组（Burst / 采样窗）与全部水层依次执行 QARTOD 质量控制及 Goring & Nikora (2002) 3D 相空间椭球去尖峰，并在全周期时序图（图 a）显式标记存在剔除水层的剖面时刻（`❌`），支持按脉冲组与水层联动查看单层时序及 3D 庞加莱相空间椭球分布。
3. **M3 · 流场云图与剖面**
   - 东向流速 $E$、北向流速 $N$、主流向流速 $V_s(\theta)$ 与垂向流速 $W$ 四维流场剖面云图；
   - 支持鼠标悬停实时联动右侧瞬时垂向流速剖面（$E, N, V_s$）与双波束垂向流速对比剖面（$W_1, W_2$），点击即可固定指定时刻剖面。
4. **M4 · 频谱与小波分析**
   - 导入或切换通道后首先在图 (a) 预览待分析流速时序；
   - 点击「解算频谱」后，解算 Lomb–Scargle / Welch 功率谱密度（图 b）、顺逆时针旋转谱（图 c）与 Morlet 连续小波时频能谱（图 d），并可按需勾选叠加显著周期重构曲线。
5. **M5 · 湍流与参数化（按数据物理条件动态开放）**
   - **仅含平均流剖面数据**：自动锁定高频耗散子项，开放**平均流剖面与底边界层剪切参数化**（时均流速剖面 $\langle E, N, V_s\rangle(z)$、垂向剪切率 $S^2(z)$、冯·卡门对数壁面律拟合摩阻流速 $u_*$ / 粗糙高度 $z_0$ / 底部拖曳系数 $C_d$、混合长涡粘系数 $A_z(z)$ 及底床切应力时序 $\tau_b/\rho(t)$）；
   - **含高频脉冲流数据（4Hz 四波束 Burst 或 8Hz 第五波束 HR）**：开放二阶结构函数法耗散率 $\varepsilon_{\mathrm{SF}}$、惯性耗散法耗散率 $\varepsilon_{\mathrm{IDM}}$、波-湍分离（iSWT / SWT / PH）及垂向涡扩散系数 $K_z$ 参数化；
   - 支持直接导出基础转换数据（`.mat` / `.csv` / `.nc`）。
6. **M6 · 数据与图表导出**
   - 支持导出基础转换数据（`.mat` / `.csv` / `.nc`）、质控后全水层数据表（`.nc` / `.csv` / `.xlsx`）与数据字段字典（`Data_Dictionary.md`）；
   - 支持预览并导出中英文出版级高分辨率（600 DPI PNG + 矢量 PDF）科研论文配图。

# 新 4+1 光路模型 · 515 nm Standard

[在线打开](https://vforvan.github.io/galvo-5d-optical-path-explorer/) · [下载 Zemax 镜片与装配资料](docs/reference/zemax-candidates-import.zip)

当前为 new-4p1-layered-spherical-v3：前置短 Z、αβ / XY 安装模块、内部回折与侧伸出光。四个单轴振镜和一个直线调焦轴；5D 逆解与补偿未接入。

- 真实 KPC040AR.14、KPX100AR.14、KPX181AR.14 与 Corning 7980 平板处方已接入球面折射。
- Z 透镜前顶点间距约 100.153 mm，全行程安装包络约 118.93 mm。
- 零位近轴束腰约 9.840 μm；焦点 Z±1 mm 时约 8.743–10.922 μm。几何 RMS 半径与近轴束腰直径分别报告。
- 当前 4 个振镜、7 个固定折转；αβ 与 XY 分开安装但仍有光学耦合，尚未完成最少镜面设计和 Standard 全域验收。
- 切角、净反射区、电机、导轨及支架为明确标注的工程预留，采样通光不代表布局可制造。

最少核心检查、上下调焦及小角度浏览器交互已通过。原始/派生镜片 ZMX、八个折射界面 CSV 和全局装配数据随页面提供；整机 Coordinate Break 与 OpticStudio 仿真尚未验证。

本公开仓库保持产物用途；完整源码、文档和模型归档提交到私有 galvo-5d-digital-twin 的 optical-path-explorer 子目录，源码提交为 0ffc953。更新前公开页面保留在 [历史页](docs/archive/2026-10-12-before-v3/index.html)，旧数值仅对应当时研究模型。

[MIT](LICENSE)

# Zemax 实物镜片导入资料

三份 `KPC040AR.14.zmx`、`KPX100AR.14.zmx`、`KPX181AR.14.zmx` 是 Newport 厂家原始文件，保留下载字节不变。来源 URL 与 SHA-256 在 `manifest.json`，厂家规格快照在 `*-source.json`。

三个 `*-515-nbk7-geometry.zmx` 是本项目派生文件：波长条目设为 0.515 μm，按产品页材料改为 SCHOTT N-BK7，净半径改为厂家最小保证值，移除未配套的 ZEC_AR-14 镀膜引用。它们用于几何/像差起步，不模拟厂家真实镀膜；未在 OpticStudio 中打开验证。

可在 Zemax 内置 `NEWPORT CORP.ZMF` 中查找料号；目录不含相同后缀时，插入这里的厂家文件或派生文件，只取两个物理界面。原文件的物面和像面距离不作为整机空气间隔。

- `surface-prescriptions.csv`：三片透镜与保护窗共八个物理界面，曲率、Conic、厚度、材料、净半径和机械半径。
- `catalog.json`：商品参数、515 nm 近轴 EFL/BFL、资料来源。这三片及平板处方已接入网页球面追迹。
- `manifest.json`：来源、原始文件哈希、派生修改记录。
- `*-source.json`：官方公开产品接口的原始规格和资源地址。

保护窗候选 Edmund #72-416 尚无已下载厂家 ZMX。CSV 的平行平板参数可手动录入，材料必须使用 Corning 7980 的厂家色散，不能以未知玻璃替代后声称等价。

完整说明见随包的 [选型、导入与空间评估](guide.md)，项目文档原件为 [真实选型与空间评估](../../docs/zemax-catalog-and-packing.md)。这些真实处方已接入 v3，尚未提供经过 OpticStudio 验证的整机折叠文件。

`assembly-layout-v3.json` 与 `folded-surfaces-v3.csv` 是当前全局装配位置、方向及界面顺序；不是可直接运行的整机 ZMX。目录内 KPC037/KPX108 属于前一版保留下载，不属于当前处方。

# 真实选型、Zemax 导入与空间评估

当前 v3 已把真实厂家球面处方接入追迹。布局、尺寸、RMS 和 Z 稳定性见 [v3 设计](layered-optical-design-v3.md)，不是冻结 BOM。

| 用途 | 厂家料号 | R1 / R2（mm） | CT（mm） | 外径 / 最小净径（mm） |
|---|---|---|---|---|
| 移动负镜 | Newport KPC040AR.14 | −25.840 / ∞ | 2.5 | 25.4 / 22.86 |
| 固定正镜 | Newport KPX100AR.14 | 77.520 / ∞ | 4.047 | 25.4 / 22.86 |
| 聚焦单片起点 | Newport KPX181AR.14 | 39.070 / ∞ | 12.383 | 50.8 / 45.72 |
| 保护窗 | Edmund #72-416 | ∞ / ∞ | 3 | 50 / 45 |

三片为 N-BK7、球面 Conic=0、AR.14（430–700 nm）；平板材料为 Corning 7980、VIS 0°（425–675 nm）。聚焦单片不是 precSYS 原扫描物镜。厂家球面形状与边厚/倒角的机械轮廓尚需图纸，不将全外径曲面延拓当作完整 CAD。

## 原始文件与派生修改

[导入目录](../reference/zemax-candidates/README.md) 的原始 ZMX 保持下载字节不变，来源 URL、日期和 SHA-256 见 `manifest.json`。处方曲率和中心厚度已核对。当前选型表以 KPC040 / KPX100 取代 v2 的 KPC037 / KPX108；目录保留旧下载，但它们没有接入 v3。

原厂文件含物/像面示例距离、波长 546.1 nm、旧 BK7 材料标识及 ZEC_AR-14 镀膜数据库引用。原文件 DIAM 是外形半径。515 nm 几何副本仅修改波长、依据厂家 N-BK7 规范替换材料、使用厂家最小净半径并移除未配套镀膜引用；曲率和中心厚度保持不变。副本不模拟实际镀膜透过率，尚未在 OpticStudio 中打开验证。

按 [Ansys Lens Catalogs 文档](https://ansyshelp.ansys.com/public/Views/Secured/Zemax/v242/en/OpticStudio_User_Guide/OpticStudio_Help/topics/Lens_Catalogs.html)，可在 Libraries → Stock Parts → Lens Catalogs 中选择 `NEWPORT CORP.ZMF` 并按料号定位。安装版本不同，后缀和料号覆盖可能不同；缺少时插入厂家 ZMX 的两个物理界面，不继承原厂示例物/像面空气距离。

八个物理界面在 `surface-prescriptions.csv`，商品与色散在 `catalog.json`。保护窗没有已下载厂家 ZMX，按两个平行界面和 3 mm 厚度录入，使用 [Corning 7980 原厂色散](https://www.corning.com/media/worldwide/csm/documents/HPFS_7980_Germicidal_Irradiation.pdf)，不能随意替换材料后称为相同处方。

`assembly-layout-v3.json` 和 `folded-surfaces-v3.csv` 包含整机位置、法线及界面顺序，便于建立 Coordinate Break 或非序列装配；它们不是可直接运行的完整整机 ZMX，尚未验证坐标变换和整域像差。

## 机械结论

当前位姿已筛查电机、镜托、镜筒、全行程移动镜座、模块底板和立柱的保守盒，以及光线穿过电机圆柱、短接头、支架盒和意外镜面的情况。零位没有未声明的盒相交，最小壁面余量 5 mm。底板与立柱、导轨与滑台的预期接触单列为安装关系。

箱壁 3 mm、每边镜托 2 mm、背部 8 mm、镜筒单边 3 mm 均为工程预留。SAT 指标不是实际圆柱间隙，页面的采样通光不代表制造可行。旋转全域、公差、完整镜架、电机和 Z 机构型号、线缆与冷却尚未冻结。

# 数据开发

> 爬虫技术、数据处理、ETL、地理信息系统（GIS）数据的完整知识库

另有详细爬虫指南：`memory/topics/web_scraping.md` (2333行)

---

## 目录

- [GIS数据下载源](#gis数据下载源)
  - [官方数据门户](#官方数据门户)
  - [卫星影像数据](#卫星影像数据)
  - [地形/DEM数据](#地形dem数据)
  - [行政区划/矢量数据](#行政区划矢量数据)
  - [开源数据源](#开源数据源)
  - [国内数据源](#国内数据源)
- [GIS数据处理工具](#gis数据处理工具)
  - [GDAL命令行工具](#gdal命令行工具)
  - [Python地理空间处理](#python地理空间处理)
  - [遥感数据处理软件](#遥感数据处理软件)
  - [国产GIS软件](#国产gis软件)
- [典型处理流程](#典型处理流程)
- [Python工具链详解](#python工具链详解)
- [GitHub热门开源项目](#github热门开源项目)

---

## GIS数据下载源

### 官方数据门户

#### USGS Earth Explorer
- **网址**: https://earthexplorer.usgs.gov/
- **数据**: Landsat全系列（Landsat 1-9超过50年历史数据）、SRTM DEM、ASTER、EO-1等
- **特点**: 全球最大免费卫星数据源，注册后可免费下载，支持按区域/时间/云量筛选
- **下载格式**: GeoTIFF、HDF、NetCDF

#### ESA Copernicus Open Access Hub
- **网址**: https://scihub.copernicus.eu/
- **数据**: Sentinel-1（SAR雷达）、Sentinel-2（光学10m多光谱）、Sentinel-3（海洋/大气）、Sentinel-5P（大气）
- **特点**: 欧空局官方分发，Sentinel-2免费光学影像最佳来源，支持API批量下载
- **替代站点**: https://dataspace.copernicus.eu/（新界面，推荐）

#### NASA EarthData
- **网址**: https://earthdata.nasa.gov/
- **数据**: MODIS、ASTER、VIIRS、SMAP、GPM降雨数据、ICESat-2冰川数据
- **特点**: NASA官方数据平台，包含大量陆地/海洋/大气数据，支持EarthData Search图形界面

#### OpenStreetMap
- **网址**: https://www.openstreetmap.org/
- **数据**: 全球矢量道路、建筑、POI、水系、行政边界等
- **下载方式**:
  - 直接下载: https://www.openstreetmap.org/export
  - Geofabrik分区域下载: https://download.geofabrik.de/（推荐，全球/各洲/各国切片）
  - Overpass API: https://overpass-turbo.eu/（在线查询）
  - OSM Extracts: https://extract.bbbike.org/（自定义区域）

---

### 卫星影像数据

#### Sentinel系列（ESA）
| 卫星 | 主要用途 | 分辨率 | 重访周期 |
|------|---------|--------|---------|
| Sentinel-1A/1B | SAR雷达影像 | 5-20m | 6天 |
| Sentinel-2A/2B | 光学多光谱 | 10/20/60m | 5天 |
| Sentinel-3 | 海洋/陆地温度/高光谱 | 300m-1km | 1-2天 |
| Sentinel-5P | 大气化学成分 | 7km | 每天 |

#### Landsat系列（USGS）
| 卫星 | 分辨率 | 波段 | 数据质量 |
|------|--------|------|---------|
| Landsat 1-5 MSS/TM | 30-80m | 多光谱 | 历史档案 |
| Landsat 7 ETM+ | 15-30m | 全色+多光谱 | 有条带丢失 |
| Landsat 8 OLI | 15-30m | 11波段 | 当前主力 |
| Landsat 9 OLI-2 | 15-30m | 11波段 | 最新一代 |

#### MODIS（NASA）
- **数据产品**: 地表温度、植被指数NDVI/EVI、海洋叶绿素、气溶胶、积雪覆盖
- **分辨率**: 250m-1km（多级别产品）
- **下载**: https://ladsweb.modaps.eosdis.nasa.gov/ 或 EarthData

#### ASTER（USGS/日本）
- **特点**: 15个波段，涵盖VNIR/SWIR/TIR，高光谱分辨率
- **下载**: EarthExplorer，需注册
- **用途**: 矿物填图、热异常监测、高程数据提取

---

### 地形/DEM数据

#### SRTM（NASA/USGS）
- **分辨率**: SRTM1（约30m，美国本土）/ SRTM3（约90m全球）
- **下载源**:
  - USGS EarthExplorer: https://earthexplorer.usgs.gov/
  - CGIAR SRTM: https://srtm.csi.cgiar.org/（拼接校正版）
  - OpenTopography: https://opentopography.org/（高分辨率DEM）

#### ALOS World 3D（Japan JAXA）
- **分辨率**: 5m（全球）
- **免费**: 需注册JAXA账户
- **网址**: https://www.eorc.jaxa.jp/ALOS/en/aw3d30/

#### Copernicus GLO-30（EU）
- **分辨率**: 30m，全球覆盖（含极地）
- **来源**: https://registry.opendata.aws/copernicus-dem-30m/

#### NASADEM（NASA）
- **分辨率**: 30m，基于SRTM+ASTER插值优化
- **来源**: USGS EarthExplorer或NASA Open Data

#### 中国DEM数据
- **地理空间数据云**: https://www.gscloud.cn/（SRTM/ASTER GDEM/叶面积指数等）
- **alos_dem数据包**: 5m分辨率，国内数据较全

---

### 行政区划/矢量数据

#### GADM（全球）
- **网址**: https://gadm.org/download_world.html
- **内容**: 全球所有国家的行政区划边界（国/省/市/区县多级）
- **格式**: Shapefile、GeoPackage、R、KMZ
- **版本**: GADM 4.1（2023年更新）
- **特点**: 免费用于非商业用途，多级嵌套，数据质量高

#### Natural Earth（美国）
- **网址**: https://www.naturalearthdata.com/downloads/
- **比例尺**: 1:10m（大）、1:50m（中）、1:110m（小）
- **内容**: 行政边界、人口、陆地/海洋、自然地理要素
- **格式**: ESRI Shapefile、GeoPackage、SQLite
- **特点**: 公共领域（Public Domain），可直接商用

#### Geofabrik OSM Extracts
- **网址**: https://download.geofabrik.de/
- **内容**: OpenStreetMap全球矢量数据按区域切片
- **格式**: ESRI Shapefile、GeoPackage、.pbf（OSM原生格式）
- **特点**: 每日更新，道路/建筑/POI极为详细

#### ISO 3166相关
- **联合国统计司**: https://unstats.un.org/unsd/strategic-partnership/
- **GeoNames**: https://www.geonames.org/（全球地名数据库，含行政区划）

#### 中国国内数据
- **全国地理信息资源目录服务系统**: https://www.webmap.cn/
- **天地图**: https://www.tianditu.gov.cn/（在线地图+数据API）
- **自然资源部标准地图服务**: https://bzdt.ch.mnr.gov.cn/
- **国家基础地理信息中心**: https://www.nsgc.org.cn/
- **国家地球系统科学数据中心**: https://www.geodata.cn/data/

---

### 开源数据源

| 数据源 | 内容 | 网址 | 特点 |
|--------|------|------|------|
| Natural Earth | 全球矢量/栅格制图数据 | naturalearthdata.com | 公共领域，三种比例尺 |
| GADM | 全球行政区划边界 | gadm.org | 多级嵌套，精确度高 |
| Geofabrik | OSM分区域矢量切片 | download.geofabrik.de | 每日更新，详细路网 |
| OpenStreetMap | 全球矢量地图数据 | openstreetmap.org | 社区维护，实时更新 |
| AWS Open Data | 遥感数据集云存储 | registry.opendata.aws | S3免费，Copernicus DEM等 |
| Google Earth Engine | PB级遥感数据云分析 | code.earthengine.google.com | 在线分析，无需下载 |
| SEDAC（NASA） | 人口/经济/政策数据 | sedac.ciesin.columbia.edu | 社会经济数据丰富 |

---

### 国内数据源

#### 遥感影像
| 平台 | 网址 | 数据类型 |
|------|------|---------|
| 中国资源卫星应用中心 | cresda.com | 高分系列(GF1-7)、资源三号(ZY-3)、环境星(HJ) |
| 国家卫星气象中心 | nsmc.org.cn | 风云卫星(FY-2/3/4) |
| 地理空间数据云 | gscloud.cn | SRTM/ASTER GDEM/叶面积指数 |
| 遥感集市 | rainwe.com | 高分影像在线浏览购买 |

#### 国产卫星简介
- **高分系列(GF)**: GF-1(2m全色+8m多光谱)、GF-2(0.8m亚米级)、GF-3(C波段全极化SAR 1-500m)、GF-6(红边波段)
- **资源三号(ZY-3)**: 民用首颗立体测图卫星，2.1m多光谱，前视/后视/正视三相机立体观测，测制1:5万地形图
- **环境一号(HJ)**: CCD多光谱（30m）+超光谱（100m）+IRS红外（150m）
- **风云卫星(FY)**: 气象卫星，FY-2/3静止轨道+极轨，覆盖亚太

#### 天地图（国家基础地理信息中心）
- **网址**: https://www.tianditu.gov.cn/
- **服务**: 矢量/影像/地形三维地图 WMTS服务
- **API**: Web服务接口，支持开发者调用
- **影像级别**: 0-18级（最高0.5m分辨率）
- **特点**: 国内权威地图数据，支持在线API访问

---

## GIS数据处理工具

### GDAL命令行工具

> GDAL(Geospatial Data Abstraction Library) 是GIS领域最核心的栅格/矢量处理库，几乎所有GIS软件都依赖它。**已安装在系统中**。

#### 安装
```bash
sudo apt install gdal-bin python3-gdal
gdalinfo --version  # 验证版本
```

#### 常用命令

**格式转换（gdal_translate）**
```bash
# HDF转GeoTIFF（带压缩和金字塔）
gdal_translate -of GTiff -co "TILED=YES" -co "COMPRESS=LZW" input.hdf output.tif

# 转换并重采样
gdal_translate -of GTiff -tr 30 30 input.tif output_30m.tif

# 设置NoData值
gdal_translate -of GTiff -a_nodata -9999 input.tif output_nodata.tif
```

**添加金字塔/概视图（gdaladdo）**
```bash
# 为TIFF添加多级缩略图（2/4/8/16为缩放级别）
gdaladdo -r average output.tif 2 4 8 16

# LZW压缩金字塔
gdaladdo -r average --config COMPRESS_OVERVIEW LZW output.tif
```

**投影转换/裁剪/镶嵌（gdalwarp）**
```bash
# 投影转换（WGS84 → EPSG:4326）
gdalwarp -t_srs EPSG:4326 input.tif output.tif

# 裁剪（按边界框）
gdalwarp -te 100 30 110 40 input.tif cropped.tif

# 裁剪（按矢量边界 shapefile）
gdalwarp -cutline boundary.shp -crop_to_cutline input.tif cropped.tif

# 多景镶嵌
gdalwarp input1.tif input2.tif mosaic.tif

# 重投影+裁剪+压缩一步到位
gdalwarp -t_srs EPSG:4326 -te 100 30 110 40 -cutline boundary.shp \
  -crop_to_cutline -of GTiff -co "COMPRESS=LZW" input.tif output.tif
```

**等高线提取（gdal_contour）**
```bash
# 从DEM提取10m间隔等高线
gdal_contour -a elev -i 10 dem.tif contour.shp
```

**栅格计算（gdal_calc.py）**
```bash
# NDVI计算 (NIR-Red)/(NIR+Red)，假设NIR=band4, Red=band3
gdal_calc.py -A band4.tif -B band3.tif \
  --outfile=ndvi.tif \
  --calc="(A.astype(float)-B.astype(float))/(A.astype(float)+B.astype(float))"
```

**矢量格式转换（ogr2ogr）**
```bash
# Shapefile → GeoJSON
ogr2ogr -f GeoJSON output.geojson input.shp

# 投影转换
ogr2ogr -t_srs EPSG:4326 output.shp input.shp

# 按属性过滤
ogr2ogr -where "POPULATION > 1000000" cities_filtered.shp cities.shp

# 裁剪矢量（按另一矢量边界）
ogr2ogr -clipsrc clip_boundary.shp output.shp input.shp
```

**合并矢量（ogrmerge.py）**
```bash
# 合并多个shapefile
ogrmerge.py -f "ESRI Shapefile" -o merged.shp input1.shp input2.shp input3.shp
```

**获取栅格信息**
```bash
gdalinfo input.tif          # 详细信息：投影/分辨率/波段/NoData
gdalinfo --version          # GDAL版本
gdalsrsinfo EPSG:4326       # 坐标系详细信息
```

---

### Python地理空间处理

#### 核心依赖安装顺序
> 安装顺序很重要：先装底层C库依赖，再装Python绑定

```bash
# 1. 系统依赖
sudo apt install libgdal-dev gdal-bin python3-gdal
sudo apt install libgeos-dev python3-dev python3-pip
sudo apt install proj-bin libproj-dev
sudo apt install libspatialindex-dev

# 2. Python包（pip安装）
pip install numpy pandas shapely pyproj
pip install fiona rasterio geopandas
```

#### 核心库简介

| 库 | 作用 | 官方文档 |
|----|------|---------|
| **GDAL** | 底层栅格/矢量读写，所有GIS库的基石 | gdal.org |
| **Fiona** | 矢量数据读写（shp/geojson/gpkg/kml等） | fiona.readthedocs.io |
| **Shapely** | 几何对象操作（点/线/面/缓冲/交集） | shapely.readthedocs.io |
| **pyproj** | 坐标投影转换、CRS定义 | pyproj.readthedocs.io |
| **rasterio** | 栅格数据读写，支持numpy数组直接操作 | rasterio.readthedocs.io |
| **GeoPandas** | 矢量数据DataFrame化，pandas风格操作 | geopandas.org |
| **XArray** | 多维数组+坐标标签，适合NetCDF/HDF | xarray.pydata.org |
| ** rasterstats** | 区域统计（zonal statistics） | pythonhosted.org/rasterstats |

#### 代码示例

**坐标投影转换（pyproj）**
```python
from pyproj import Transformer, CRS

# WGS84 → Web Mercator (EPSG:3857)
transformer = Transformer.from_crs("EPSG:4326", "EPSG:3857", always_xy=True)
x_out, y_out = transformer.transform(116.4, 39.9)  # 北京
print(f"Web Mercator: {x_out}, {y_out}")

# 批量转换
import pyproj
wgs84 = pyproj.CRS("EPSG:4326")
web_mercator = pyproj.CRS("EPSG:3857")
transformer = pyproj.Transformer.from_crs(wgs84, web_mercator, always_xy=True)
points = [(116.4, 39.9), (121.5, 31.2)]  # 多个点
results = [transformer.transform(lon, lat) for lon, lat in points]
```

**矢量裁剪栅格（rasterio + geopandas）**
```python
import rasterio
from rasterio.mask import mask
import geopandas as gpd

# 读取矢量边界
gdf = gpd.read_file("boundary.shp")

# 裁剪栅格
with rasterio.open("image.tif") as src:
    out_image, out_transform = mask(src, gdf.geometry, crop=True)
    out_meta = src.meta.copy()
    out_meta.update({
        "height": out_image.shape[1],
        "width": out_image.shape[2],
        "transform": out_transform
    })

with rasterio.open("cropped.tif", "w", **out_meta) as dst:
    dst.write(out_image)
```

**批量重投影（geopandas）**
```python
import geopandas as gpd

gdf = gpd.read_file("china.shp")
gdf_proj = gdf.to_crs("EPSG:3857")  # Web Mercator
gdf_proj.to_file("china_webmercator.shp")
```

**NDVI计算（rasterio + numpy）**
```python
import rasterio
import numpy as np

with rasterio.open("Sentinel2.tif") as src:
    band4 = src.read(4)   # NIR
    band3 = src.read(3)   # Red
    profile = src.profile

ndvi = (band4.astype(float) - band3.astype(float)) / \
       (band4.astype(float) + band3.astype(float))

# 保存NDVI
profile.update(dtype=rasterio.float32, count=1)
with rasterio.open("ndvi.tif", "w", **profile) as dst:
    dst.write(ndvi.astype(rasterio.float32), 1)
```

**DEM坡度坡向分析（richdem）**
```python
import richdem as rd

dem = rd.LoadGDAL("dem.tif")
slope = rd.TerrainAttribute(dem, attribute='slope_radians')
aspect = rd.TerrainAttribute(dem, attribute='aspect')
rd.SaveGDAL("slope.tif", slope)
```

**多景镶嵌（rasterio）**
```python
import rasterio
from rasterio.merge import merge
import glob

files = glob.glob("scene_*.tif")
src_files = [rasterio.open(f) for f in files]
merged, transform = merge(src_files)
out_meta = src_files[0].meta.copy()
out_meta.update({"width": merged.shape[2], "height": merged.shape[1], "transform": transform})

with rasterio.open("mosaic.tif", "w", **out_meta) as dst:
    dst.write(merged)
```

---

### 遥感数据处理软件

#### SNAP（ESA官方，免费）
- **网址**: https://step.esa.int/main/download/snap-download/
- **用途**: Sentinel全系列数据处理、干涉雷达InSAR、大气校正、镶嵌、裁剪
- **特点**: Java跨平台，SNAP Toolbox处理Sentinel数据最权威
- **常用处理流程**: 热噪声去除 → 轨道校正 → 辐射定标 → 地形校正 → 滤波 → 正射校正

#### ENVI（Harris，商业）
- **用途**: 高分影像预处理、图像融合、几何校正、植被指数、分类
- **特点**: 遥感领域最经典软件，IDL语言扩展
- **典型流程**: 正射校正 → 图像融合 → 镶嵌裁剪 → NDVI计算 → 分类

#### PCI Geomatica（PCI，商业）
- **网址**: https://www.pcigeomatics.com/
- **用途**: 遥感图像处理、GIS分析、雷达数据分析
- **特点**: 加拿大出品，自动化处理能力强

#### QGIS（开源）
- **网址**: https://qgis.org/
- **用途**: 桌面GIS、地图制图、矢量/栅格编辑、空间分析
- **特点**: 免费开源，插件生态丰富（Processing框架集成GRASS/SAGA/OTB）

---

### 国产GIS软件

#### SuperMap（超图）
- **网址**: https://www.supermap.com/
- **产品**: iDesktop桌面GIS、iServer发布服务、iClient前端库
- **特点**: 国产商业GIS最强，支持三维GIS、大数据GIS、云GIS

#### MapGIS（中地数码）
- **网址**: https://www.mapgis.com/
- **用途**: 地质/国土行业GIS、地下管网、三维地质
- **特点**: 国产老牌GIS，在国土、地矿行业应用广泛

#### GeoStar（吉奥之星）
- **网址**: https://www.geostar.com.cn/
- **特点**: 武汉大学背景，数字城市/测绘领域

#### CAD矢量数据处理
- **FME (Safe Software)**: 强大的ETL工具，支持700+格式转换
- **QGIS**: 开源免费，处理矢量数据完全够用

---

## 典型处理流程

### 卫星影像处理全流程

```
原始数据下载
    ↓
数据解析（解压/读取元数据）
    ↓
辐射定标（DN → 辐射亮度/反射率）
    ↓
大气校正（消除大气影响，如FLAASH/6S/QUAC）
    ↓
几何校正/正射校正（消除地形/平台姿态误差）
    ↓
投影转换（统一到目标坐标系）
    ↓
图像镶嵌（多景拼接成大区域）
    ↓
图像裁剪（按矢量边界裁出研究区）
    ↓
去云/阴影处理（多时相合成/掩膜）
    ↓
植被指数/波段计算（NDVI/EVI/NDWI等）
    ↓
分类/变化检测（监督/非监督分类）
    ↓
精度验证
    ↓
成果输出（GeoTIFF/NetCDF/数据库/服务）
```

### DEM数据处理流程

```
SRTM/ASTER原始DEM下载
    ↓
格式转换（HDF/原始SRTM → GeoTIFF）
    ↓
投影转换（WGS84 → 目标坐标系）
    ↓
镶嵌（多幅DEM拼接）
    ↓
裁剪（按研究区边界）
    ↓
空洞填补（无数据区插值）
    ↓
投影平滑（去除拼接缝）
    ↓
坡度/坡向/曲率分析
    ↓
山体阴影（Hillshade）
    ↓
等高线生成
    ↓
汇流网络/流域边界提取
    ↓
成果发布
```

### GIS矢量数据处理流程

```
OSM/GADM等原始数据下载
    ↓
格式转换（.osm/pbf → Shapefile/GeoJSON）
    ↓
投影转换（地理坐标系 → 投影坐标系）
    ↓
要素筛选（按属性/空间过滤）
    ↓
拓扑检查（修正悬挂节点/重叠面）
    ↓
融合/简化（按行政边界融合/道路抽稀）
    ↓
与遥感数据配准
    ↓
属性增补（关联人口/经济数据）
    ↓
质量检查（面积检查/边界一致性）
    ↓
成果发布（GeoPackage/SHP/GML/数据库）
```

---

## Python工具链详解

### 环境管理
```bash
# conda环境（推荐，避免GDAL版本冲突）
conda create -n gis python=3.10
conda activate gis
conda install -c conda-forge gdal fiona rasterio geopandas
pip install shapely pyproj rioxarray xarray rasterstats

# 或使用虚拟环境
python3 -m venv gis_env
source gis_env/bin/activate
pip install -r requirements_gis.txt
```

### requirements_gis.txt 示例
```
numpy>=1.24
pandas>=2.0
geopandas>=0.14
rasterio>=1.3
shapely>=2.0
pyproj>=3.6
fiona>=1.9
rioxarray>=0.14
xarray>=2024
rasterstats>=0.6
richdem>=23.0
```

### 常用Python脚本示例

**批量下载Sentinel-2（sentinelsat）**
```python
from sentinelsat import SentinelAPI, geojson_to_fo
from shapely.geometry import box

api = SentinelAPI('username', 'password', 'https://scihub.copernicus.eu/dhus')
# 按区域和时间搜索
footprint = box(116.0, 39.0, 117.0, 40.0).wkt
products = api.query(footprint,
                     date=('20240101', '20240331'),
                     platformname='Sentinel-2',
                     cloudcoverpercentage=(0, 30))
# 下载
api.download_all(products, directory_path='./data/sentinel2')
```

**GDAL Python批量处理**
```python
from osgeo import gdal
import glob

files = glob.glob("hdf/*.hdf")
for f in files:
    out_tif = f.replace(".hdf", ".tif")
    gdal.Translate(out_tif, f,
                    format='GTiff',
                    options=['COMPRESS=LZW', 'TILED=YES'])
```

**并行处理加速（joblib）**
```python
from joblib import Parallel, delayed
import rasterio

def process_tile(tile_path):
    with rasterio.open(tile_path) as src:
        data = src.read(1)
        # 处理逻辑
        pass
    return result

results = Parallel(n_jobs=8)(
    delayed(process_tile)(f) for f in tile_files
)
```

---

## GitHub热门开源项目

### 爬虫框架
- [scrapy/scrapy](https://github.com/scrapy/scrapy) - Scrapy框架（52k stars）
- [binux/pyspider](https://github.com/binux/pyspider) - 国产分布式爬虫（21k stars）
- [cnnotations/DrissionPage](https://github.com/cnnotions/DrissionPage) - 国产浏览器自动化（13k stars）
- [playwright-dev/playwright-python](https://github.com/playwright-dev/playwright-python) - 微软浏览器自动化（11k stars）
- [urllib3/urllib3](https://github.com/urllib3/urllib3) - HTTP客户端

### 异步HTTP
- [aiohttp/aiohttp](https://github.com/aiohttp/aiohttp) - 异步HTTP客户端（13k stars）
- [psf/requests](https://github.com/psf/requests) - 最流行HTTP库（50k stars）

### 代理池
- [jhao104/proxy_pool](https://github.com/jhao104/proxy_pool) - 代理池管理（13k stars）
- [hengyoush/async-proxy-pool](https://github.com/hengyoush/async-proxy-pool) - 异步代理池

### 数据处理
- [pandas-dev/pandas](https://github.com/pandas-dev/pandas) - 数据分析（39k stars）
- [pola-rs/polars](https://github.com/pola-rs/polars) - 高性能DataFrame（28k stars）
- [numpy/numpy](https://github.com/numpy/numpy) - 数值计算（27k stars）

### 地理空间
- [geopandas/geopandas](https://github.com/geopandas/geopandas) - 地理数据pandas（4k stars）
- [pangeo-data/xESMF](https://github.com/pangeo-data/xESMF) - 网格重映射
- [OSGeo/gdal](https://github.com/OSGeo/gdal) - GDAL官方仓库
- [python-visualization/folium](https://github.com/python-visualization/folium) - Leaflet地图可视化
- [mapbox/rasterio](https://github.com/mapbox/rasterio) - 栅格数据读写
- [OpenGIS/ctypesgen](https://github.com/OpenGIS/ctypesgen) - GDAL Python绑定生成
- [SciTools/cartopy](https://github.com/SciTools/cartopy) - 地图投影（1k stars）
- [mapbox/rasterio](https://github.com/mapbox/rasterio) - 栅格IO库

### 自动化测试
- [mitmproxy/mitmproxy](https://github.com/mitmproxy/mitmproxy) - 中间人代理抓包（35k stars）
- [aws/aws-cli](https://github.com/aws/aws-cli) - AWS命令行（14k stars）

### 数据存储
- [sqlalchemy/sqlalchemy](https://github.com/sqlalchemy/sqlalchemy) - ORM（24k stars）
- [redis/redis](https://github.com/redis/redis) - 内存数据库（68k stars）
- [clickhouse/clickhouse](https://github.com/clickhouse/clickhouse) - OLAP数据库（36k stars）

### 调度与工作流
- [PrefectHQ/prefect](https://github.com/PrefectHQ/prefect) - 数据流编排（14k stars）
- [apache/airflow](https://github.com/apache/airflow) - 工作流平台（49k stars）
- [testerSunshine/PPTGen](https://github.com/testerSunshine/PPTGen) - PPT生成

### ETL工具
- [airbytehq/airbyte](https://github.com/airbytehq/airbyte) - 数据集成（14k stars）
- [dbt-labs/dbt-core](https://github.com/dbt-labs/dbt-core) - 数据转换（23k stars）
- [DataHubIO/datahub](https://github.com/DataHubIO/datahub) - 元数据平台（11k stars）

### GIS专题
- [python-visualization/folium](https://github.com/python-visualization/folium) - 交互式地图（Python+Leaflet）
- [mapbox/rasterio](https://github.com/mapbox/rasterio) - 栅格数据处理
- [pyvista/pyvista](https://github.com/pyvista/pyvista) - 3D科学可视化（含GIS应用）
- [Awesome-Satellite-Benchmarks](https://github.com/satellite-image-learning/Awesome-Satellite-Benchmarks) - 卫星影像数据集汇总

---

## 推荐学习路径

### 入门（1-2周）
1. Python基础 + NumPy/Pandas
2. GDAL命令行工具（gdal_translate/warp/ogr2ogr）
3. QGIS桌面操作，熟悉GIS基本概念
4. GeoPandas读写shapefile/geojson

### 进阶（1-2月）
1. 遥感数据处理：SNAP处理Sentinel-1/2数据
2. Python GIS：rasterio + geopandas联合处理
3. 坐标投影：pyproj全掌握
4. 地形分析：richdem/SAGA

### 高级（持续）
1. Google Earth Engine云端大规模处理
2. 深度学习遥感影像分类（U-Net/ResNet）
3. 时序遥感：植被动态监测/变化检测
4. 分布式处理：Dask/RasterFrames

---

## 数据部备注

### 爬虫工具链
```
requests → BeautifulSoup/Playwright → 代理池 → 分布式调度
```

### ETL工具链
```
MySQL/PostgreSQL → SQLAlchemy → Pandas → ClickHouse/Parquet
```

### GIS工具链
```
GDAL/rasterio → GeoPandas → PostgreSQL(PostGIS) → QGIS/MapServer
```

### 当前项目参考
- **星际争霸数据采集**: https://github.com/xx789123/sc2-data-crawler
- **军用GIS项目**: 地理数据采集+处理+发布的完整链路

---

*最后更新: 2026-04-17 by 数据开发部*

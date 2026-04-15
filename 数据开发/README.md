# 数据部学习资料

> 爬虫技术、数据处理、ETL、地理数据的完整知识库

另有详细爬虫指南：[memory/topics/web_scraping.md](https://github.com/xx789123/tuo-knowledge/blob/main/data.md) (2333行)

## 官方文档

### 爬虫技术
- [Scrapy官方文档](https://docs.scrapy.org/) - 官方英文文档
- [Scrapy中文文档](https://scrapy-chs.readthedocs.io/) - 中文翻译版
- [DrissionPage](https://drissionpage.cn/) - 国产浏览器自动化工具
- [Playwright Python](https://playwright.dev/python/) - 微软浏览器自动化
- [aiohttp文档](https://docs.aiohttp.org/) - 异步HTTP客户端
- [BeautifulSoup文档](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) - HTML解析

### 数据处理
- [pandas官方文档](https://pandas.pydata.org/docs/) - 数据分析库
- [Polars](https://pola.rs/) - 高性能DataFrame库
- [NumPy中文](https://numpy.org.cn/) - 数值计算
- [Dask](https://dask.org/) - 大规模数据处理

### 地理数据
- [GDAL官方](https://gdal.org/) - 地理数据处理库
- [GeoPandas文档](https://geopandas.org/) - 地理数据pandas
- [Cesium中文](https://cesium.cn/) - 三维地球平台
- [Rasterio](https://rasterio.readthedocs.io/) - 栅格地理数据处理
- [Shapely](https://shapely.readthedocs.io/) - 几何操作

### APP抓包
- [mitmproxy文档](https://docs.mitmproxy.org/) - 中间人代理
- [Frida文档](https://frida.re/docs/) - 动态插桩工具
- [Charles Proxy](https://www.charlesproxy.com/) - HTTP代理抓包

### 反爬与代理
- [反爬策略与应对](https://www.scrapingdog.com/blog/how-to-bypass-bot-detection/) - 反爬教程
- [Proxy Pool开源](https://github.com/jhao104/proxy_pool) - 开源代理池
- [快代理](https://www.kuaidaili.com/) - 代理IP服务
- [芝麻代理](https://www.zmhttp.com/) - 代理IP服务

### 验证码识别
- [pytesseract](https://pypi.org/project/pytesseract/) - OCR识别
- [ddddocr](https://github.com/sml2h3/ddddocr) - 通用验证码识别
- [EasyOCR](https://github.com/JaidedAI/EasyOCR) - 多语言OCR

### 数据可视化
- [Matplotlib中文](https://www.matplotlib.org.cn/) - Python绑图
- [Pyecharts](https://pyecharts.org/) - 中文图表库
- [Plotly](https://plotly.com/python/) - 交互图表
- [Altair](https://altair-viz.github.io/) - 声明式可视化

## 核心技能

### 爬虫架构分层
```
采集层:
  - requests: 静态页面
  - aiohttp: 异步采集
  - Scrapy: 框架级爬虫
  - Playwright: 动态渲染页面
  - DrissionPage: 国产无头浏览器

解析层:
  - BeautifulSoup: HTML解析
  - lxml: XML/HTML高速解析
  - parsel: Scrapy内置解析器
  - regex: 正则表达式

存储层:
  - MySQL: 结构化数据
  - MongoDB: 非结构化数据
  - Redis: 缓存/代理池
  - CSV/JSON: 轻量级存储

调度层:
  - cron: 定时任务
  - Airflow: 工作流编排
  - Prefect: 现代数据流水线
```

### Scrapy项目结构
```
myproject/
├── myproject/
│   ├── __init__.py
│   ├── items.py          # 数据模型
│   ├── middlewares.py    # 中间件
│   ├── pipelines.py      # 管道(清洗/存储)
│   ├── settings.py       # 配置
│   └── spiders/
│       ├── __init__.py
│       └── example.py    # 爬虫
├── scrapy.cfg
└── requirements.txt
```

### 数据清洗标准流程
```
1. 缺失值处理
   - 删除: 缺失比例 > 30%
   - 填充: 数值型用均值/中位数，类别型用众数
   - 标记: 单独建一列标记缺失

2. 重复值去重
   - 完全重复: drop_duplicates()
   - 部分重复: 根据业务键判断

3. 格式标准化
   - 日期格式统一: YYYY-MM-DD
   - 字符串去空格/统一大小写
   - 数值类型转换

4. 异常值检测
   - 3σ原则 (正态分布)
   - IQR法则 (四分位距)
   - 业务逻辑判断

5. 数据转换
   - 类别编码: LabelEncoder / OneHotEncoder
   - 标准化: StandardScaler / MinMaxScaler
   - 特征工程: 派生特征
```

### GDAL常用命令
```bash
# 格式转换
gdal_translate -of GTiff -co "TILED=YES" -co "COMPRESS=LZW" input.hdf output.tif

# 添加金字塔
gdaladdo -r average output.tif 2 4 8 16

# 投影转换
gdalwarp -t_srs EPSG:4326 input.tif output.tif

# 裁剪
gdalwarp -cutline border.shp -crop_to_cutline input.tif output.tif
```

## 工具推荐

### 数据采集
- [Octoparse](https://www.octoparse.com/) - 无代码爬虫
- [ParseHub](https://www.parsehub.com/) - 可视化爬虫
- [WebScraper](https://webscraper.io/) - 浏览器插件爬虫

### 数据处理
- [OpenRefine](https://openrefine.org/) - 数据清洗工具
- [Trifacta](https://www.trifacta.com/) - 数据准备平台

### ETL工具
- [Airflow](https://airflow.apache.org/) - Airbnb数据流水线
- [Prefect](https://www.prefect.io/) - 现代数据流水线
- [Dagster](https://dagster.io/) - 数据编排平台

---
*由坨坨维护 · 2026-04-15 · 更新*

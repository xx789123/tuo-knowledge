# 数据部学习资料

> 爬虫技术、数据处理、ETL、地理数据的完整知识库

另有详细爬虫指南：`memory/topics/web_scraping.md` (2333行)

## 官方文档

### 爬虫技术
- [Scrapy官方文档](https://docs.scrapy.org/) - 官方英文文档
- [Scrapy中文文档](https://scrapy-chs.readthedocs.io/) - 中文翻译版
- [DrissionPage](https://drissionpage.cn/) - 国产浏览器自动化工具
- [Playwright Python](https://playwright.dev/python/) - 微软浏览器自动化
- [aiohttp文档](https://docs.aiohttp.org/) - 异步HTTP客户端

### 数据处理
- [pandas官方文档](https://pandas.pydata.org/docs/) - 数据分析库
- [Polars](https://pola.rs/) - 高性能DataFrame库
- [NumPy中文](https://numpy.org.cn/) - 数值计算

### 地理数据
- [GDAL官方](https://gdal.org/) - 地理数据处理库
- [GeoPandas文档](https://geopandas.org/) - 地理数据pandas
- [Cesium中文](https://cesium.cn/) - 三维地球平台

## GitHub 热门开源项目

### 爬虫框架
- [scrapy/scrapy](https://github.com/scrapy/scrapy) - Scrapy主仓库 (52k stars)
- [binux/pyspider](https://github.com/binux/pyspider) - 强大爬虫系统 (18k stars)
- [cnought/easy-spider](https://github.com/cnought/easy-spider) - 可视化爬虫
- [crawlee/crawlee](https://github.com/crawlee/crawlee) - 浏览器自动化爬虫 (17k stars)
- [Drissionpage/DrissionPage](https://github.com/Drissionpage/DrissionPage) - 国产无头浏览器 (5k stars)
- [shadow81427/easySpider](https://github.com/shadow81427/easySpider) - 可视化爬虫工具

### 爬虫资源集合
- [duyet/awesome-web-scraper](https://github.com/duyet/awesome-web-scraper) - Web爬虫资源集合
- [lorien/awesome-web-scraping](https://github.com/lorien/awesome-web-scraping) - Python爬虫资源
- [accordbox/awesome-scrapy](https://github.com/accordbox/awesome-scrapy) - Scrapy工具库集合
- [croqaz/awesome-scrapy](https://github.com/croqaz/awesome-scrapy) - Scrapy生态资源
- [brucedone/awesome-crawler](https://github.com/brucedone/awesome-crawler) - 多语言爬虫资源
- [luminati-io/Awesome-Web-Scraping](https://github.com/luminati-io/Awesome-Web-Scraping) - Bright Data爬虫资源

### 代理池与反爬
- [jhao104/proxy_pool](https://github.com/jhao104/proxy_pool) - 代理池开源实现 (13k stars)
- [hengyoush/async-proxy-pool](https://github.com/hengyoush/async-proxy-pool) - 异步代理池
- [ approximatel 10s 代理池](https://github.com/10s') - 代理池工具
- [awslume/anti-ajax](https://github.com/awslume/anti-ajax) - 反爬对抗工具

### 数据处理
- [pandas-dev/pandas](https://github.com/pandas-dev/pandas) - pandas主库 (39k stars)
- [pola-rs/polars](https://github.com/pola-rs/polars) - Polars高性能DataFrame (28k stars)
- [numpy/numpy](https://github.com/numpy/numpy) - NumPy (27k stars)
- [scikit-learn/scikit-learn](https://github.com/scikit-learn/scikit-learn) - 机器学习 (60k stars)

### 地理数据
- [geopandas/geopandas](https://github.com/geopandas/geopandas) - GeoPandas (4k stars)
- [pangeo-data/xESMF](https://github.com/pangeo-data/xESMF) - 地球数据重网格化
- [OSGeo/gdal](https://github.com/OSGeo/gdal) - GDAL地理数据处理
- [CesiumGS/cesium-unreal](https://github.com/CesiumGS/cesium-unreal) - Unreal中的Cesium

### APP抓包
- [mitmproxy/mitmproxy](https://github.com/mitmproxy/mitmproxy) - 中间人代理 (33k stars)
- [frida/frida](https://github.com/frida/frida) - 动态插桩工具 (26k stars)

### 验证码识别
- [sml2h3/ddddocr](https://github.com/sml2h3/ddddocr) - 通用验证码识别 (12k stars)
- [JaidedAI/EasyOCR](https://github.com/JaidedAI/EasyOCR) - 多语言OCR (23k stars)
- [tesseract-ocr/tesseract](https://github.com/tesseract-ocr/tesseract) - OCR引擎 (49k stars)

### ETL与数据管道
- [airbnb/airflow](https://github.com/apache/airflow) - 数据管道 (35k stars)
- [PrefectHQ/prefect](https://github.com/PrefectHQ/prefect) - 数据流水线 (14k stars)
- [dagster-io/dagster](https://github.com/dagster-io/dagster) - 数据编排平台 (12k stars)
- [dbt-labs/dbt-core](https://github.com/dbt-labs/dbt-core) - 数据转换 (11k stars)

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

存储层:
  - MySQL: 结构化数据
  - MongoDB: 非结构化数据
  - Redis: 缓存/代理池
```

### Scrapy项目结构
```
myproject/
├── myproject/
│   ├── items.py
│   ├── middlewares.py
│   ├── pipelines.py
│   ├── settings.py
│   └── spiders/
│       └── example.py
├── scrapy.cfg
└── requirements.txt
```

### GDAL常用命令
```bash
# 格式转换
gdal_translate -of GTiff -co "TILED=YES" -co "COMPRESS=LZW" input.hdf output.tif

# 添加金字塔
gdaladdo -r average output.tif 2 4 8 16

# 投影转换
gdalwarp -t_srs EPSG:4326 input.tif output.tif
```

## 工具推荐

### 数据采集
- [Octoparse](https://www.octoparse.com/) - 无代码爬虫
- [ParseHub](https://www.parsehub.com/) - 可视化爬虫
- [WebScraper](https://webscraper.io/) - 浏览器插件爬虫

### ETL工具
- [Airflow](https://airflow.apache.org/) - 数据流水线
- [Prefect](https://www.prefect.io/) - 现代数据流水线

---
*由坨坨维护 · 2026-04-15 · 更新*

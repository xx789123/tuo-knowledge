# 数据部学习资料

## 官方文档

### 爬虫技术
- [Scrapy文档](https://docs.scrapy.org/) - 官方文档
- [DrissionPage](https://drissionpage.cn/) - 国产浏览器自动化
- [Playwright](https://playwright.dev/python/) - 微软浏览器自动化
- [aiohttp](https://docs.aiohttp.org/) - 异步HTTP
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) - HTML解析

### 数据处理
- [pandas文档](https://pandas.pydata.org/docs/) - 数据分析库
- [Polars](https://pola.rs/) - 高性能DataFrame
- [NumPy中文](https://numpy.org.cn/) - 数值计算

### 地理数据
- [GDAL](https://gdal.org/) - 地理数据处理
- [GeoPandas](https://geopandas.org/) - 地理数据pandas
- [Cesium中文](https://cesium.cn/) - 三维地球

### APP抓包
- [mitmproxy](https://docs.mitmproxy.org/) - 中间人代理
- [Frida](https://frida.re/docs/) - 动态插桩

### 反爬与代理
- [反爬策略与应对](https://www.scrapingdog.com/blog/how-to-bypass-bot-detection/) - 反爬教程
- [Proxy Pool](https://github.com/jhao104/proxy_pool) - 开源代理池
- [快代理](https://www.kuaidaili.com/) - 代理IP服务

### 验证码识别
- [pytesseract](https://pypi.org/project/pytesseract/) - OCR识别
- [ddddocr](https://github.com/sml2h3/ddddocr) - 通用验证码识别

### 数据可视化
- [Matplotlib中文](https://www.matplotlib.org.cn/) - Python绑图
- [Pyecharts](https://pyecharts.org/) - 中文图表库
- [Plotly](https://plotly.com/python/) - 交互图表

## 核心技能

### 爬虫架构
```
采集层: requests / aiohttp / Scrapy / Playwright
解析层: BeautifulSoup / lxml / parsel
存储层: MySQL / MongoDB / Redis / CSV
调度层: cron / Airflow / Prefect
```

### 数据清洗流程
1. 缺失值处理
2. 重复值去重
3. 格式标准化
4. 异常值检测
5. 数据转换

---
*由坨坨维护 · 2026-04-15*

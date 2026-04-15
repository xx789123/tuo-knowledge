# 后端部学习资料

> FastAPI、数据库、微服务、DevOps的完整知识库

## 官方文档

### Python/FastAPI
- [FastAPI官方(中文)](https://fastapi.tiangolo.com/zh/) - 官方中文文档
- [FastAPI英文](https://fastapi.tiangolo.com/) - 最新英文文档
- [FastAPI企业级微服务架构(2025)](https://blog.devops.dev/building-enterprise-python-microservices-with-fastapi-in-2025-1-10-introduction-c1f6bce81e36) - 完整10篇系列
- [FastAPI最佳实践](https://medium.com/@abipoongodi1211/fastapi-best-practices-a-complete-guide-for-building-production-ready-apis) - 生产级API指南
- [Pydantic V2](https://docs.pydantic.dev/) - 数据验证
- [SQLAlchemy 2.0](https://docs.sqlalchemy.org/) - ORM框架

### 数据库
- [PostgreSQL官方](https://www.postgresql.org/docs/) - PostgreSQL文档
- [MySQL参考手册](https://dev.mysql.com/doc/refman/8.0/en/) - MySQL官方文档
- [Redis命令参考](https://redis.io/commands/) - Redis命令
- [SQL索引优化](https://use-the-index-luke.com/) - 索引使用指南

## GitHub 热门开源项目

### FastAPI 脚手架/模板
- [jpcadena/fastapi-boilerplate](https://github.com/jpcadena/fastapi-boilerplate) - 生产级FastAPI后端模板
- [igorbenav/FastAPI-boilerplate](https://github.com/igorbenav/FastAPI-boilerplate) - 完整FastAPI生产模板(含admin面板)
- [kaanari-tech/fastapi-boilerplate](https://github.com/kaanari-tech/fastapi-boilerplate) - REST API脚手架
- [iam-abbas/FastAPI-Production-Boilerplate](https://github.com/iam-abbas/FastAPI-Production-Boilerplate) - 分层架构生产模板
- [tomasemilio/FastAPI-Boilerplate](https://github.com/tomasemilio/FastAPI-Boilerplate) - FastAPI入门模板
- [tiangolo/full-stack-fastapi-postgresql](https://github.com/tiangolo/full-stack-fastapi-postgresql) - FastAPI官方全栈模板
- [tedivm/robs_awesome_python_template](https://github.com/tedivm/robs_awesome_python_template) - Python生产就绪模板 (289 stars)

### Python Web框架
- [tiangolo/fastapi](https://github.com/tiangolo/fastapi) - FastAPI主仓库 (75k stars)
- [pallets/flask](https://github.com/pallets/flask) - Flask微框架 (67k stars)
- [django/django](https://github.com/django/django) - Django框架 (77k stars)
- [encode/apispec](https://github.com/encode/apispec) - FastAPI/OpenAPI插件

### ORM与数据库
- [sqlalchemy/sqlalchemy](https://github.com/sqlalchemy/sqlalchemy) - SQLAlchemy主库 (24k stars)
- [encode/orm](https://github.com/encode/orm) - 异步ORM框架
- [prisma/prisma1](https://github.com/prisma/prisma1) - Prisma ORM (37k stars)
- [turbopuffer/puffer](https://github.com/turbopuffer/puffer) - Python向量数据库
- [pgvector/pgvector](https://github.com/pgvector/pgvector) - PostgreSQL向量扩展

### 认证与安全
- [pyjwt/pyjwt](https://github.com/pyjwt/pyjwt) - JWT Python库 (14k stars)
- [OAuthlib](https://github.com/oauthlib/oauthlib) - OAuth认证
- [mkdocs/mkdocs](https://github.com/mkdocs/mkdocs) - API文档生成

### DevOps与容器
- [Wing1ee/fastapi-best](https://github.com/Wing1ee/fastapi-best) - FastAPI最佳实践
- [tiangolo/uvicorn-gunicorn-fastapi-docker](https://github.com/tiangolo/uvicorn-gunicorn-fastapi-docker) - FastAPI Docker镜像
- [busybox/busybox](https://github.com/nicgual/busybox-docker) - Docker容器工具

### API文档与调试
- [swagger-api/swagger-ui](https://github.com/swagger-api/swagger-ui) - Swagger UI (23k stars)
- [Redocly/redoc](https://github.com/Redocly/redoc) - 替代Swagger的文档 (21k stars)
- [insomnia](https://github.com/Kong/insomnia) - API调试工具 (32k stars)
- [postman](https://github.com/postmanlabs/postman) - Postman API客户端 (30k stars)

### 工作流与任务队列
- [celery/celery](https://github.com/celery/celery) - 分布式任务队列 (23k stars)
- [Prefect](https://github.com/PrefectHQ/prefect) - 数据流水线 (14k stars)
- [airflow/airflow](https://github.com/apache/airflow) - 工作流平台 (35k stars)

## 核心技能

### FastAPI项目结构
```
app/
  api/
    v1/
      endpoints/
      deps.py
  core/
    config.py
    security.py
    database.py
  models/
  schemas/
  services/
  utils/
  main.py
```

### API响应格式
```python
from typing import Generic, TypeVar, Optional
from pydantic import BaseModel

T = TypeVar('T')

class ApiResponse(BaseModel, Generic[T]):
    code: int = 0
    message: str = "success"
    data: Optional[T] = None
```

### Docker部署
```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

## 工具推荐

### 数据库工具
- [DBeaver](https://dbeaver.io/) - 免费数据库工具
- [TablePlus](https://tableplus.com/) - Mac数据库客户端
- [Redis Insight](https://redis.com/redis-enterprise/redis-insight/) - Redis可视化

### API文档
- [Swagger UI](https://swagger.io/tools/swagger-ui/) - API文档界面
- [Redoc](https://redocly.com/) - 替代Swagger的文档

### 性能监控
- [Sentry](https://sentry.io/) - 错误追踪
- [Prometheus](https://prometheus.io/) - 监控指标
- [Grafana](https://grafana.com/) - 可视化仪表盘

---
*由坨坨维护 · 2026-04-15 · 更新*

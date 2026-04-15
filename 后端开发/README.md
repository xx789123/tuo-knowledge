# 后端部学习资料

> FastAPI、数据库、微服务、DevOps的完整知识库

## 官方文档

### Python/FastAPI
- [FastAPI官方(中文)](https://fastapi.tiangolo.com/zh/) - 官方中文文档
- [FastAPI英文](https://fastapi.tiangolo.com/) - 最新英文文档
- [FastAPI企业级微服务架构(2025)](https://blog.devops.dev/building-enterprise-python-microservices-with-fastapi-in-2025-1-10-introduction-c1f6bce81e36) - 完整10篇系列
- [FastAPI最佳实践](https://medium.com/@abipoongodi1211/fastapi-best-practices-a-complete-guide-for-building-production-ready-apis) - 生产级API指南
- [FastAPI架构设计](https://zyneto.com/blog/best-practices-in-fastapi-architecture/) - 可扩展API设计模式
- [FastAPI微服务性能](https://talent500.com/blog/fastapi-microservices-python-api-design-patterns-2025/) - 异步高性能
- [Pydantic V2](https://docs.pydantic.dev/) - 数据验证
- [SQLAlchemy 2.0](https://docs.sqlalchemy.org/) - ORM框架

### 数据库
- [PostgreSQL官方](https://www.postgresql.org/docs/) - PostgreSQL文档
- [MySQL参考手册](https://dev.mysql.com/doc/refman/8.0/en/) - MySQL官方文档
- [Redis命令参考](https://redis.io/commands/) - Redis命令
- [MongoDB文档](https://www.mongodb.com/docs/) - MongoDB官方
- [SQL索引优化](https://use-the-index-luke.com/) - 索引使用指南

### 安全
- [OWASP Top 10 (2025)](https://owasp.org/Top10/zh-cn/) - Web应用安全
- [OAuth2.0](https://oauth.net/2/) - 授权框架
- [JWT.io](https://jwt.io/) - JSON Web Token
- [Passlib](https://passlib.readthedocs.io/) - 密码哈希

### DevOps
- [Docker官方文档](https://docs.docker.com/) - 容器化
- [Kubernetes中文](https://kubernetes.io/zh-cn/) - K8s官方
- [Docker Compose](https://docs.docker.com/compose/) - 多容器编排
- [GitHub Actions](https://docs.github.com/actions) - CI/CD
- [Nginx文档](https://nginx.org/en/docs/) - 反向代理

### 消息队列
- [Kafka文档](https://kafka.apache.org/documentation/) - Kafka入门
- [RabbitMQ教程](https://www.rabbitmq.com/tutorials/) - 官方教程
- [Redis Streams](https://redis.io/docs/data-types/streams/) - 轻量级队列

## 核心技能

### FastAPI项目结构（企业级）
```
app/
  api/
    __init__.py
    v1/
      __init__.py
      router.py
      endpoints/
        user.py
        order.py
      deps.py
  core/
    __init__.py
    config.py
    security.py
    database.py
  models/
    __init__.py
    user.py
    order.py
  schemas/
    __init__.py
    user.py
    order.py
  services/
    __init__.py
    user_service.py
    order_service.py
  utils/
    helpers.py
  main.py
```

### API响应格式规范
```python
from typing import Generic, TypeVar, Optional
from pydantic import BaseModel

T = TypeVar('T')

class ApiResponse(BaseModel, Generic[T]):
    code: int = 0
    message: str = "success"
    data: Optional[T] = None

@router.get("/users/{user_id}")
async def get_user(user_id: int) -> ApiResponse[UserSchema]:
    user = await user_service.get(user_id)
    return ApiResponse(data=user)
```

### 数据库模型示例
```python
from sqlalchemy import Column, Integer, String, DateTime, Boolean
from sqlalchemy.orm import relationship
from sqlalchemy.sql import func
from app.core.database import Base

class User(Base):
    __tablename__ = "users"

    id = Column(Integer, primary_key=True, index=True)
    email = Column(String(255), unique=True, index=True, nullable=False)
    hashed_password = Column(String(255), nullable=False)
    full_name = Column(String(100))
    is_active = Column(Boolean, default=True)
    created_at = Column(DateTime(timezone=True), server_default=func.now())
    updated_at = Column(DateTime(timezone=True), onupdate=func.now())

    orders = relationship("Order", back_populates="owner")
```

### 中间件配置
```python
from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware
from fastapi.middleware.gzip import GZipMiddleware

app = FastAPI()

app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

app.add_middleware(GZipMiddleware, minimum_size=1000)
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

```yaml
version: '3.8'
services:
  api:
    build: .
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=postgresql://user:pass@db:5432/mydb
    depends_on:
      - db
      - redis

  db:
    image: postgres:15
    volumes:
      - postgres_data:/var/lib/postgresql/data

  redis:
    image: redis:7-alpine
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  redis_data:
```

## 工具推荐

### API文档
- [Swagger UI](https://swagger.io/tools/swagger-ui/) - API文档界面
- [Redoc](https://redocly.com/) - 替代Swagger的文档

### 数据库工具
- [DBeaver](https://dbeaver.io/) - 免费数据库工具
- [TablePlus](https://tableplus.com/) - Mac数据库客户端
- [Redis Insight](https://redis.com/redis-enterprise/redis-insight/) - Redis可视化

### 性能监控
- [Sentry](https://sentry.io/) - 错误追踪
- [Prometheus](https://prometheus.io/) - 监控指标
- [Grafana](https://grafana.com/) - 可视化仪表盘

---
*由坨坨维护 · 2026-04-15 · 更新*

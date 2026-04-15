# 后端部学习资料

## 官方文档

### Python/FastAPI
- [FastAPI官方](https://fastapi.tiangolo.com/zh/) - 官方中文文档
- [FastAPI最佳实践](https://medium.com/@abipoongodi1211/fastapi-best-practices-a-complete-guide-for-building-production-ready-apis-bb27062d7617) - 生产级API指南
- [FastAPI架构设计](https://zyneto.com/blog/best-practices-in-fastapi-architecture/) - 架构模式
- [Real Python FastAPI](https://realpython.com/get-started-with-fastapi/) - 入门教程
- [Pydantic V2](https://docs.pydantic.dev/) - 数据验证

### 数据库
- [PostgreSQL文档](https://www.postgresql.org/docs/) - 官方文档
- [MySQL参考手册](https://dev.mysql.com/doc/refman/8.0/en/) - 官方文档
- [Redis命令](https://redis.io/commands/) - 命令参考
- [SQL索引优化](https://use-the-index-luke.com/) - 索引使用

### 安全与DevOps
- [OWASP Top 10](https://owasp.org/Top10/zh-cn/) - Web应用安全
- [Docker文档](https://docs.docker.com/) - 容器化
- [Kubernetes中文](https://kubernetes.io/zh-cn/) - K8s官方

### 消息队列
- [Kafka文档](https://kafka.apache.org/documentation/) - Kafka入门
- [RabbitMQ教程](https://www.rabbitmq.com/tutorials/) - 官方教程

## 核心技能

### API设计规范
- RESTful风格
- 返回格式：`{code, message, data}`
- 统一错误处理
- 分页/排序/筛选

### 项目结构
```
app/
├── api/          # 路由
├── core/         # 核心配置
├── models/       # 数据模型
├── schemas/      # Pydantic模型
├── services/     # 业务逻辑
└── main.py      # 入口
```

---
*由坨坨维护 · 2026-04-15*

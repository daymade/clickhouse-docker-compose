# ClickHouse Docker Setup

这是一个用于在 macOS 上使用 OrbStack 部署 ClickHouse 的 Docker 配置示例。

## 目录结构

```
clickhouse-docker-setup/
├── docker-compose.yml
├── config.d/
├── users.d/
├── docker-entrypoint-initdb.d/
├── data/               # 数据目录（不纳入版本控制）
└── logs/               # 日志目录（不纳入版本控制）
```

## 使用步骤

1. **克隆仓库**

    ```bash
    git clone git@github.com:daymade/clickhouse-docker-compose.git
    cd clickhouse-docker-compose
    ```

2. **创建数据和日志目录**（可选）

    ```bash
    mkdir -p data
    mkdir -p logs
    ```

3. **配置 ClickHouse**（可选）

    - 在 `config.d/` 和 `users.d/` 目录下添加自定义配置文件。

4. **启动 ClickHouse 容器**

    ```bash
    docker-compose up -d
    ```

5. **验证 ClickHouse 是否运行正常**

    ```bash
    echo 'SELECT version()' | curl 'http://localhost:18123/' --data-binary @-
    ```

## 参考文档

- [ClickHouse Docker 镜像官方文档](https://hub.docker.com/r/clickhouse/clickhouse-server/)
- [OrbStack 官方文档](https://orbstack.dev/docs)

## 注意事项

- **数据持久化**：数据存储在 `data/` 目录，日志存储在 `logs/` 目录。请勿将这些目录纳入版本控制。
- **安全性**：默认配置允许来自所有 IP 地址的连接，并且 `default` 用户没有密码。仅用于测试环境，请在生产环境中进行适当的安全配置。

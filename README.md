# 📦 Docker Compose 清单维护仓库

本仓库用于集中管理和维护多服务的 Docker Compose 配置模板，分为 **单实例部署** 与 **集群部署** 两类结构，适配本地开发、测试环境和中小型生产系统。

---

## 📁 仓库结构说明

```bash
compose/
├── single/                          # 单实例测试场景
│   └── service-name/
│       ├── docker-compose.yaml
│       ├── .env
│       └── README.md
├── cluster/                         # 集群高可用场景
│   └── service-name/
│       ├── docker-compose.yaml
│       ├── .env
│       └── README.md
```

- `single/`：适用于简单服务、开发调试或轻量部署场景
- `cluster/`：适用于包含主从、复制、分片或高可用机制的复杂部署架构
- 每个服务一个独立目录，包含 `docker-compose.yaml` 和必要的 `.env`、`README.md` 文件，如需扩展，可再次基础上按需添加配置即可

---

## 🧩 使用与维护规范

### ✅ 文件标准

- 每个服务目录下必须包含：
  - `docker-compose.yaml`
  - `.env`（如使用环境变量）
  - （可选）`README.md`：描述启动步骤、端口信息、注意事项
 

### ✅ 通用变量管理示例

`.env` 示例：

```env
MYSQL_ROOT_PASSWORD=change-me
MYSQL_DATABASE=mydb
```

`docker-compose.yaml` 使用方式：

```yaml
environment:
  - MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
  - MYSQL_DATABASE=${MYSQL_DATABASE}
```

---

## 🚀 快速使用示例

使用过程中：
- 单实例可直接切换到工程目录替换相关参数配置启动容器即可！
- 集群为背景的话，如果是单节点则也和单实例一样，如果是多节点集群背景，则需拆分清单文件中的容器实例到不同节点后进行启动!

通用操作：

```bash
cd compose/single/redis             # 切换单实例工程目录
cd compose/cluster/redis-cluster    # 切换集群工程目录
docker-compose up                   # 启动容器
docker-compose down                 # 停止并移除容器
docker-compose ps                   # 查看服务状态
docker-compose logs -f              # 查看服务日志
```

---

## 🛠️ 推荐目录模板


---

## 🤝 贡献说明

- 欢迎添加更多服务或完善已有模板
- 所有提交需确保 YAML 格式正确、能正常启动
- 如服务需初始化脚本或特殊操作，请写入子目录内的 `README.md`

---

## 👤 维护者

- **作者**：xwone  
- **角色**：运维工程师  
- **邮箱**：zhenw4824@gmail.com

---

> 本项目将持续扩展通用 Compose 模板，并区分单机/集群结构。欢迎贡献 PR 或 Issue！

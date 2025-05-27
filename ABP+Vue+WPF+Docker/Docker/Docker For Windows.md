# SQL Server
## 拉取最新的SQL Server 镜像(# 以管理员身份运行 PowerShell（Windows）或终端（Mac/Linux）)
> docker pull mcr.microsoft.com/mssql/server:latest      # 拉取最新版本（如 2022）

## 查看本机镜像列表
>docker images

## 运行并持久化容器

#### 1. 创建专用数据卷（推荐替代目录挂载）

powershell

复制

下载

# 创建Docker托管卷（避免直接挂载Windows目录）
docker volume create mssql_data

# 运行容器
docker run -d `
--name sqlserver `
-e "ACCEPT_EULA=Y" `
-e "MSSQL_SA_PASSWORD=2624434145@qq.com" `
-p 1433:1433 `
-v mssql_data:/var/opt/mssql `
mcr.microsoft.com/mssql/server:2022-latest

### 二、验证卷位置的步骤

#### 1. 使用 `docker volume inspect` 查看元数据

powershell

复制

下载

docker volume inspect mssql_data

输出示例：

json

复制

下载

[
    {
        "CreatedAt": "2024-06-15T12:34:56Z",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/mssql_data/_data",
        "Name": "mssql_data",
        "Options": null,
        "Scope": "local"
    }
]

- **关键字段**：`Mountpoint` 是容器内的路径（非宿主机路径）。

# 通过ABP CLI的方式创建
##  安装ABP CLI
>dotnet tool install -g Volo.Abp.Cli

### 创建纯后端的项目
> abp new Simulation--template app --ui none --database-provider ef --mobile none

> abp new Simulation --template module --database-provider ef

### 创建MVC/Razor项目
> abp new Simulation -t app
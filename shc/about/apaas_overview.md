# 有关EnOS服务托管中心

EnOS服务托管中心（Service Hosting Center，SHC）提供高性能可伸缩的容器应用管理服务，帮助项目负责人创建和管理应用开发项目、配置集群和容器，并帮助应用开发者快速构建和部署应用。SHC容器服务简化了容器管理集群的搭建工作，打造云端最佳容器运行环境。

## 应用生命周期管理

提供完整的应用生命周期管理功能，包括：

- 创建应用开发项目
- 管理项目成员
- 新建应用，维护应用信息
- 管理应用部署配置和流水线

## 容器服务

提供完善的容器服务，简化容器管理集群的搭建工作，打造应用最佳容器运行环境，包括：

- 部署管理（Deployment和Stateful Set配置）
- 配置管理（Config Map和Secret配置）
- 路由管理（Service和Route配置）
- 存储容量申请（Storage配置）

## DevOps持续交付

支持自动完成从代码提交到应用部署的 DevOps 完整流程，包括：

- 按阶段（Stage）配置任务
- 执行配置的阶段任务
- 查看任务执行结果

## 集群管理

提供集中的集群管理服务，包括：

- 资源配额管理（CPU、内存、Pod配额）
- 网络策略
- 存储资源管理

## 数据库服务

为应用开发提供数据库服务，支持的数据库服务包括：

- Redis
- MySQL
- Mongo

## 丰富的工具集

为应用开发和部署提供丰富的工具集，包括：

- Redmine
- Jenkins
- Gitlab
- SonarQube
- Nexus
- NPM
- Harbor

## 相关角色

EnOS SHC主要服务于以下角色：

**项目负责人**

为提高对多个应用和服务的管理效率，在EnOS SHC中引入了项目的概念。在单个项目中，可创建和管理多个应用。项目负责人根据应用开发的需求，创建和维护应用开发项目的基本信息，创建应用，添加和管理项目成员，管理成员的角色和权限。

**应用开发人员**

应用开发人员包括应用开发、测试、运维等角色。开发人员基于自己的角色，参与对应的应用开发任务，包括维护代码仓库、创建和运行流水线、构建和部署应用等。

## EnOS SHC的相关产品及服务

### 应用开发

使用Enos SDK开发应用程序，并通过EnOS API获取存储的数据。[了解更多 >>](/docs/app-development/zh_CN/latest/app_dev_overview.html)

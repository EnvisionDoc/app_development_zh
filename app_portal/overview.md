# 有关Application Portal

EnOS Application Portal 是通用灵活的权限管理和统一登录门户，它提供给应用开发者一套基于RBAC的统一权限体系和登录门户，同时保证终端用户可以在同一套系统，同一套用户和权限，统一的用户体验下，流畅的访问和使用应用，提高安全控制，降低研发成本。

EnOS Application Portal 是基于EnOS的应用统一登录门户，其系统架构图如下：

.. image:: media/architecture.png



## 主要功能

EnOS Application Portal 的主要功能包括：

- 基于RBAC的权限管理，包括角色、权限、用户组、组织结构等通用能力
- 通过资产管理层级，自动授权客户资产
- 通过子管理员配置，分层分级授权管理
- 开放应用菜单配置，实现用户跨应用访问
- 统一门户和个性化配置，实现多OU切换
- 提供实名认证、多因子认证、和安全等级防护（规划中）

以上功能的实现基于 Application Portal 与 EnOS 应用、资产、权限等模块的交互。Application Portal 按照功能划分可分为应用Portal和管理后台两大模块，本文档从应用开发者、系统管理员、OU管理员、和应用用户的角度，分别介绍 Application Portal 与 EnOS 的交互，以及应用Portal和管理后台两大模块的功能和使用方法。



## 相关角色

EnOS Application Portal 主要服务于以下角色：

**应用开发者**

基于EnOS提供的API和SDK，线下开发应用。应用开发者可以是企业或组织内部的应用开发人员，也可以是第三方应用开发者。应用开发者需对应用做相应的配置，应用才能同步和展示到Application Portal。

**系统管理员**

为企业或组织完成Application Portal的初始化、创建和分配OU管理员，注册插件应用等。

**OU管理员**

企业或组织的IT或系统运维人员。OU管理员通过系统管理员分配的账号，登录Application Portal，进入管理后台，负责企业或组织内应用的分类管理、用户与权限、和资产等的全面管理。

**应用用户**

应用的实际使用者。用户通过OU管理员创建的账号登录Application Portal，使用企业或组织内开发或购买的应用，查看或管理有权限访问的资产，进行经授权的相关的操作。



## 相关服务

### 设备管理

EnOS设备管理服务帮助你快速将物理设备安全连接至EnOS云端并开始数据传输，管理设备周期，及将物理世界的资产结构映射至数字世界。[了解更多 >>](/docs/device-connection/zh_CN/2.0.9/device_management_overview.html)

### 数据资产管理

EnOS数据资产管理服务提供流数据处理、时序数据管理、数据质量、数据订阅等服务。[了解更多 >>](/docs/data-asset/zh_CN/2.0.9/data_asset_overview)

### 应用使能

使用Enos SDK开发应用程序，并通过EnOS API访问EnOS服务和资源。[了解更多 >>](/docs/app-development/zh_CN/2.0.9/app_dev_overview.html)
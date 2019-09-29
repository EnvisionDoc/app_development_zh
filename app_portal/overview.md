# 有关Application Portal

EnOS Application Portal 是通用灵活的权限管理和统一登录门户，它提供给应用开发者一套基于RBAC的统一权限体系和登录门户，同时保证终端用户可以在同一套系统，同一套用户和权限，统一的用户体验下，流畅的访问和使用应用，提高安全控制，降低研发成本。

EnOS Application Portal 是基于EnOS的应用统一登录门户，其系统架构图如下：

.. image:: media/architecture.png

## 主要功能

EnOS Application Portal 的主要功能包括：

1.	基于RBAC的权限管理，包括角色、权限、用户组、组织结构等通用能力
2.	通过资产管理层级，自动授权客户资产
3.	通过子管理员配置，分层分级授权管理
4.	开放应用菜单配置，实现用户跨应用访问
5.	统一门户和个性化配置，实现多OU切换
6.	提供实名认证、多因子认证、和安全等级防护（规划中）

以上功能的实现基于下图所示的完整环节和流程：

.. image:: media/arch.png

Application Portal 按照功能划分可分为应用Portal和管理后台两大模块，本文档从普通用户、OU管理员、和系统管理员的角度，分别介绍这两个模块的功能和使用方法。

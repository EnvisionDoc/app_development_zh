# 管理应用

通过EnOS控制台注册或购买的应用，会被自动同步到Application Portal的应用管理页面。OU管理员可对组织内的应用进行如下管理操作：

- 启用或禁用OU注册或购买的应用
- 分配应用展示的组织结构
- 设置应用的菜单组
- 将应用进行排序
- 创建应用快捷方式

## 前提条件

1. 企业或组织的应用开发者需要预先在EnOS控制台注册应用，创建应用的菜单和权限点。

2. 如果企业或组织购买第三方应用，OU管理员需要在EnOS控制台购买应用。第三方应用开发者收到购买申请后，审批OU购买应用的申请，并授权企业或组织访问应用的菜单和权限。

有关通过EnOS控制台管理应用的详细信息，参考 [管理应用](../../app_management/managing_apps)。

## 启用 / 禁用应用

通过EnOS控制台注册和购买的应用会自动同步到Application Portal的应用管理页面。OU管理员可通过以下步骤启停应用：

1. 进入管理后台，在左侧菜单栏中选择 **应用管理**，打开应用列表。

2. 在列表的 **启用** 列中，滑动开关启用/禁用应用。

   .. image:: ../media/enable_apps.png

应用启用后，OU内拥有该应用权限的人员将能看到该应用；禁用后，OU内全部用户在应用切换列表将看不到该应用，但应用配置的使用权限不变。

## 为应用分配组织结构

为应用分配组织结构后，组织结构内的用户即可使用该应用。通过以下步骤为应用分配组织结构：

1. 在应用列表中找到目标应用，点击 **分配组织结构** 图标。

2. 在弹窗中，选择将应用分配给已经创建好的组织结构，点击 **确认**。

   .. image:: ../media/apps_2.png

## 管理菜单组

通过管理菜单组，可配置应用内需要展示的菜单结构和组合。通过以下步骤管理应用的菜单组：

1. 在应用列表中找到目标应用，点击 **管理菜单组** 图标。

2. 在 **菜单组** 一栏中，点击 + 新建菜单组。

   .. image:: ../media/apps_5.png

3. 对应用内已有菜单组，选择 **重命名** / **删除** 可重命名菜单组或删除菜单组。

   .. image:: ../media/apps_3.png

4. 选中一个菜单组，点击 **配置菜单** 按钮，为该菜单组配置应用内的菜单选项，可多选（勾选了上级菜单，所属下级菜单默认被勾选）。

   .. image:: ../media/apps_4.png

## 应用排序

通过应用排序功能，可调整应用列表中所有应用和应用快捷方式的显示顺序。

1. 在应用列表页面，点击 **应用排序** 按钮。

2. 在弹窗中，拖拽应用名称，对应用进行排序，点击 **确定**。应用列表将按照新的顺序显示应用。

   .. image:: ../media/ordering_apps.png

## 创建应用快捷方式

Application Portal支持创建应用快捷方式，将不同应用的模块或菜单整合在一起，组成新的应用。有关应用快捷方式的详细信息，参考 [创建应用快捷方式](creating_app_shortcut)。

<!-- end -->

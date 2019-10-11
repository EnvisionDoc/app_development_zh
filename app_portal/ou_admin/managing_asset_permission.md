# 管理资产

Application Portal支持与EnOS同步资产信息，并可为已创建的用户和用户组分配资产访问权限，用户即可通过应用看到资产的数据。资产权限管理包括以下步骤：

- 资产同步：将资产数据同步更新到Application Portal
- 为用户或用户组分配资产访问权限

## 资产同步

资产同步是将本组织已接入EnOS并被标签标记的资产（使用 `auth_unit:true` 标签）从EnOS同步到Application Portal。同步完成后，资产才可被分配给用户。

1. 登录Application Portal管理后台，从导航栏中选择 **资产同步**。

2. 点击 **同步资产**，即可将EnOS上的资产数据同步到Application Portal。

   .. image:: ../media/asset_1.png

.. note:: 将资产同步到Application Portal之前，必须在EnOS控制台为待同步的资产或模型标记 auth_unit:true 的标签。



## 资产权限分配 <asset_assign>

为用户或者用户组分配可以管理的资产。设置完成后，用户即可通过应用看到相关资产数据。

1. 登录Application Portal管理后台，从导航栏中选择 **资产权限分配**。

2. 选择用户或用户组可以查看该用户/用户组已被分配的资产。点击 **管理资产**，可将资产批量分配给选定的用户/用户组。

  .. image:: ../media/asset_3.png

3. 点击已分配资产后的 **移除** 图标即可将该资产从用户/用户组移除。

  .. image:: ../media/asset_2.png



<!-- end -->

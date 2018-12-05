# 应用框架快速入门

## 产品介绍

应用框架是EnOS系统为开发者提供的集中管理组织内应用的用户和访问权限的模块，帮助应用开发者和组织管理员高效地管理应用的内外部用户账号、应用资源定义、和访问资源权限分配等。

### 名词解释
**应用**

在EnOS平台上开发并且注册的软件和工具的总称。应用可分为公有应用和组织私有应用。

**公司 、组织**
应用的开发者或者应用所属的机构。在应用框架内，定义公司和组织结构的信息，便于更好地管理应用的用户和相应的权限。

**应用权限**
EnOS系统为开发者提供的应用资源访问控制权限，可将不同的资源授予给不同的用户。应用权限类型可分为菜单、UI视图、和数据。

**系统管理员**
EnOS平台管理员，或大型组织内指定的超级管理员。负责定义公司和组织信息、注册应用、定义应用权限、为公司或组织分配应用、创建组织管理员角色。

**组织管理员**
单个组织内的应用管理员。负责组织内应用的分类管理、管理用户账号、和用户权限。

**用户**
应用的使用者。使用组织管理员分配的用户账号登录应用。

### 产品特征
应用框架产品特征和优势体现在：

**数据集成**：EnOS系统将接入的资产数据、应用、EnOS API进行数据互相集成，保证接入的资产能通过应用授权后，分配给不同的用户使用。

**安全可靠**：EnOS系统对不同客户的数据进行了隔离并采用资产授权方式保证数据安全，只有对应用进行资产主动授权才能让应用访问到自己的资产。

**跨组织应用授权**：当需要授权外部用户访问自己的资源时，可对应用进行资产和权限授权，外部用户通过应用查看资产信息。



## 准备工作

在使用应用框架管理应用的资源权限之前，需要预先对应用做相应的配置，包括定义应用权限、安装EnOS前端SDK配置权限、发布应用。

### 定义应用权限

应用权限是EnOS系统将应用资源定义为应用的访问控制权限，方便将不同的资源授予给不同的用户使用。因此，应用开发者需规划和定义应用的资源和权限。系统管理员或组织管理员需要依据定义的应用权限ID，在应用管理页面中配置应用的权限。

下表是应用权限定义的示例：

| 权限名称               | 权限ID            | 权限类型        |
| ---------------------- | ----------------- | --------------- |
| Monitor 菜单           | menu.monitor      | 菜单（Menu）    |
| Report 菜单            | menu.report       | 菜单（Menu）    |
| Monitor #1 权限        | monitor.1         | UI视图 （View） |
| Monitor #2 权限        | monitor.2         | UI视图 （View） |
| Monitor #3 权限        | monitor.3         | UI视图 （View） |
| Diagnostic Report 按钮 | button.dis_report | UI视图 （View） |
| Generation 字段        | report.generation | 数据（Data）    |
| Severity 字段          | report.severity   | 数据（Data）    |
| Boiler Efficiency 板块 | view.boiler       | 数据（Data）    |
| HP Heater Input Ratio  | view.hp_heater    | 数据（Data）    |
| Condenser Undercooling | view.condenser    | 数据（Data）    |

### 配置应用权限

完成应用权限定义之后，可使用EnOS前端SDK配置应用权限。

#### 安装EnOS前端SDK

EnOS前端SDK发布于npm，下载地址：[http://npm.envisioncn.com/package/@enos/portalsdk](http://npm.envisioncn.com/package/@enos/portalsdk)

使用如下命令安装EnOS前端SDK：

```
npm install @enos/portalsdk --save
```

#### API

应用框架本身提供API，供内部应用调用。应用可以通过前端SDK获取当前用户权限和页面操作等。

API统一挂在portalSdk下，调用API需要先引入SDK模块。

```
import portalSdk from '@enos/portalsdk';
```

API列表和功能的详细介绍，请参考[SDK Readme](http://npm.envisioncn.com/package/@enos/portalsdk)文档。

#### 定义菜单权限

在 App 管理模块新增类型为`Menu`的权限，并为指定用户分配对应的 App 和权限，用户登录后，通过 API `getPermissions` 可获取到其拥有的全部权限，其中包含了配置的 `Menu` 权限。

SDK 提供了 React 版本的 `Menu` 组件，通过输入菜单数据和当前用户权限，提供统一的菜单展示。App 开发者可使用 `Menu` 组件展示菜单，也可根据权限数据自定义展示。

##### Menu 组件的参数

| Property     | Description                    | Type     |
| ------------ | ------------------------------ | -------- |
| menus        | 菜单数据全集，具体格式参考下文 | array    |
| permissions  | 当前用户拥有的权限             | array    |
| onSelectMenu | Menu 选中的回调                | function |
| theme        | 当前主题 Key                   | string   |

##### Menu 组件的使用示例

```
import portalSdk from '@enos/portalsdk';
import Menu from '@enos/portalsdk/lib/Menu';

class Demo extends React.Component {
    render() {
        return (
          <Menu
              menus={customMenu}
              permissions={portalSdk.getPermissions()}
              onSelectMenu={this.onSelectMenu}
              theme={portalSdk.getTheme()} />   );
  }
}

ReactDOM.render(<Demo />, mountNode);
```

##### Menu 组件接收的菜单数据格式

```
[
  {
    id: 'category_admin',
    title: 'Admin',
    children: [
      {
        id: 'app_user_admin_menu_company',
        title: 'Company Mgmt',
        link: '/admin/company.html'
      },
      {
        id: 'app_user_admin_menu_ouadmin',
        title: 'OU Administrator',
        link: '/admin/ouadminlist.html'
      },
      {
        id: 'app_user_admin_menu_sysapp',
        title: 'Sys App Mgmt',
        link: '/admin/sysapp.html'
      }
    ]
  }
]
```

#### 定义UI视图权限

为需要做 `View` 权限控制的元素增加属性 `meta-enos-view-id`，值设置为对应的权限ID。

在 App 管理模块新增类型为 `View` 的权限，并为指定用户分配对应的 App 和权限，权限ID填写为上一步设置的值。

当用户对于某一个 `View` 无权限时，默认不显示该 `View`，如需要为无权限 `View` 保留页面渲染位置，可以为元素添加属性 `meta-enos-view-reserve=‘true’`。

##### 前端元素配置示例

```
 <!-- 完全不显示 -->
 <div meta-enos-view-id='qwerty'>I am control point</div>
 <!-- 保留占位 -->
 <div meta-enos-view-id='qwerty' meta-enos-view-reserve='true'>I am reserved control point</div>
```

#### 定义数据权限

获取数据相关权限列表。

```
portalSdk.getDataPermissions();
```

##### 返回示例

```
[
  {
    "permissionId": 0,
    "elementId": "model.name",
    "permissionName": "model_name",
    "permissionType": 2,
    ...
  },
  {
    "permissionId": 1,
    "elementId": "model.phone",
    "permissionName": "model_phone",
    "permissionType": 2,
    ...
  }
]
```

### 发布应用

完成应用权限配置之后，即可发布应用上线，获取应用URL。系统管理员或组织管理员在应用框架系统中注册应用时，需要输入应用的URL。



## 操作指南

本文通过系统管理员、组织管理员、和用户的角色，介绍如何使用EnOS应用框架管理应用的内外部用户账号、应用资源定义、和访问资源权限分配等。

### 系统管理员

系统管理员一般为EnOS平台管理员，或大型组织内指定的超级管理员。系统管理员负责如下操作：

- 创建公司或组织
- 注册公有应用
- 定义应用权限
- 为公司分配公有应用
- 创建组织管理员账号

#### 创建公司

在应用框架内，通过定义公司和组织，可以更好地管理应用的用户和相应的权限。系统管理员可通过以下步骤，注册公司信息。

1. 使用预先定义的系统管理员账号，登录应用框架，进入系统管理页面。
2. 在页面左侧任务栏，点击**公司管理**。
3. 点击**+公司**按钮，在**新建公司**弹窗内，输入公司名、详细地址、和公司描述。
4. 点击**保存**，完成公司信息注册。

注册完成之后，所有已注册的公司信息会显示在公司管理页面的表格中。在该表格中，可以更新公司状态、编辑公司信息、管理为公司分配的应用，如下图所示。

![](image/company_zh.png)

#### 注册公有应用

平台内的公有应用，根据公司或组织需求，可授权给平台用户使用。系统管理员可通过以下步骤，在框架内注册公有应用。

1. 在系统管理页面左侧任务栏，点击**应用管理**。
2. 点击**+应用**按钮，在**新应用**弹窗内，输入应用名、应用链接、应用描述，选择背景颜色和应用图标。
3. 点击**保存**，完成公有应用注册。

注册完成之后，所有已注册的公有应用和组织私有应用信息会显示在应用管理页面的表格中。在该表格中，可以更新应用状态、编辑应用信息、定义应用权限，如下图所示。

![](image/public_app_zh.png)

#### 定义应用权限

应用权限是EnOS系统将应用资源定义为应用的访问控制权限，方便将不同的资源授予给不同的用户使用。系统管理员可通过以下步骤，定义应用权限。

1. 在系统管理页面左侧任务栏，点击**应用管理**。
2. 在应用列表中，点击选定应用的**权限**图标，打开应用权限管理页面。
3. 点击+权限按钮，在**新权限**弹窗内，输入权限名称、权限ID（必须在web SDK中预先定义）、权限描述，选择权限类型。目前支持如下权限类型：
   - 菜单：菜单类型的应用资源，如下拉菜单、任务栏
   - UI视图：应用页面上的视图资源，如按钮、视频
   - 数据：应用的数据资源，如报表
4. 点击**保存**，完成权限定义。
5. 重复以上操作，定义更多的应用权限。

应用权限定义完成之后，所有已定义的权限信息会显示在权限管理页面的表格中。在该表格中，可以编辑或删除已定义的权限，如下图所示。

![](image/app_permission_zh.png)

#### 为公司分配公有应用

平台内的公有应用可按公司需求，分配给公司用户使用。系统管理员可通过以下步骤，为公司分配公有应用。

1. 在系统管理页面左侧任务栏，点击**公司管理**。

2. 在公司列表中，点击选定公司的**权限**图标，打开公有应用列表。

3. 勾选赋予该公司的公有应用。

4. 点击**保存**，完成应用分配。如下图所示。

   ![](image/assign_app_zh.png)

为公司分配的公有应用将会被列入公司的**应用管理**页面表格中。公司的组织管理员可将分配的公有应用权限开放给用户。

#### 创建组织管理员账号

公司或组织内的应用和权限管理，都需要专有的组织管理员。系统管理员可通过以下步骤，为公司或组织创建组织管理员账号。

1. 在系统管理页面左侧任务栏，点击**OU管理员**。
2. 点击**+添加**按钮，在**新公司管理员**弹窗内，输入用户名、邮箱地址，选择组织管理员所属组织。
3. 点击**保存**，完成组织管理员账号创建。
4. 在组织管理员账号表格中，点击**重置**图标，为创建的账号生成初始密码。

账号创建完成之后，所有已创建的组织管理员账号信息会显示在账号管理页面的表格中。在该表格中，可以编辑或删除账号，或者重置账号密码，如下图所示。

![](image/create_ouadmin_zh.png)

### 组织管理员

组织管理员为单个组织内的应用管理员。组织管理员使用系统管理员提供的账号和密码，登录系统之后，负责如下操作：

- 注册私有应用
- 定义应用权限
- 创建用户账号
- 管理用户权限
- 管理应用分组

#### 注册私有应用

私有应用是组织内部自行开发的应用，可供内部用户或者外部用户使用。组织管理员可通过以下步骤注册私有应用。

1. 使用组织管理员账号，登录应用框架，进入系统管理页面。
2. 在系统管理页面左侧任务栏，点击**应用管理**。
3. 点击**+应用**按钮，在**新应用**弹窗内，输入应用名、应用链接、应用描述，选择背景颜色和应用图标。
4. 点击**保存**，完成私有应用注册。

注册完成之后，所有已注册的私有应用和分配给组织的公有应用信息会显示在应用管理页面的表格中。在该表格中，可以更新私有应用的状态、编辑应用信息、定义应用权限，如下图所示。

![](image/private_app_zh.png)

#### 定义应用权限

组织管理员可为私有应用定义权限。具体步骤与系统管理员为公有应用定义权限的步骤相同。

#### 创建用户账号

为了实现内部和外部用户同时使用应用，需要创建不同类型的用户账号。组织管理员可通过以下步骤，为应用创建用户账号。

1. 在系统管理页面左侧任务栏，点击**用户管理**。
2. 点击**+用户**按钮，在**新用户**弹窗内，输入用户名、邮箱地址，选择用户类型（内部用户或外部用户）。
3. 点击**保存**，完成用户账号创建。
4. 在用户账号表格中，点击**重置**图标，为创建的用户账号生成初始密码。

用户账号创建完成之后，所有已创建的用户账号信息会显示在账号管理页面的表格中。在该表格中，可以编辑或删除账号，重置账号密码，或者管理用户的应用权限。如下图所示。

![](image/create_user_zh.png)

#### 管理用户权限

用户账号创建完成之后，即可授权和管理用户访问应用的权限，具体步骤如下。

1. 在系统管理页面左侧任务栏，点击**用户管理**，打开账号管理页面。

2. 在选定用户的信息栏中，点击授权图标，打开用户权限管理页面。

3. 依次点击需要授权的应用分组和应用名，展开应用权限列表。

4. 选择需要授权给用户的应用权限。

5. 点击**保存**，完成应用权限授权。如下图所示：

   ![](image/user_permission_zh.png)

如需为指定用户设置与组织管理员相似的平台管理权限，可在上图所示的账号管理页面，点击Settings Group。然后选择授权给用户的管理权限，包括用户管理、应用管理、和桌面配置权限。

为用户授权应用权限之后，用户登录平台，点击应用图标，即可访问经授权之后的应用和资源。

#### 管理应用分组

当组织拥有多个应用时，为方便管理应用，可将应用进行分组管理。具体步骤如下。

1. 在系统管理页面左侧任务栏，点击**桌面配置**，打开应用分组管理页面。
2. 点击+添加按钮，在**添加应用组**弹窗内，输入应用分组名称，勾选需要加入该分组的应用。
3. 点击**确定**，完成创建应用分组。注意：一个应用只能归属于一个分组。

应用被分组之后，当用户登录系统之后，即可按照分组查看应用。

### 用户

用户是应用的实际使用者。在使用组织管理员分配的账号登录系统之后，用户可在桌面查看经授权的应用。打开应用之后，访问经授权的资源。如下图所示。

![](image\user_view.png)
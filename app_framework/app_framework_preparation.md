# 准备工作
在使用应用框架管理应用的资源权限之前，需要预先对应用做相应的配置，包括定义应用权限、安装EnOS前端SDK配置权限、发布应用。

## 定义应用权限
应用权限是EnOS系统将应用资源定义为应用的访问控制权限，方便将不同的资源授予给不同的用户使用。因此，应用开发者需规划和定义应用的资源和权限。系统管理员或组织管理员需要依据定义的应用权限ID，在应用管理页面中配置应用的权限。

下表是应用权限定义的示例：

| 权限名称               | 权限ID            | 权限类型        |
|:-----------------------|:------------------|:----------------|
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

## 配置应用权限
完成应用权限定义之后，可使用EnOS前端SDK配置应用权限。

### 安装EnOS前端SDK

EnOS前端SDK发布于npm，下载地址：[http://npm.envisioncn.com/package/@enos/portalsdk](http://npm.envisioncn.com/package/@enos/portalsdk)

使用如下命令安装EnOS前端SDK：

```
npm install @enos/portalsdk --save
```

### API

应用框架本身提供API，供内部应用调用。应用可以通过前端SDK获取当前用户权限和页面操作等。

API统一挂在portalSdk下，调用API需要先引入SDK模块。

```
import portalSdk from '@enos/portalsdk';
```

API列表和功能的详细介绍，请参考[SDK Readme](http://npm.envisioncn.com/package/@enos/portalsdk)文档。

### 定义菜单权限

在 App 管理模块新增类型为`Menu`的权限，并为指定用户分配对应的 App 和权限，用户登录后，通过 API `getPermissions` 可获取到其拥有的全部权限，其中包含了配置的 `Menu` 权限。

SDK 提供了 React 版本的 `Menu` 组件，通过输入菜单数据和当前用户权限，提供统一的菜单展示。App 开发者可使用 `Menu` 组件展示菜单，也可根据权限数据自定义展示。

##### Menu 组件的参数

| Property     | Description                    | Type     |
|:-------------|:-------------------------------|:---------|
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

### 定义UI视图权限

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

### 定义数据权限

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

## 发布应用

完成应用权限配置之后，即可发布应用上线，获取应用URL。系统管理员或组织管理员在应用框架系统中注册应用时，需要输入应用的URL。

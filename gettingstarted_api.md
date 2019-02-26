# EnOS REST API 快速入门

本文介绍如何通过调用EnOS REST API来管理您在EnOS平台上的资源和数据。您也可以通过调用EnOS REST API，开发自有应用来管理资源和数据。调用EnOS REST API的主要步骤如下：

1. 入驻EnOS平台注册应用

2. 获取API文档

3. 调用EnOS API

4. 测试及发布应用

调用EnOS API需要以下3大元素：

- API名称：调用API接口的名称，包括API的路径和业务参数。
- 应用ID：在EnOS平台注册的应用ID，包括 `accessKey` 和 `secretKey` ， 作为应用或者开发者的身份。
- 签名：API调用的安全认证方法，为防止API调用过程中被恶意篡改或盗用。签名是根据accessKey、secretKey以及API请求参数生成的。服务端会对签名进行验证，签名不合法的请求将会被拒绝。

## 前提条件

调用EnOS API之前，确保您在EnOS系统中拥有授权访问的资源。资源可以是设备、数据、事件、用户帐户等。因此，在开始调用EnOS API之前，您通常已经完成了设备链接和数据上传，并且拥有一个用户帐户，该帐户具有通过EnOS IAM功能分配的访问策略。

## 入驻EnOS平台注册应用

要使用EnOS系统任何资源首先要成为EnOS系统开发者。调用EnOS API，需要通过以下步骤注册应用，获取 `accessKey` 和 `secretKey`。

1. 登录EnOS系统，在页面左侧导航栏点击 **应用管理**。

2. 打开应用管理页面后，点击 **注册应用**。

3. 在应用注册页面，输入应用名和应用描述，选择应用类型。

4. 完成应用注册之后，打开应用详情页面，查看应用的`accessKey` 和 `secretKey`。

## 获取API文档

EnOS系统提供详细的API描述文档，包括API的调用方法、API路径、参数描述、调用示例、和返回示例。

登录EnOS系统之后，在页面左侧导航栏点击 **EnOS API** > **API文档**，即可查看按服务分类的API列表。点击 **更多** 图标，即可打开每个API的详细文档，如下图所示。

.. image:: media/List_of_APIs.png
   :alt: 图1 - 查看EnOS API文档
   

.. image:: media/Example_of_API_details.png
   :alt: 图2 - EnOS API 文档示例
   

## 调用EnOS API

EnOS API是基于HTTP协议来调用的。您可以直接使用系统提供的官方SDK（支持Java语言，包含了请求的封装，签名加密，响应解释，性能优化等）来调用，也可以根据约定的协议来封装HTTP请求进行调用。详见 [调用EnOS REST API](call_enos_api)。

## 测试及发布应用

EnOS系统提供API测试工具和API访问日志查询工具帮助开发者测试EnOS API的调用代码。开发和测试完成后，即可发布应用。应用线上运行过程中，也可以通过访问日志查看应用的运行情况。

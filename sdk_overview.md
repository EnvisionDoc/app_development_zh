# EnOS API 和 SDK

## EnOS API

EnOS通过以下服务的API接口，开放EnOS的功能和服务：

- 接入服务：开放EnOS系统在设备连接和设备管理领域的业务能力，包括产品和设备的创建和管理。
- 模型服务：支持搜索和获取组织内模型的详细信息。
- 资产服务：提供组织内资产的创建、管理、更新等服务。
- 告警服务：提供资产告警的查询和管理服务。 
- 资产树服务：提供组织内资产树的创建、管理、更新、查询等服务。
- TSDB数据服务：提供获取已存储的资产数据服务。
- TSDB策略服务：提供获取TSDB存储策略配置信息的服务。
- IAM服务：提供用户帐户生命周期管理，用户身份验证以及EnOS资源访问权限控制等服务。
- 通用文件服务：提供文件管理服务，包括文件上传，下载，保存和删除。

对EnOS API的详细介绍，访问 **EnOS控制台 > EnOS API**。

.. image:: media/enos_api.png

## EnOS SDK

EnOS向用户和应用开发者提供一系列开发者工具套件，帮助开发者不用复杂编程即可高效地完成设备接入、数据采集、订阅设备数据、访问EnOS数据和服务。

对EnOS SDK的详细介绍、最新版本、及下载地址，访问 **EnOS控制台 > SDK中心**。

.. image:: media/sdk_center.png



<!--

## EnOS 设备 SDK

EnOS 设备 SDK 支持设备接入领域的业务需求，包括设备的身份注册、设备的上下线、网关设备的拓扑增删改查、设备的测点上报、设备服务的触发、设备的通用控制指令等。

### EnOS Device SDK for MQTT for Java

- [添加 Maven 项目依赖](https://mvnrepository.com/artifact/com.envisioniot/enos-mqtt/2.1.2)
- [从GitHub下载源代码](https://github.com/EnvisionIot/enos-mqtt-sdk-java)

### EnOS Device SDK for MQTT for Python (Preview Edition)

- 通过PIP安装：

  ```
  pip install enos-mqtt-sdk-python
  ```

- [从GitHub下载源代码](https://github.com/EnvisionIot/enos-mqtt-sdk-python)



## EnOS API Core SDK

EnOS API Core SDK 提供调用EnOS API的基础环境，支持同步请求和异步请求。

### Java Core SDK（Poseidon）

- [添加 Maven 项目依赖](https://mvnrepository.com/artifact/com.envisioniot/apim-poseidon/0.1.7)



[EnOS API 快速入门及 API 文档](/docs/api/zh_CN/latest/gettingstarted.html)



### Python Core SDK（Athena）

- 通过PIP安装：

  ```
  pip install aphrodite
  ```




[EnOS API 快速入门及 API 文档](/docs/api/zh_CN/latest/gettingstarted.html)



## EnOS IoT SDK for C

EnOS IoT SDK for C 支持基于X.509证书的身份验证API、设备与云之间通过MQTT协议的数据传输API、以及EnOS云服务API。

- [从GitHub下载源代码](https://github.com/EnvisionIot/enos-iot-sdk-c)



## EnOS 数据订阅 SDK

EnOS 数据订阅 SDK 支持消费通过EnOS控制台订阅的资产实时数据和告警数据。

- [添加 Maven 项目依赖](https://mvnrepository.com/artifact/com.envisioniot/enos-subscribe/2.2.0)



## 参考

- [EnOS SDK 快速入门](gettingstarted_sdk)



## EnOS Appframework Mars

EnOS Appframework Mars SDK 为开发者提供应用管理（包括权限校验体系）和应用开发的框架，同时提供了一套简易开发API接口。

- [添加 Maven 项目依赖](https://mvnrepository.com/artifact/com.envisioniot/enos-appframework-mars/0.1.0)

-->
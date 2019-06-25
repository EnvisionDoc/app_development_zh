# EnOS SDK

EnOS系统向用户和应用开发者提供一系列开发者工具套件，帮助开发者高效地完成设备接入、设备注册、数据收集、订阅设备数据、调用EnOS API接口开发应用等工作。



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

<!--

[EnOS API 快速入门及 API 文档](/docs/api/zh_CN/latest/gettingstarted.html)

-->

### Python Core SDK（Athena）

- 通过PIP安装：

  ```
  pip install aphrodite
  ```


<!--

[EnOS API 快速入门及 API 文档](/docs/api/zh_CN/latest/gettingstarted.html)

-->

## EnOS IoT SDK for C

EnOS IoT SDK for C 支持基于X.509证书的身份验证API、设备与云之间通过MQTT协议的数据传输API、以及EnOS云服务API。

- [从GitHub下载源代码](https://github.com/EnvisionIot/enos-iot-sdk-c)



## EnOS 数据订阅 SDK

EnOS 数据订阅 SDK 支持消费通过EnOS控制台订阅的资产实时数据和告警数据。

- [添加 Maven 项目依赖](https://mvnrepository.com/artifact/com.envisioniot/enos-subscribe/2.2.0)



## 参考

- [EnOS SDK 快速入门](gettingstarted_sdk)



<!-- ## EnOS Appframework Mars

EnOS Appframework Mars SDK 为开发者提供应用管理（包括权限校验体系）和应用开发的框架，同时提供了一套简易开发API接口。

- [添加 Maven 项目依赖](https://mvnrepository.com/artifact/com.envisioniot/enos-appframework-mars/0.1.0) -->

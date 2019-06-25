# EnOS SDK 快速入门

欢迎使用EnOS开发者工具套件（SDK）。通过使用EnOS系统SDK，不用复杂编程即可完成资产接入、资产数据存储、资产数据读取等服务。本文以EnOS API Core SDK（Poseidon）为例，介绍如何快速获取EnOS SDK、准备开发环境、并开始应用开发。

## 前提条件

在使用EnOS SDK之前，确保您在EnOS系统中拥有授权访问的资源。资源可以是设备、数据、事件、用户帐户等。例如，在使用EnOS API Core SDK调用某个产品的API前，确保您已经在EnOS 控制台创建了该产品的相关资源。

您还需要一对 `AccessKey`  和  `SecretKey`，即SA账号。 目前SA账号的产生只能由创建应用产生。请在EnOS控制台中的应用注册页面上创建应用并查看对应的SA信息。在调用API接口写入数据时，需确保使用的SA账号有相应的权限，请参考[管理服务账号](/docs/iam/zh_CN/latest/howto/service_account/managing_service_account.html)。

## 安装 EnOS API Core SDK

安装EnOS API Core SDK的系统环境要求如下：

- Java：安装Java JDK SE 8，安装 Maven 3（推荐版本）。
- Python：安装 Python 2.7.10 以上版本，并且需要支持 `pip` 。
- C：安装CMake (下载地址：<https://cmake.org/>)。

可以通过如下方法安装EnOS SDK：

- Java：通过在 `pom.xml` 文件中添加Maven项目依赖
- Python：通过PIP安装
- 从GitHub中央仓库下载SDK源代码

### 使用Maven安装

如果使用Maven管理Java项目，登录中央仓库 http://search.maven.org，然后搜索com.envisioniot.enos，找到需要使用的SDK版本。通过在 `pom.xml` 文件中添加Maven项目依赖安装EnOS SDK。您可以在Maven库中查找各产品的Maven依赖坐标。

以EnOS API Core SDK为例，您只需在 `pom.xml` 中声明这个开发工具包，如下所示：

```java
<dependency>
  <groupId>com.envisioniot</groupId>
  <artifactId>apim-poseidon</artifactId>
  <version>0.1.7</version>
</dependency>
```

### 通过PIP安装

使用以下命令安装SDK（以EnOS API Core SDK为例）：

```
pip install aphrodite
```

### 下载SDK源代码安装

从GitHub仓库下载SDK源代码安装。以EnOS Device SDK for MQTT为例，通过以下命令下载：

```
git clone https://github.com/EnvisionIot/enos-mqtt-sdk-java.git
```

## 示例
以下代码示例展示了使用EnOS API Core SDK调用`GetAsset` API接口（根据资产ID获取资产数据）：

```
import com.envision.apim.poseidon.config.PConfig;
import com.envision.apim.poseidon.core.Poseidon;

public class demo {
    public static void main(String[] args) {

        String appKey = "accessKey";
        String appSecret = "secretKey";

        String response = Poseidon.config(PConfig.init().appKey(appKey).appSecret(appSecret))
                .url("https://apigw-address/asset-service/v2.0/assets?orgId=orgId&assetId=assetId")
                .method("GET")
                .sync();
        System.out.println(response);
        }
    }
```
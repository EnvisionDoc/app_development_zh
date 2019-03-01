# EnOS SDK 快速入门

欢迎使用EnOS开发者工具套件（SDK）。通过使用EnOS系统SDK，不用复杂编程即可完成资产接入、资产数据存储、资产数据读取等服务。本文以EnOS Service SDK为例，介绍如何快速获取EnOS SDK、准备开发环境、并开始应用开发。

## 前提条件

在使用EnOS SDK之前，确保您在EnOS系统中拥有授权访问的资源。资源可以是设备、数据、事件、用户帐户等。例如，在使用EnOS SDK调用某个产品的API前，确保您已经在EnOS 控制台创建了该产品的相关资源。

您还需要一对 `accessKey`  和  `secretKey`，即SA账号。 目前SA账号的产生只能由创建应用产生。请在EnOS控制台中的应用注册页面上创建应用并查看对应的SA信息，或联系您的系统管理员。

## 安装 EnOS SDK

安装EnOS SDK的系统环境要求如下：

- Java：支持1.7以上版本的JDK，安装 Maven 3（推荐版本）。
- Python：安装 Python 2.7.10 以上版本，并且需要支持 `pip` 。
- C：安装CMake (下载地址：<https://cmake.org/>)。

可以通过如下方法安装EnOS SDK：

- Java：通过在 `pom.xml` 文件中添加Maven项目依赖安装EnOS SDK；Python：通过PIP安装。
- 从GitHub中央仓库下载SDK源代码安装。

### 使用Maven安装

如果使用Maven管理Java项目，登录中央仓库 http://search.maven.org，然后搜索**com.envisioniot.enos**，找到需要使用的SDK版本。通过在 `pom.xml` 文件中添加Maven项目依赖安装EnOS SDK。您可以在Maven库中查找各产品的Maven依赖坐标。

以EnOS Service SDK为例，您只需在 `pom.xml` 中声明这个开发工具包，如下所示：

```java
	<dependency>
    <groupId>com.envisioniot</groupId>
    <artifactId>enos-api-sdk</artifactId>
    <version>2.1.0</version>
    </dependency>
```

### 通过PIP安装

使用以下命令安装SDK（以EnOS Service SDK为例）：

```
pip install enos-api-sdk-python
```

### 下载SDK源代码安装

从GitHub仓库下载SDK源代码安装。以EnOS Service SDK为例，通过以下命令下载：

```
git clone https://github.com/EnvisionIot/enos-api-sdk-java.git
```

## 示例：使用EnOS Service SDK for Java
以下代码示例展示了使用EnOS Service SDK for Java的3个主要步骤：

1. 创建并初始化 `EnOSDefaultClient` 实例。

   ```
   String serverUrl = "xxx";
   String accessKey = "xxx";
   String secretKey = "xxx";
   int connectTimeout = 5000; //Set connect timeout as 5000 milliseconds
   int readTimeout = 5000;    //Set read timeout as 5000 milliseconds
   EnOSDefaultClient client = new EnOSDefaultClient(serverUrl, accessKey,secretKey,connectTimeout,readTimeout);
   ```

2. 创建API请求并设置参数。在引入多个产品SDK时，有可能存在Request类同名的情况，请注意按照package区分。以 `createProduct` 接口为例：

   ```
   Product product = new Product();
   product.setProductName("xxx");
   product.setProductDesc("xxx");
   product.setModelId("xxxxx");
   product.setDataType(1);
   product.setNodeType(1);
   ProductCreateRequest request = new ProductCreateRequest(orgId, product);
   ```

3. 发起请求并处理应答或异常。

   ```
   EnOSResponse<Product> response;
   try {
       response = client.execute(request);
       System.out.println(response.getData());
   } catch (ServerException e) {
       e.printStackTrace();
   } catch (ClientException e) {
       e.printStackTrace();
   }
   ```

4. 正常情况下，应答中的所有字段，都会被反序列化到response中，可以直接调用 `response.getXXX()` 来获得应答中的字段。

   ```
   String status = response.getStatus()
   ```

### 示例代码

以下代码以调用  `createProduct`  接口（创建产品）为例。

```java
import com.envisioniot.enos.enosapi.api.request.connectservice.CreateProductRequest;
import com.envisioniot.enos.enosapi.api.resource.connectservice.Product;
import com.envisioniot.enos.enosapi.common.exception.EnOSApiException;
import com.envisioniot.enos.enosapi.common.response.EnOSResponse;
import com.envisioniot.enos.enosapi.sdk.client.EnOSDefaultClient;

public class Main {
    public static void main(String[] args) {
    String serverUrl = "xxx";
    String accessKey = "xxx";
    String secretKey = "xxx";
    int connectTimeout = 5000;
    int readTimeout = 5000;
    product.setProductName("XXX");
    product.setProductDesc("XXX");
    product.setModelId("XXXXX");
    product.setDataType(1);
    product.setNodeType(1);
    EnOSDefaultClient client = new EnOSDefaultClient(serverUrl, accessKey,secretKey,connectTimeout,readTimeout);
    Product product = new Product();
    CreateProductRequest request = new CreateProductRequest(orgId, product);
    try {
        EnOSResponse response = client.defaultClient().execute(request);
    } catch (EnOSApiException e) {
        e.printStackTrace();
    }
 }
    }
```

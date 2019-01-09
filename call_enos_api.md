# 调用 EnOS REST API

封装HTTP请求进行API调用实际是通过手动方式或API调用工具构造REST API的URL，并通过URL访问EnOS API。本文详细介绍如何根据约定的协议来封装HTTP请求调用EnOS API。主要流程为：填充参数 > 生成签名 > 拼装HTTP请求 > 发起HTTP请求 > 得到HTTP响应 > 解释JSON返回结果。

## 封装HTTP请求

构造API URL需要的信息包括：

1. EnOS API的网关地址（服务URL）：`` https://enos-api-cn1.envisioniot.com/ ``

2. 调用方法：EnOS API的请求方法，例如GET，POST，PUT，DELETE

3. API路径：每个EnOS API的路径，详见API参考文档

4. 请求参数：包括拼接在URL中的query请求参数以及JSON格式的body请求参数

以getProduct（查询产品信息）接口为例，封装的HTTP请求如下：

```
GET https://enos-api-cn1.envisioniot.com/connectService/products/{productKey}?accessKey={}&requestTimestamp={}&sign={}&orgId={}
```

### 公共参数

调用EnOS API需要传入的公共请求参数包括：

.. list-table::
   :widths: auto

   * - 参数名称
     - 参数类型
     - 是否必须
     - 参数描述
   * - Content-Type
     - String
     - 是
     - 数据提交方式，一般情况下值可为“application/json;charset=UTF-8”；若执行文件上传或其他表单提交，值设为“multipart/form-data;charset=UTF-8”
   * - accessKey
     - String
     - 是
     - 服务账号的accessKey，通过创建应用生成
   * - secretKey
     - String
     - 是
     - 服务账号的secretKey，通过创建应用生成
   * - requestTimestamp
     - String
     - 是
     - Unix时间戳，是指从格林威治时间1970年01月01日00时00分00秒(北京时间1970年01月01日08时00分00秒)起至现在的总秒数。
   * - sign
     - String
     - 是
     - API输入参数签名结果，签名算法参照下面的介绍。

### 业务参数

API调用除了必须包含公共参数外，如果API本身有业务级的参数也必须传入，每个API的业务级参数请考API文档说明。

### 调用示例

以调用getProduct接口为例，具体步骤如下：

**1. 设置参数值**

公共参数：

```
requestTimestamp = 1536560363020
```

业务参数：

```
orgId = "123"
productKey = "12345"
```

**2. 按ASCII顺序排序**

```
orgId = "123"
productKey = "12345"
requestTimestamp = "1536560363020"
```

**3. 拼接参数名与参数值**

```java
orgId123productKey12345requestTimestamp1536560363020
```

**4. 生成签名**

假设accessKey和secretKey分别为"accessKeyExample"和"secretKeyExample"，则签名结果为：

```
hex(md5(accessKeyExample+orgId123productKey12345requestTimestamp1536560363020+secretKeyExample)) = "4A6936C442CC34C5C42B9E06D97F2FA268B7E52F"
```

**5.组装HTTP请求**

将所有参数名和参数值采用utf-8进行URL编码（参数顺序可随意，但必须要包括签名参数），然后通过GET或POST（含byte[]类型参数）发起请求，如：

```
http://http://xxx.envisioniot.com/enosapi/connectService/products/12345?orgId = 123&productKey = 12345&requestTimestamp = 1536560363020&accessKey=accessKeyExample&secretKey=secretKeyExample&sign=4A6936C442CC34C5C42B9E06D97F2FA268B7E52F
```

### 注意事项

- 所有的请求和响应数据编码皆为utf-8格式，URL里的所有参数名和参数值请做URL编码。如果请求的Content-Type是application/x-www-form-urlencoded，则HTTP Body体里的所有参数值也做URL编码；如果是multipart/form-data格式，每个表单字段的参数值无需编码,但每个表单字段的charset部分需要指定为utf-8；如果是applincation/json，则整个HTTP Body作为字符串参与签名，但不需要进行URL编码
- 生成签名（sign）仅对未使用官方SDK进行API调用时需要操作，如使用了官方SDK，该步骤SDK会自动完成。

## 解释JSON返回结果

API调用成功之后，调用结果以JSON格式返回。根据每个API的功能，解析系统返回的结果。

### 公共返回参数

.. list-table::
   :widths: auto

   * - 字段
     - 数据类型
     - 描述
   * - requestId
     - String
     - 系统为当前请求生成的唯一标识
   * - status
     - Int
     - 状态码，详见状态码表格内解释
   * - msg
     - String
     - 状态码说明
   * - submsg
     - String
     - 状态详细说明

### 状态码列表

.. list-table::
   :widths: auto

   * - 状态码
     - 描述
   * - 0
     - 调用成功
   * - 400
     - 参数错误
   * - 401
     - 未认证的请求，比如accessKey和secretKey对不上
   * - 403
     - 无权限
   * - 404
     - 资源找不到
   * - 405
     - 不支持的方法
   * - 409
     - 资源已存在
   * - 414
     - 请求体太大
   * - 415
     - 请求参数超出范围，比如数组参数或字符串参数
   * - 429
     - 超出配额，或者超过限流
   * - 497
     - 时间戳或签名验证失败
   * - 498
     - 资源或API无访问权限
   * - 499
     - 客户端错误
   * - 500
     - 服务器内部错误
   * - 501
     - API未实现
   * - 503
     - API服务不可用
   * - 504
     - 调用超时
   * - 6xx
     - 第三方服务定义错误码

<!--end-->

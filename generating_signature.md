# API签名算法

为了防止API调用过程中被恶意篡改或盗用，开发者需要根据accessKey、secretKey以及请求参数生成签名，服务端会对签名进行验证，签名不合法的请求将会被拒绝。目前EnOS API采用的签名方法为SHA-1。

## 算法说明

使用SHA-1签名算法生成签名的步骤如下：

1. 对URL参数（包括requestTimestamp）和application/x-www-form-urlencoded类型的表单参数进行字典升序排列。

2. 将以上排序后的参数表进行字符串连接，如：

   ```
   key1value1key2value2key3value3...keyNvalueN
   ```

3. 如果请求带有JSON类型的body，把整个body当做字符串拼接到上一步的字符串后面。

4. 将accessKey作为前缀，将secretKey作为后缀，对该字符串采用utf-8编码，使用签名算法对编码后的字节流进行摘要，并转换成16进制编码，如：

   ```
   <app_key><key1value1key2value2key3value3...keyNvalueN><app_secret>
   ```

## **JAVA生成签名示例**

```java
// 定义appKey和appSecret
        String accessKey = "eos_test_appkey";
        String secretKey = "eos_test_secret";
        String apiUrl = "http://xxx.envisioniot.com/enosapi";

// 参数表
        Map<String, String> paramMap = new HashMap();
        paramMap.put("mdmids", "67c17f7cebd44323b764e853394af5e8%2C70106f0c458e4b3994e741670d6be659");
        paramMap.put("points", "INV.GenActivePW%2CINV.APProduction");
        paramMap.put("time_group", "D");

// 对参数名进行字典排序
        String[] keyArray = paramMap.keySet().toArray(new String[0]);
        Arrays.sort(keyArray);

// 拼接有序的参数名-值串
        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append(accessKey);
        for (String key : keyArray)
        {
            stringBuilder.append(key).append(paramMap.get(key));
        }
        stringBuilder.append(secretKey);
        String codes = stringBuilder.toString();

// 上述参数/AppKey/AppSecret拼接后字符串连接示例：
// eos_test_appkeymdmids67c17f7cebd44323b764e853394af5e8%2C70106f0c458e4b3994e741670d6be659pointsINV.GenActivePW%2CINV.APProductiontime_groupDeos_test_secret

// 此处采用SHA-1签名方法并转换为大写
        String sign = org.apache.commons.codec.digest.DigestUtils.shaHex(codes).toUpperCase();

//签名结果
//2D87E22205279651B59AD96AAEC102464374734F
```

## 签名校验报错处理方法

若访问API过程中出现 `Signature verification failed` 错误提示，常见原因如下：

1.  accessKey与secretKey不匹配
2.  签名方法有误
3.  生成签名时，中文的参数值没有先转换为UTF8编码

## 参考

- [Getting started with EnOS REST APIs](gettingstarted_api)

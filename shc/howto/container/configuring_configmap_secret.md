# 配置Config Map和Secret

本文章介绍应用开发人员如何新建Config Map和Secret，将配置信息注入容器。

Config Map可用于存储细粒度信息，如单个属性；或粗粒度信息如整个配置文件或JSON对象。Config Map可存储键/值对配置数据，这些数据可以在pod里使用。通过Config Map，可以更方便的处理不包含敏感信息的字符串。

Secret解决了密码、token、密钥等敏感数据的配置问题，而不需要把这些敏感数据暴露到镜像或者pod spec中。Secret可以以Volume或者环境变量的方式使用。通过Secret，可以更方便的处理包含敏感信息的字符串。

## 新建Config Map

通过以下步骤为应用新建Config Map：

1. 在左侧导航栏中，选择 **容器 > Config Maps**。

2. 点击 **新建Config Map**，并完成Config Map的详细配置。

3. 提供Config Map的基本信息：

   - **应用**：选择需要使用Config Map的应用
   - **环境**：选择Config Map使用环境，目前支持dev，alpha，beta，ppe，和prod环境
   - **集群**：选择部署应用的集群，目前集群已由系统预先配置

4. 输入需要配置的Config Map信息（KEY/VALUE键值对）。

  .. image:: ../../media/config_map.png

5. 输入对Config Map的描述信息。

6. 点击 **新建Config Map** 按钮，完成配置。

## 新建Secret

通过以下步骤为应用新建Secret：

1. 在左侧导航栏中，选择 **容器 > Secrets**。

2. 点击 **新建Secret**，并完成Secret的详细配置。

3. 提供Secret的基本信息：

   - **应用**：选择需要使用Secret的应用
   - **环境**：选择Secret使用环境，目前支持dev，alpha，beta，ppe，和prod环境
   - **集群**：选择部署应用的集群，目前集群已由系统预先配置

4. 选择Secret加密类型：

   - **Opaque**：Base64编码格式的Secret，用来存储密码、密钥等。
   
     .. note:: Opaque类型的Value需要填写Base64加密后的内容。可以使用在线加密解密工具：<http://tool.oschina.net/encrypt?type=3>

   - **kubernetes.io/rbd**：

     .. image:: ../../media/secret.png

5. 输入对Secret的描述信息。

6. 点击 **新建Secret** 按钮，完成配置。

## 后续操作

Config Map和Secret创建完成后，可对Config Map和Secret进行克隆、编辑、和删除操作。具体步骤和[配置Deployment](configuring_deployment)相似。

<!--end-->
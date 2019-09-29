# 配置Service和Route

本文章介绍应用开发人员如何新建Service配置，以支撑应用对集群外部暴露Web服务，并且同时配置Route。

## 前提条件

在新建Service之前，需要完成Deployment配置。详细步骤，参见[配置Deployment](configuring_deployment)。

## 新建Service

通过以下步骤为应用新建Service：

1. 在左侧导航栏中，选择 **容器 > Services**。

2. 点击 **新建Service**，并完成Service的详细配置。

3. 提供Service的基本信息：

   - **应用**：选择需要发布Service的应用
   - **环境**：选择Service环境，目前支持dev，alpha，beta，ppe，和prod环境
   - **集群**：选择部署应用的集群，目前集群已由系统预先配置
   - **类型**：选择Service的类型，目前仅支持ClusterIP

4. 完成Service的端口配置：输入服务的端口和目标端口，并选择协议类型。

  - **输入端口**：提供给集群内部客户访问Service的入口
  - **目标端口**：是pod上的端口，从服务端口接收的数据最终经过kube-proxy流入到后端pod的目标端口，进入容器
  - **协议**：端口支持的协议，可选TCP或UDP

5. **选择器**：选择应用的部署类型，及对应的部署名称。

  .. image:: ../../media/service_config.png

6. 输入对Service的描述信息。

7. 点击 **新建Service** 按钮，完成配置。

## 新建Route

通过以下步骤为应用新建Route：

1. 在左侧导航栏中，选择 **容器 > Routes**。

2. 点击 **新建Route**，并完成Route的详细配置。

3. 提供Route的基本信息：

   - **应用**：选择需要使用Route的应用
   - **环境**：选择Route环境，目前支持dev，alpha，beta，ppe，和prod环境
   - **集群**：选择部署应用的集群，目前集群已由系统预先配置

4. 配置Route规则：

   - **主机名**：根据集群默认设置，无法修改

   - **路径**：输入访问对外服务的路径

   - **服务**：选择已创建的服务

   - **端口**：输入路由，仅可选8080

     .. image:: ../../media/route_config.png

5. 输入对Route的描述信息。

6. 点击 **新建Route** 按钮，完成配置。

## 后续操作

Service和Route创建完成后，可对Service和Route进行克隆、编辑、和删除操作。具体步骤和[配置Deployment](configuring_deployment)相似。

<!--end-->
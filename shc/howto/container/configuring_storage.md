# 配置Storage

本文章介绍应用开发人员如何新建Storage配置，以支撑应用的数据存储需求。

## 新建Storage

通过以下步骤为应用新建Storage：

1. 在左侧导航栏中，选择 **容器 > Storage**。

2. 点击 **新建Storage**，并完成Storage的详细配置。

3. 提供Storage的基本信息：

  .. image:: ../../media/storage_config.png

   - **应用**：选择需要使用Storage的应用
   - **环境**：选择Storage使用环境，目前支持dev，alpha，beta，ppe，和prod环境
   - **集群**：选择部署应用的集群，目前集群已由系统预先配置
   - **储存类型**：选择储存模式，支持块（Block）和文件系统（Filesystem）
   - **访问模式**：选择访问模式，支持ReadWriteOnce（以读写模式被加载到一个节点上）和ReadWriteMany（以读写模式被多个节点同时加载）
   - **容量**：输入应用需要的Storage容量（GB）
   - **说明**：输入对Storage的描述信息

4. 点击 **新建Storage** 按钮，完成配置。

## 后续操作

Storage配置创建完成后，可对Storage配置进行克隆、编辑、和删除操作。具体步骤和[配置Deployment](configuring_deployment)相似。

<!--end-->


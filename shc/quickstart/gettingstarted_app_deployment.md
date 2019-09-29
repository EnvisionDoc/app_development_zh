# 快速构建和部署应用

本教程将指导你如何通过EnOS SHC快速构建和部署应用、将应用发布至指定集群中，并且测试使用应用。

## 场景描述<scenario>

通过EnOS SHC将名为*uic*的应用发布至*beta*集群中，并使用该服务查询个人信息。


## 任务描述<description>

在应用开发项目中，完成应用*uic*的容器配置，流水线创建和发布上线。创建部署配置、服务配置和路由配置，然后为其创建流水线，添加构建、代码扫描和部署三个任务，点击运行，启动流水线，完成以上任务，并使用该服务查询个人信息。


基于上述需求，快速发布应用的流程如下图所示：

.. image:: media/app_deployment_process.png

## 前提条件<prerequisites>

1. EnOS SHC中已创建应用开发项目，并且名为*uic*的应用已经创建完成，应用代码已保存到Git仓库。

2. 用户为应用开发项目的成员，且拥有应用*uic*的开发权限。详细步骤，参考[管理项目和应用基本信息](/docs/apaas/zh_CN/latest/howto/admin/index.html)。

## 步骤1：创建部署配置<deployment>

该步骤为应用*uic*创建部署配置，完成部署应用所需要的资源详细信息。

1. 登录EnOS控制台，在左侧导航栏中选择 **服务托管中心**，进入应用开发项目。

2. 在左侧导航栏，选择 **容器 > Deployments**。

3. 点击 **新建Deployment**，选择 **Config** 方式，提供如下部署配置：

   - 应用名称：uic
   - 环境：beta
   - 集群：beta-k8s-cn4
   - 副本数：1
   - CPU至少：0.1；CPU最大：0.8
   - 内存至少： 0.1；内存最大：0.5
   - 就绪探针：开启
   - 超时时间：120
   - 探测周期：2
   - 失败重试次数：3             
   - 探测延迟：20
   - 探针方式：tcpSocket；TCP端口：8080
   - 容器最小就绪时间：30s
   - 说明：应用uic的beta环境部署配置

4. 点击**新建Deployment**按钮，保存部署配置。

   .. image:: media/deploymen1_2.png


## 步骤2：创建配置字典并更新部署配置<config>

该步骤为应用*uic*创建配置字典，并更新已有的部署配置信息：

1. 在左侧导航栏，选择 **容器 > Config Maps**。

2. 点击 **新建Config Map**，提供如下配置字典信息：

   - 应用名称：uic
   - 环境：beta
   - 集群：beta-k8s-cn4
   - 数据：Key: application.properties；Value: 为application.properties文件的内容
   - 说明：应用uic的beta环境的配置字典

3. 点击 **新建Config Map** 保存配置字典信息。

   .. image:: media/config_map.png

4. 在导航栏点击Deployments，选择步骤1创建的部署配置，点击**编辑**按钮。

5. 编辑部署配置中的Config Map，如下图所示：

   .. image:: media/update_config_map.png




## 步骤3：创建服务配置和路由配置<service>

该步骤为应用*uic*创建服务配置和路由配置，以支撑*uic*应用对集群外部暴露Web服务。

服务配置步骤如下：

1. 在左侧导航栏，选择 **容器 > Services**。

2. 点击 **新建Service**，提供如下服务配置信息：

   - 应用：uic
   - 环境：beta
   - 集群：beta-k8s-cn4
   - 类型：ClusterIp
   - 端口配置：8080，8080，TCP
   - 说明：应用uic的beta环境服务配置

3. 点击 **新建Service** 按钮，完成服务配置。

   .. image:: media/service.png

路由配置详细步骤如下：

1. 在左侧导航栏，选择 **容器 > Routes**。

2. 点击 **新建Route**，提供如下路由配置信息：

   - 应用：uic
   - 环境：beta
   - 集群：beta-k8s-cn4
   - 主机名：uic
   - 路径：/api/user
   - 服务：uic-service-dev  
   - 端口：8080
   - 说明：应用uic的beta环境路由配置

3. 点击 **新建Route** 按钮，完成路由配置。

   .. image:: media/route.png

## 步骤4：创建流水线<pipeline>

该步骤为应用uic创建流水线，一条流水线由基本信息、视图和任务组成，创建一条流水线需经以下几个步骤：

### 配置基础信息

1. 在左侧导航栏，选择 **研发 > 流水线**。

2. 点击 **新建流水线**，提供如下基本信息：

   - 应用名称：uic
   - 流水线名称：uic-pipeline-dev
   - 环境：beta
   - 语言/版本：java_1.8.0
   - 工具：maven_3.3.9
   - 触发设置：手动触发

   .. image:: media/pipeline_basic.png

### 配置阶段

1. 选择 **构建**，并提供如下信息：

   - 任务名称：构建

   - Docker文件路径：Dockerfile

   - Docker镜像仓库：harbor.eniot.io

     .. image:: media/task_build.png

3. 选择 **代码扫描**，并提供如下信息：

   - 任务名称：代码扫描

   - 待扫描代码：src/main/java

     .. image:: media/task_code_scan.png

   .. note:: 对于构建和代码扫描规则的详细介绍，参考[新建流水线](../howto/pipeline/creating_pipeline)。


4. 选择 **部署**，并提供如下信息：

   - 环境：beta

   - 任务名称：部署

   - 集群：beta-k8s-cn4

   - 部署类型：Deployment

   - 部署名称：uic-deployment-dev

     .. image:: media/task_deployment.png

6. 点击 **新建流水线** 按钮，保存流水线配置。

## 步骤5：运行流水线并查看结果<result>

该步骤运行配置的流水线，并查看流水线运行结果。

1. 在创建的流水线列表中，点击创建的流水线*uic-pipeline-dev*，打开流水线详情页面。

2. 点击 **运行** 按钮，选择仓库分支，点击 **运行**。

   .. image:: media/run_pipeline.png

3. 查看流水线运行结果。

   - 点击 **构建**，查看构建任务运行结果，包括构建日志以及镜像地址：

     .. image:: media/build_result.png

   - 点击 **代码扫描**，查看代码扫描任务运行结果，包括扫描日志和扫描结果地址：

     .. image:: media/scan_result.png

   - 点击 **部署**，查看部署任务运行结果：

     .. image:: media/deploy_result.png



## 步骤6：测试运行发布的应用<test>

应用部署成功后，测试运行应用，确保应用按照配置的服务信息可正常运行。

<!--end-->

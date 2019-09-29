# 新建流水线

本文章介绍应用开发人员如何为应用新建流水线、配置流水线阶段和任务。

## 前提条件

在新建流水线之前，需要完成应用创建和基本信息配置。详细步骤，参见[新建应用](../admin/managing_app#newapp)。

## 配置流水线基础信息

通过以下步骤为应用新建流水线：

1. 在项目列表中，点击项目名称，进入项目空间。

2. 在左侧导航栏中，选择 **研发 > 流水线**。

3. 点击 **新建流水线**，并在 **基础信息** 一栏中，提供流水线的基础配置信息：

   - **应用名称**：从已创建应用列表中，选择为哪一个应用创建流水线

   - **流水线名称**：输入创建流水线的名称

   - **是否部署**：选择流水线是否需要部署功能，若需部署则相应地选择部署环境。

   - **语言/版本**：选择开发应用使用的语言以及对应版本

   - **工具**：选择语言需要依赖的工具，如Java需要依赖Maven

   - **仓库地址**：根据选择的应用，自动填入应用所在的仓库地址

   - **触发设置**：选择触发流水线运行的方式：
     - 自动触发：当指定的Gitlab仓库分支发生变化时，运行流水线
     - 手动触发：手动选择Gitlab仓库分支，并运行流水线
     - 定时触发：在设定时间定时运行流水线

   - **仓库分支**：当触发设置为自动触发或定时触发时，选择运行流水线的Gitlab仓库分支

   - **触发时间**：当触发设置为定时触发时，选择运行流水线的具体时间。

     .. image:: ../../media/create_pipeline.png

4. 完成基础信息配置后，在 **Stage** 一栏中，点击 **添加Stage**，配置流水线的阶段和任务。


## 配置阶段和任务

通过以下步骤配置建流水线的阶段和任务：

1. **阶段名称**：输入Stage的名称。

2. 点击 **添加任务** 按钮，选择任务类型，并输入相应的参数。

   - **构建**
     - 任务名称：输入构建任务的名称
     - Docker文件路径：输入Dockerfile存放路径，如docker/Dockerfile，默认为项目根路径
     - Docker镜像仓库：选择镜像仓库

   .. note:: 构建任务会判断是否存在*build.sh*，若存在，则自动执行*build.sh*；若不存在，则判断是否存在*pom.xml*，若存在，则执行*mvn clean package -U -DskipTests*命令。使用自定义*build.sh*进行构建时需要将构建结果如war/tar/jar/zip包等的存放位置设置为项目根目录下的*target*目录。

   - **部署**

     - 任务名称：输入部署任务的名称
     - 集群：选择部署应用的集群
     - 部署类型：选择部署类型，可选Deployment或StatefulSet
     - 部署名称：选择应用的部署配置名称（参见[配置Deployment](../container/configuring_deployment)）

   - **代码扫描**
     - 任务名称：输入代码扫描任务的名称
     - 待扫描代码：输入需要扫描的文件路径，如*src/main/java*，*src/main/java/utils/Test.java*
     - 排除文件：输入无需扫描的文件路径，如src/main/java/*，src/main/java/**/，src/main/java/utils/Test.java
     - 单元测试：选择是否进行单元测试，如需进行单元测试，则输入测试文件的路径，如*src/test*

   .. note:: 代码扫描任务会判断是否存在*build.sh*，若存在，则自动执行*build.sh*；若不存在，则判断是否存在*pom.xml*，若存在，则执行*mvn clean compile -DskipTests*命令。编程语言为Java时，会判断是否存在*sonar-project.properties*文件，若存在，则使用*sonar-scanner*完成代码扫描；若不存在，则使用*mvn sonar:sonar*进行代码扫描。其他编程语言如Node.js，则默认使用*sonar-scanner*进行代码扫描。

   - **发布依赖包**

     - 任务名称：输入任务的名称
     - 构建路径：输入pom文件所在的路径，如*share*，默认为项目根路径
     - 参数：Java默认命令为*mvn deploy*，可添加参数，如*-DskipTests*；npm默认命令为*npm*
       *publish*，可添加参数，如*--access=public*

   - **Jenkins任务**
     - 任务名称：输入Jenkins任务的名称
     - Jenkins URL：输入Jenkins服务地址，如：<http://jenkins-ci.envisioncn.com:8080/jenkins>
     - User Name：输入Jenkins用户名
     - API Token：输入Jenkins用户名所生成的API Token
     - 任务名：输入Jenkins job名称
     - Jenkins参数：输入需要的Jenkins参数

   - **自定义任务**
     - 任务名称：输入自定义的任务的名称
     - Shell脚本路径：输入需要执行的脚本的路径

3. 点击并拖动任务，可以对任务进行排序。

   .. image:: ../../media/add_stage.png

4. 阶段内的任务配置完成后，点击 **添加Stage**，重复以上步骤，添加流水线的第二个阶段。

5. 阶段配置完成之后，点击 **新建流水线** 按钮，保存流水线配置。

## 后续操作

流水线创建完成后，可运行流水线，并查看流水线运行状态和结果。

<!--end-->

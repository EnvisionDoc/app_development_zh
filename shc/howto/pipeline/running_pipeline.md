# 运行流水线并查看结果

流水线创建完成后，流水线将按照配置的触发方式运行。如业务需要，可手动触发运行流水线，并查看流水线运行状态和结果。

## 运行流水线

通过以下步骤手动运行流水线：

1. 在左侧导航栏中，选择 **研发 > 流水线**。

2. 在已创建的流水线列表中，点击流水线名称，打开流水线详情页面。

3. 点击 **运行** 按钮，选择代码仓库分支，运行流水线。

   .. image:: ../../media/run_pipeline.png


## 查看运行结果

流水线开始运行后，流水线运行的状态和结果将显示在 **执行结果** 一栏中。

1. 点击流水线中的任务名称，查看每个任务的运行结果：

   .. image:: ../../media/pipeline_success.png

2. 如果流水线任务运行失败，点击 **查看日志** 按钮或下载日志，查找出错原因。编辑流水线和任务后，重新运行流水线。

   .. image:: ../../media/pipeline_failure.png

当构建任务运行成功后，自动生成的镜像标签命名规范如下：

- master branch：master_{git_project_name}时间戳，可重复构建
- feature branch：feature_{feature_name}时间戳，可重复构建
- release branch：{release_name}，不重复构建

.. note:: Feature branch是指非release branch以外的branch（不以release开头）

## 后续操作

流水线运行完成后，可编辑、删除流水线，回滚流水线的部署，查询流水线历史运行记录。

<!--end-->
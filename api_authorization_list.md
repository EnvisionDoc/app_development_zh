# API和权限对应表

为了确保安全访问，以下EnOS API对调用权限进行了限制，需要购买应用的OU授予应用ID相应的权限策略后，应用才可以调用相应的API。有关EnOS内的用户权限，参见[策略，角色，与权限](/docs/iam/zh_CN/latest/access_policy)。


| 接口	| 服务	| 资源权限|
| ------ | ------ | ------ |
| getAsset	| 资产	| Read|
| deleteAsset	| 资产	| Write|
| createAsset	| 接入配置	| Full Access|
| updateAsset	| 资产	| Write|
| listAssets	| 接入配置	| Read|
| insertNode	| 资产树管理	| Full Access|
| getNode	| 资产树管理	| Read|
| listChildNodes	| 资产树管理	| Read|
| searchNodes	| 资产树管理	| Read|
| deleteNode	| 资产树管理	| Full Access|
| deleteAllNodesAndAsset	| 资产树管理	| Full Access|
| bindAssetToNode	| 资产树管理	| Full Access|
| updateNodeName	| 资产树管理	| Full Access|
| searchNodePaths	| 资产树管理	| Read|
| createTree	| 资产树管理	| Full Access|
| listTrees	| 资产树管理	| Read|
| getTree	| 资产树管理	| Read|
| getThingModel	| 模型管理	| Read|
| listThingModels	| 模型管理	| Read|
| setMeasurepointByDeviceKey	| 资产	| Control|
| setMeasurepointByAssetId	| 资产	| Control|
| invokeServiceByDeviceKey	| 资产	| Control|
| invokeServiceByAssetId	| 资产	| Control|
| listProductTags	| 接入配置	| Read|
| updateProductTags	| 接入配置	| Full Access|
| deleteProductTags	| 接入配置	| Full Access|
| listProducts	| 接入配置	| Read|
| getProduct	| 接入配置	| Read|
| createProduct	| 接入配置	| Full Access|
| updateProduct	| 接入配置	| Full Access|
| deleteProduct	| 接入配置	| Full Access|
| listTopologyByDeviceKey	| 接入配置	| Read|
| listTopologyByAssetId	| 接入配置	| Read|
| createTopologyByDeviceKey	| 接入配置	| Full Access|
| createTopologyByAssetId	| 接入配置	| Full Access|
| deleteTopologyByDeviceKey	| 接入配置	| Full Access|
| deleteTopologyByAssetId	| 接入配置	| Full Access|
| listDeviceTagsByDeviceKey	| 接入配置	| Read|
| listDeviceTagsByAssetId	| 接入配置	| Read|
| updateDeviceTagsByDeviceKey	| 接入配置	| Full Access|
| updateDeviceTagsByAssetId	| 接入配置	| Full Access|
| deleteDeviceTagsByDeviceKey	| 接入配置	| Full Access|
| deleteDeviceTagsByAssetId	| 接入配置	| Full Access|
| uploadDeviceMeasurepoints	| 接入配置	| Full Access|
| checkDevices	| 接入配置	| Read|
| getMeasurepointsDataByDeviceKey	| 接入配置	| Read|
| getMeasurepointsDataByAssetID	| 接入配置	| Read|
| registerDevices	| 接入配置	| Full Access|
| listDevices	| 接入配置	| Read|
| getDeviceByDeviceKey	| 接入配置	| Read|
| getDeviceByAssetId	| 接入配置	| Read|
| updateDeviceByDeviceKey	| 接入配置	| Full Access|
| updateDeviceByAssetId	| 接入配置	| Full Access|
| deleteDeviceByDeviceKey	| 接入配置	| Full Access|
| deleteDeviceByAssetId	| 接入配置	| Full Access|
| getDeviceStatusByDeviceKeys	| 接入配置	| Read|
| getDeviceStatusByAssetIds	| 接入配置	| Read|
| getDeviceStatistics	| 接入配置	| Read|
| disableDeviceByDeviceKey	| 接入配置	| Full Access|
| disableDeviceByAssetId	| 接入配置	| Full Access|
| enableDeviceByDeviceKey	| 接入配置	| Full Access|
| applyCertificateByDeviceKey	| 接入配置	| Full Access|
| applyCertificateByAssetId	| 接入配置	| Full Access|
| revokeCertificateByDeviceKey	| 接入配置	| Full Access|
| revokeCertificateByAssetId	| 接入配置	| Full Access|
| listCertificatesByDeviceKey	| 接入配置	| Read|
| listCertificatesByAssetId	| 接入配置	| Read|



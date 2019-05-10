# API和权限对应表

为了确保安全访问，以下EnOS API对调用权限进行了限制，需要资源的所有者OU授予应用服务账号相应的权限策略后，应用才可以调用相应的API。有关EnOS内的用户权限，参见[策略，角色，与权限](/docs/iam/zh_CN/latest/access_policy)。


| 接口	| 服务	| 资源权限|
| ------ | ------ | ------ |
| deleteAsset	| 资产	| Write|
| createAsset	| 设备管理	| Full Access|
| updateAsset	| 资产	| Write|
| insertNode	| 资产树管理	| Full Access|
| deleteNode	| 资产树管理	| Full Access|
| deleteAllNodesAndAsset	| 资产树管理	| Full Access|
| bindAssetToNode	| 资产树管理	| Full Access|
| updateNodeName	| 资产树管理	| Full Access|
| createTree	| 资产树管理	| Full Access|
| setMeasurepointByDeviceKey	| 资产	| Control|
| setMeasurepointByAssetId	| 资产	| Control|
| invokeServiceByDeviceKey	| 资产	| Control|
| invokeServiceByAssetId	| 资产	| Control|
| updateProductTags	| 设备管理	| Full Access|
| deleteProductTags	| 设备管理	| Full Access|
| createProduct	| 设备管理	| Full Access|
| updateProduct	| 设备管理	| Full Access|
| deleteProduct	| 设备管理	| Full Access|
| createTopologyByDeviceKey	| 设备管理	| Full Access|
| createTopologyByAssetId	| 设备管理	| Full Access|
| deleteTopologyByDeviceKey	| 设备管理	| Full Access|
| deleteTopologyByAssetId	| 设备管理	| Full Access|
| updateDeviceTagsByDeviceKey	| 设备管理	| Full Access|
| updateDeviceTagsByAssetId	| 设备管理	| Full Access|
| deleteDeviceTagsByDeviceKey	| 设备管理	| Full Access|
| deleteDeviceTagsByAssetId	| 设备管理	| Full Access|
| uploadDeviceMeasurepoints	| 设备管理	| Full Access|
| registerDevices	| 设备管理	| Full Access|
| updateDeviceByDeviceKey	| 设备管理	| Full Access|
| updateDeviceByAssetId	| 设备管理	| Full Access|
| deleteDeviceByDeviceKey	| 设备管理	| Full Access|
| deleteDeviceByAssetId	| 设备管理	| Full Access|
| disableDeviceByDeviceKey	| 设备管理	| Full Access|
| disableDeviceByAssetId	| 设备管理	| Full Access|
| enableDeviceByDeviceKey	| 设备管理	| Full Access|
| applyCertificateByDeviceKey	| 设备管理	| Full Access|
| applyCertificateByAssetId	| 设备管理	| Full Access|
| revokeCertificateByDeviceKey	| 设备管理	| Full Access|
| revokeCertificateByAssetId	| 设备管理	| Full Access|



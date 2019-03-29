# API和权限对应表

为了确保安全访问，以下EnOS API对调用权限进行了限制，需要购买应用的OU授予应用ID相应的权限策略后，应用才可以调用相应的API。有关EnOS内的用户权限，参见[策略，角色，与权限](/docs/iam/zh_CN/dev/access_policy)。


| 接口	| 服务	| 资源权限| 
| ------ | ------ | ------ |
| getAsset	| 资产	| read| 
| deleteAsset	| 资产	| write| 
| createAsset	| 接入配置	| full_access| 
| updateAsset	| 资产	| write| 
| listAssets	| 接入配置	| read| 
| insertNode	| 资产树管理	| full_access| 
| getNode	| 资产树管理	| read| 
| listChildNodes	| 资产树管理	| read| 
| searchNodes	| 资产树管理	| read| 
| deleteNode	| 资产树管理	| full_access| 
| deleteAllNodesAndAsset	| 资产树管理	| full_access| 
| bindAssetToNode	| 资产树管理	| full_access| 
| updateNodeName	| 资产树管理	| full_access| 
| searchNodePaths	| 资产树管理	| read| 
| createTree	| 资产树管理	| full_access| 
| listTrees	| 资产树管理	| read| 
| getTree	| 资产树管理	| read| 
| getThingModel	| 模型管理	| read| 
| listThingModels	| 模型管理	| read| 
| setMeasurepointByDeviceKey	| 资产	| control| 
| setMeasurepointByAssetId	| 资产	| control| 
| invokeServiceByDeviceKey	| 资产	| control| 
| invokeServiceByAssetId	| 资产	| control| 
| listProductTags	| 接入配置	| read| 
| updateProductTags	| 接入配置	| full_access| 
| deleteProductTags	| 接入配置	| full_access| 
| listProducts	| 接入配置	| read| 
| getProduct	| 接入配置	| read| 
| createProduct	| 接入配置	| full_access| 
| updateProduct	| 接入配置	| full_access| 
| deleteProduct	| 接入配置	| full_access| 
| listTopologyByDeviceKey	| 接入配置	| read| 
| listTopologyByAssetId	| 接入配置	| read| 
| createTopologyByDeviceKey	| 接入配置	| full_access| 
| createTopologyByAssetId	| 接入配置	| full_access| 
| deleteTopologyByDeviceKey	| 接入配置	| full_access| 
| deleteTopologyByAssetId	| 接入配置	| full_access| 
| listDeviceTagsByDeviceKey	| 接入配置	| read| 
| listDeviceTagsByAssetId	| 接入配置	| read| 
| updateDeviceTagsByDeviceKey	| 接入配置	| full_access| 
| updateDeviceTagsByAssetId	| 接入配置	| full_access| 
| deleteDeviceTagsByDeviceKey	| 接入配置	| full_access| 
| deleteDeviceTagsByAssetId	| 接入配置	| full_access| 
| uploadDeviceMeasurepoints	| 接入配置	| full_access| 
| checkDevices	| 接入配置	| read| 
| getMeasurepointsDataByDeviceKey	| 接入配置	| read| 
| getMeasurepointsDataByAssetID	| 接入配置	| read| 
| registerDevices	| 接入配置	| full_access| 
| listDevices	| 接入配置	| read| 
| getDeviceByDeviceKey	| 接入配置	| read| 
| getDeviceByAssetId	| 接入配置	| read| 
| updateDeviceByDeviceKey	| 接入配置	| full_access| 
| updateDeviceByAssetId	| 接入配置	| full_access| 
| deleteDeviceByDeviceKey	| 接入配置	| full_access| 
| deleteDeviceByAssetId	| 接入配置	| full_access| 
| getDeviceStatusByDeviceKeys	| 接入配置	| read| 
| getDeviceStatusByAssetIds	| 接入配置	| read| 
| getDeviceStatistics	| 接入配置	| read| 
| disableDeviceByDeviceKey	| 接入配置	| full_access| 
| disableDeviceByAssetId	| 接入配置	| full_access| 
| enableDeviceByDeviceKey	| 接入配置	| full_access| 
| applyCertificateByDeviceKey	| 接入配置	| full_access| 
| applyCertificateByAssetId	| 接入配置	| full_access| 
| revokeCertificateByDeviceKey	| 接入配置	| full_access| 
| revokeCertificateByAssetId	| 接入配置	| full_access| 
| listCertificatesByDeviceKey	| 接入配置	| read| 
| listCertificatesByAssetId	| 接入配置	| read| 



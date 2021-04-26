# API列表

以下是物联网络管理平台API列表。

|API|描述|
|---|--|
|[GetUserLicense](/cn.zh-CN/云端开发指南/云端API参考/基础管理/GetUserLicense.md)|获取用户合约信息|
|[ListFreqBandPlanGroups](/cn.zh-CN/云端开发指南/云端API参考/基础管理/ListFreqBandPlanGroups.md)|获取频谱计划组支持列表|
|[GetFreqBandPlanGroup](/cn.zh-CN/云端开发指南/云端API参考/基础管理/GetFreqBandPlanGroup.md)|获取频谱计划组信息|

## 网关管理相关API

|API|描述|
|---|--|
|[CreateGateway](/cn.zh-CN/云端开发指南/云端API参考/网关管理/CreateGateway.md)|新增网关|
|[DeleteGateway](/cn.zh-CN/云端开发指南/云端API参考/网关管理/DeleteGateway.md)|删除网关|
|[UpdateGateway](/cn.zh-CN/云端开发指南/云端API参考/网关管理/UpdateGateway.md)|更新网关信息|
|[UpdateGatewayEnablingState](/cn.zh-CN/云端开发指南/云端API参考/网关管理/UpdateGatewayEnablingState.md)|更新网关启用状态|
|[GetGateway](/cn.zh-CN/云端开发指南/云端API参考/网关管理/GetGateway.md)|获取网关信息|
|[ListGateways](/cn.zh-CN/云端开发指南/云端API参考/网关管理/ListGateways.md)|获取网关信息列表|
|[CountGateways](/cn.zh-CN/云端开发指南/云端API参考/网关管理/CountGateways.md)|获取符合条件的网关数量|
|[ListGatewaysGisInfo](/cn.zh-CN/云端开发指南/云端API参考/网关管理/ListGatewaysGisInfo.md)|获取所有网关的地理位置信息|

## 网络管理相关API

|API|描述|
|---|--|
|[CreateLocalJoinPermission](/cn.zh-CN/云端开发指南/云端API参考/网络管理/CreateLocalJoinPermission.md)|创建专用入网凭证|
|[DeleteLocalJoinPermission](/cn.zh-CN/云端开发指南/云端API参考/网络管理/DeleteLocalJoinPermission.md)|删除专用入网凭证|
|[UpdateOwnedLocalJoinPermission](/cn.zh-CN/云端开发指南/云端API参考/网络管理/UpdateOwnedLocalJoinPermission.md)|更新专用入网凭证的信息|
|[UpdateOwnedLocalJoinPermissionEnablingState](/cn.zh-CN/云端开发指南/云端API参考/网络管理/UpdateOwnedLocalJoinPermissionEnablingState.md)|更新专用入网凭证的启停状态|
|[GetOwnedJoinPermission](/cn.zh-CN/云端开发指南/云端API参考/网络管理/GetOwnedJoinPermission.md)|获取入网凭证基本信息|
|[ListOwnedJoinPermissions](/cn.zh-CN/云端开发指南/云端API参考/网络管理/ListOwnedJoinPermissions.md)|获取符合条件的入网凭证列表|
|[CountOwnedJoinPermissions](/cn.zh-CN/云端开发指南/云端API参考/网络管理/CountOwnedJoinPermissions.md)|获取符合条件的入网凭证数量|
|[GetRentedJoinPermission](/cn.zh-CN/云端开发指南/云端API参考/网络管理/GetRentedJoinPermission.md)|获取租用入网凭证的基本信息|
|[ListRentedJoinPermissions](/cn.zh-CN/云端开发指南/云端API参考/网络管理/ListRentedJoinPermissions.md)|获取符合条件的租用入网凭证列表|
|[CountRentedJoinPermissions](/cn.zh-CN/云端开发指南/云端API参考/网络管理/CountRentedJoinPermissions.md)|获取符合条件的租用入网凭证数量|
|[ReturnJoinPermission](/cn.zh-CN/云端开发指南/云端API参考/网络管理/ReturnJoinPermission.md)|退租入网凭证|
|[SubmitJoinPermissionAuthOrder](/cn.zh-CN/云端开发指南/云端API参考/网络管理/SubmitJoinPermissionAuthOrder.md)|发起入网凭证授权流程|
|[CancelJoinPermissionAuthOrder](/cn.zh-CN/云端开发指南/云端API参考/网络管理/CancelJoinPermissionAuthOrder.md)|取消入网凭证授权流程|
|[AcceptJoinPermissionAuthOrder](/cn.zh-CN/云端开发指南/云端API参考/网络管理/AcceptJoinPermissionAuthOrder.md)|同意入网凭证授予|
|[RejectJoinPermissionAuthOrder](/cn.zh-CN/云端开发指南/云端API参考/网络管理/RejectJoinPermissionAuthOrder.md)|拒绝入网凭证授予|
|[GetJoinPermissionAuthOrder](/cn.zh-CN/云端开发指南/云端API参考/网络管理/GetJoinPermissionAuthOrder.md)|获取入网凭证授权详情|

## 节点管理相关API

|API|描述|
|---|--|
|[CreateNodeGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/CreateNodeGroup.md)|创建节点分组|
|[DeleteNodeGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/DeleteNodeGroup.md)|删除节点分组|
|[UpdateNodeGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/UpdateNodeGroup.md)|更新节点分组的信息|
|[GetNodeGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/GetNodeGroup.md)|获取节点分组详情|
|[ListNodeGroups](/cn.zh-CN/云端开发指南/云端API参考/节点管理/ListNodeGroups.md)|获取符合条件的节点分组列表|
|[CountNodeGroups](/cn.zh-CN/云端开发指南/云端API参考/节点管理/CountNodeGroups.md)|获取符合条件的节点分组数量|
|[BindJoinPermissionToNodeGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/BindJoinPermissionToNodeGroup.md)|分配入网凭证于节点分组|
|[UnbindJoinPermissionFromNodeGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/UnbindJoinPermissionFromNodeGroup.md)|取消入网凭证于节点分组|
|[UpdateDataDispatchConfig](/cn.zh-CN/云端开发指南/云端API参考/节点管理/UpdateDataDispatchConfig.md)|更新数据流转配置|
|[UpdateDataDispatchEnablingState](/cn.zh-CN/云端开发指南/云端API参考/节点管理/UpdateDataDispatchEnablingState.md)|更新数据流转出口的启停用|
|[AddNodeToGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/AddNodeToGroup.md)|增加节点到节点分组|
|[RemoveNodeFromGroup](/cn.zh-CN/云端开发指南/云端API参考/节点管理/RemoveNodeFromGroup.md)|删除节点分组中的节点|
|[GetNode](/cn.zh-CN/云端开发指南/云端API参考/节点管理/GetNode.md)|获取节点信息|
|[ListNodesByOwnedJoinPermissionId](/cn.zh-CN/云端开发指南/云端API参考/节点管理/ListNodesByOwnedJoinPermissionId.md)|获取专用凭证下的节点列表|
|[ListNodesByNodeGroupId](/cn.zh-CN/云端开发指南/云端API参考/节点管理/ListNodesByNodeGroupId.md)|获取节点分组下的节点列表|
|[CountNodesByOwnedJoinPermissionId](/cn.zh-CN/云端开发指南/云端API参考/节点管理/CountNodesByOwnedJoinPermissionId.md)|获取符合凭证条件的节点数量|
|[CountNodesByNodeGroupId](/cn.zh-CN/云端开发指南/云端API参考/节点管理/CountNodesByNodeGroupId.md)|获取符合分组条件的节点数量|

## 计量统计相关API

|API|描述|
|---|--|
|[ListGatewayTransferPackets](/cn.zh-CN/云端开发指南/云端API参考/报表查询/ListGatewayTransferPackets.md)|获取网关上下行数据包|
|[GetGatewayTransferPacketsDownloadUrl](/cn.zh-CN/云端开发指南/云端API参考/报表查询/GetGatewayTransferPacketsDownloadUrl.md)|获取网关上下行数据CVS文件|
|[ListNodeGroupTransferPackets](/cn.zh-CN/云端开发指南/云端API参考/报表查询/ListNodeGroupTransferPackets.md)|获取节点分组上下行数据包|
|[GetNodeGroupTransferPacketsDownloadUrl](/cn.zh-CN/云端开发指南/云端API参考/报表查询/GetNodeGroupTransferPacketsDownloadUrl.md)|获取节点分组上下行数据CVS文件|
|[ListNodeTransferPacketPaths](/cn.zh-CN/云端开发指南/云端API参考/报表查询/ListNodeTransferPacketPaths.md)|获取节点上行路径详情|
|[GetNodeTransferPacket](/cn.zh-CN/云端开发指南/云端API参考/报表查询/GetNodeTransferPacket.md)|获取数据包历史详情|
|[ListGatewayTransferFlowStats](/cn.zh-CN/云端开发指南/云端API参考/报表查询/ListGatewayTransferFlowStats.md)|获取网关流量统计|
|[ListNodeGroupTransferFlowStats](/cn.zh-CN/云端开发指南/云端API参考/报表查询/ListNodeGroupTransferFlowStats.md)|获取节点组流量统计|
|[ListGatewayOnlineRecords](/cn.zh-CN/云端开发指南/云端API参考/报表查询/ListGatewayOnlineRecords.md)|获取网关在线离线记录|
|[ListActiveGateways](/cn.zh-CN/云端开发指南/云端API参考/报表查询/ListActiveGateways.md)|获取今日活跃网关|
|[GetGatewayStatusStat](/cn.zh-CN/云端开发指南/云端API参考/报表查询/GetGatewayStatusStat.md)|获取网关状态|
|[GetGatewayPacketStat](/cn.zh-CN/云端开发指南/云端API参考/报表查询/GetGatewayPacketStat.md)|获取网关维度数据有效数|

## 事件通知相关API

|API|描述|
|---|--|
|[GetNotification](/cn.zh-CN/云端开发指南/云端API参考/事件通知/GetNotification.md)|获取通知信息|
|[CountNotifications](/cn.zh-CN/云端开发指南/云端API参考/事件通知/CountNotifications.md)|获取符合条件的通知数量|
|[ListNotifications](/cn.zh-CN/云端开发指南/云端API参考/事件通知/ListNotifications.md)|获取通知列表|
|[UpdateNotificationsHandleState](/cn.zh-CN/云端开发指南/云端API参考/事件通知/UpdateNotificationsHandleState.md)|更新通知的处理状态|

## 上下行数据相关API

|API|描述|
|---|--|
|[t1616750.dita\#doc\_api\_LinkWAN\_SendUnicastCommand](/cn.zh-CN/云端开发指南/云端API参考/上下行数据/SendUnicastCommand.md)|发送 下行数据|


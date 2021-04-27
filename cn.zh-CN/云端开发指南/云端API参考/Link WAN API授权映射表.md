# Link WAN API授权映射表

定义授权策略，将具体某些API方法的访问权限授予RAM用户。

为RAM用户授权的具体方法，请参见[自定义权限](/cn.zh-CN/用户指南/RAM授权管理/自定义权限.md)。

以下表格列举了物联网络管理平台的API操作名称及对应资源名称，即您在创建相关授权策略时参数**Action**与**Resource**的可选值。每个单独的表格代表了一类资源相关的授权。

## 网关安全元组工单

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|SubmitGatewayTupleOrder|linkwan:SubmitGatewayTupleOrder|acs:linkwan:\*:\*:gateway-tuple-order/\*|提交网关安全元组的申请单。|
|GetGatewayTupleOrder|linkwan:GetGatewayTupleOrder|acs:linkwan:\*:\*:gateway-tuple-order/$\{orderId\}|获取网关安全元组申请单的信息。|
|CountGatewayTupleOrders|linkwan:CountGatewayTupleOrders|acs:linkwan:\*:\*:gateway-tuple-order/\*|获取网关安全元组申请单的数量。|
|ListGatewayTupleOrders|linkwan:ListGatewayTupleOrders|acs:linkwan:\*:\*:gateway-tuple-order/\*|查询网关安全元组申请单列表。|

## 节点安全元组工单

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|SubmitNodeTupleOrder|linkwan:SubmitNodeTupleOrder|acs:linkwan:\*:\*:node-tuple-order/\*|提交节点安全元组的申请单。|
|GetNodeTupleOrder|linkwan:GetNodeTupleOrder|acs:linkwan:\*:\*:node-tuple-order/$\{orderId\}|获取节点安全元组申请单的信息。|
|CountNodeTupleOrders|linkwan:CountNodeTupleOrders|acs:linkwan:\*:\*:node-tuple-order/\*|获取节点安全元组申请单的数量。|
|ListNodeTupleOrders|linkwan:ListNodeTupleOrders|acs:linkwan:\*:\*:node-tuple-order/\*|查询节点安全元组申请单列表。|

## 网关安全元组

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|GetGatewayTuplesDownloadUrl|linkwan:GetGatewayTuplesDownloadUrl|acs:linkwan:\*:\*:gateway-tuple/\* 与 acs:linkwan:\*:\*:gateway-tuple-order/$\{orderId\}|根据申请单获取网关安全元组的下载链接。|

## 节点安全元组

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|GetNodeTuplesDownloadUrl|linkwan:GetNodeTuplesDownloadUrl|acs:linkwan:\*:\*:node-tuple/\* 与 acs:linkwan:\*:\*:node-tuple-order/$\{orderId\}|根据申请单获取节点安全元组的下载链接。|

## 拥有的入网凭证

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|CreateLocalJoinPermission|linkwan:CreateLocalJoinPermission|acs:linkwan:\*:\*:owned-join-permission/\*|创建专用入网凭证。|
|DeleteLocalJoinPermission|linkwan:DeleteLocalJoinPermission|acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|删除专用入网凭证。|
|UpdateOwnedLocalJoinPermission|linkwan:UpdateOwnedLocalJoinPermission|acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|更新专用入网凭证。|
|UpdateOwnedLocalJoinPermissionEnablingState|linkwan:UpdateOwnedLocalJoinPermissionEnablingState|acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|启停专用入网凭证。|
|GetOwnedJoinPermission|linkwan:GetOwnedJoinPermission|acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|获取专用入网凭证信息。|
|ListOwnedJoinPermissions|linkwan:ListOwnedJoinPermissions|acs:linkwan:\*:\*:owned-join-permission/\*|查询专用入网凭证列表。|
|CountOwnedJoinPermissions|linkwan:CountOwnedJoinPermissions|acs:linkwan:\*:\*:owned-join-permission/\*|获取专用入网凭证的数量。|

## 租用的入网凭证

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|ApplyRoamingJoinPermission|linkwan:ApplyRoamingJoinPermission|acs:linkwan:\*:\*:rented-join-permission/\*|申请泛在入网凭证。|
|ReturnJoinPermission|linkwan:ReturnJoinPermission|acs:linkwan:\*:\*:rented-join-permission/$\{joinPermissionId\}|退换入网凭证（包括专用和泛在凭证）。|
|UpdateRoamingJoinPermission|linkwan:UpdateRoamingJoinPermission|acs:linkwan:\*:\*:rented-join-permission/$\{joinPermissionId\}|更新泛在入网凭证。|
|UpdateRoamingJoinPermissionEnablingState|linkwan:UpdateRoamingJoinPermissionEnablingState|acs:linkwan:\*:\*:rented-join-permission/$\{joinPermissionId\}|启停泛在入网凭证。|
|GetRentedJoinPermission|linkwan:GetRentedJoinPermission|acs:linkwan:\*:\*:rented-join-permission/$\{joinPermissionId\}|获取租用的入网凭证信息。|
|ListRentedJoinPermissions|linkwan:ListRentedJoinPermissions|acs:linkwan:\*:\*:rented-join-permission/\*|查询租用的入网凭证列表。|
|CountRentedJoinPermissions|linkwan:CountRentedJoinPermissions|acs:linkwan:\*:\*:rented-join-permission/\*|获取租用的入网凭证数量。|

## 专用入网凭证授权工单

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|SubmitJoinPermissionAuthOrder|linkwan:SubmitJoinPermissionAuthOrder|acs:linkwan:\*:\*:join-permission-auth-order/\* 与 acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|提交授权工单，发起向目标凭证租户的授权。|
|CancelJoinPermissionAuthOrder|linkwan:CancelJoinPermissionAuthOrder|acs:linkwan:\*:\*:join-permission-auth-order/$\{joinPermissionOrderId\}|取消授权工单。|
|AcceptJoinPermissionAuthOrder|linkwan:AcceptJoinPermissionAuthOrder|acs:linkwan:\*:\*:join-permission-auth-order/$\{joinPermissionOrderId\}|接受授权工单，成为凭证的租户。|
|RejectJoinPermissionAuthOrder|linkwan:RejectJoinPermissionAuthOrder|acs:linkwan:\*:\*:join-permission-auth-order/$\{joinPermissionOrderId\}|拒绝授权工单。|
|GetJoinPermissionAuthOrder|linkwan:GetJoinPermissionAuthOrder|acs:linkwan:\*:\*:join-permission-auth-order/$\{joinPermissionOrderId\}|获取授权工单信息。|
|GetLatestApplyingJoinPermissionAuthOrder|linkwan:GetLatestApplyingJoinPermissionAuthOrder|acs:linkwan:\*:\*:join-permission-auth-order/\* 与 acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|获取针对指定入网凭证的正在进行中的授权工单。|

## 网关

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|CreateGateway|linkwan:CreateGateway|acs:linkwan:\*:\*:gateway/\*|录入网关。|
|DeleteGateway|linkwan:DeleteGateway|acs:linkwan:\*:\*:gateway/$\{gwEui\}|删除网关。|
|UpdateGateway|linkwan:UpdateGateway|acs:linkwan:\*:\*:gateway/$\{gwEui\}|更新网关信息。|
|UpdateGatewayEnablingState|linkwan:UpdateGatewayEnablingState|acs:linkwan:\*:\*:gateway/$\{gwEui\}|启停网关。|
|GetGateway|linkwan:GetGateway|acs:linkwan:\*:\*:gateway/$\{gwEui\}|获取网关信息。|
|CountGateways|linkwan:CountGateways|acs:linkwan:\*:\*:gateway/\*|获取网关数量。|
|ListGateways|linkwan:ListGateways|acs:linkwan:\*:\*:gateway/\*|查询网关列表。|
|ListGatewaysGisInfo|linkwan:ListGatewaysGisInfo|acs:linkwan:\*:\*:gateway/\*|列举网关的地理信息。|

## 节点分组

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|CreateNodeGroup|linkwan:CreateNodeGroup|acs:linkwan:\*:\*:node-group/\*|创建节点分组。|
|DeleteNodeGroup|linkwan:DeleteNodeGroup|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|删除节点分组。|
|UpdateNodeGroup|linkwan:UpdateNodeGroup|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|更新节点分组配置。|
|GetNodeGroup|linkwan:GetNodeGroup|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|获取节点分组信息。|
|ListNodeGroups|linkwan:ListNodeGroups|acs:linkwan:\*:\*:node-group/\*|查询节点分组列表。|
|CountNodeGroups|linkwan:CountNodeGroups|acs:linkwan:\*:\*:node-group/\*|获取节点分组数量。|
|BindJoinPermissionToNodeGroup|linkwan:BindJoinPermissionToNodeGroup|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\} 与 acs:linkwan:\*:\*:rented-join-permission/$\{joinPermissionId\}|将节点分组与入网凭证关联。|
|UnbindJoinPermissionFromNodeGroup|linkwan:UnbindJoinPermissionFromNodeGroup|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\} 与 acs:linkwan:\*:\*:rented-join-permission/$\{joinPermissionId\}|解除节点分组与入网凭证的关联。|
|UpdateDataDispatchConfig|linkwan:UpdateDataDispatchConfig|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|设定节点分组的数据流转配置。|
|EmptyDataDispatchConfig|linkwan:EmptyDataDispatchConfig|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|清空节点分组的数据流转配置。|
|UpdateDataDispatchEnablingState|linkwan:UpdateDataDispatchEnablingState|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|启停节点分组的数据流转能力。|
|AddNodeToGroup|linkwan:AddNodeToGroup|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|录入节点到节点分组。|
|RemoveNodeFromGroup|linkwan:RemoveNodeFromGroup|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|从节点分组删除节点。|
|SubmitNodesAddingTask|linkwan:SubmitNodesAddingTask|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\} 与 acs:linkwan:\*:\*:node-adding-task/\*|提交批量录入任务，向节点分组录入批量节点。|
|GetNodesAddingTask|linkwan:GetNodesAddingTask|acs:linkwan:\*:\*:node-group/$\{nodeGroupId\} 与 acs:linkwan:\*:\*:node-adding-task/$\{taskId\}|查询批量录入任务。|

## 节点

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|SendUnicastCommand|linkwan:SendUnicastCommand|acs:linkwan:\*:\*:node/$\{devEui\}|向节点发送业务数据。|
|GetNode|linkwan:GetNode|acs:linkwan:\*:\*:node/$\{devEui\}|获取节点信息。|
|CountNodes|linkwan:CountNodes|acs:linkwan:\*:\*:node/\*|获取节点数量。|
|ListNodes|linkwan:ListNodes|acs:linkwan:\*:\*:node/\*|查询节点列表。|
|ListNodesByOwnedJoinPermissionId|linkwan:ListNodesByOwnedJoinPermissionId|acs:linkwan:\*:\*:node/\* 与 acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|查询使用指定入网凭证的节点列表。|
|ListNodesByNodeGroupId|linkwan:ListNodesByNodeGroupId|acs:linkwan:\*:\*:node/\* 与 acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|在指定的节点分组中查询节点列表。|
|CountNodesByOwnedJoinPermissionId|linkwan:CountNodesByOwnedJoinPermissionId|acs:linkwan:\*:\*:node/\* 与 acs:linkwan:\*:\*:owned-join-permission/$\{joinPermissionId\}|获取使用指定入网凭证的节点的数量。|
|CountNodesByNodeGroupId|linkwan:CountNodesByNodeGroupId|acs:linkwan:\*:\*:node/\* 与 acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|获取指定节点分组中的节点数量。|

## 频段

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|GetFreqBandPlanGroup|linkwan:GetFreqBandPlanGroup|acs:linkwan:\*:\*:freq-band-plan/$\{freqBandPlanGroupId\}|获取频段详细信息。|
|ListFreqBandPlanGroups|linkwan:ListFreqBandPlanGroups|acs:linkwan:\*:\*:freq-band-plan/\*|查询频段列表。|

## 报表

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|ListGatewayTransferPackets|linkwan:ListGatewayTransferPackets|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:gateway/$\{gwEui\}|查询网关数据包详情报表。|
|GetGatewayTransferPacketsDownloadUrl|linkwan:GetGatewayTransferPacketsDownloadUrl|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:gateway/$\{gwEui\}|获取网关数据包详情报表下载 URL。|
|ListNodeGroupTransferPackets|linkwan:ListNodeGroupTransferPackets|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|查询节点分组数据包详情报表。|
|GetNodeGroupTransferPacketsDownloadUrl|linkwan:GetNodeGroupTransferPacketsDownloadUrl|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|获取节点分组数据包详情报表下载URL。|
|ListGatewayTransferFlowStats|linkwan:ListGatewayTransferFlowStats|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:gateway/$\{gwEui\}|查询网关数据包量分时统计报表。|
|ListNodeGroupTransferFlowStats|linkwan:ListNodeGroupTransferFlowStats|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:node-group/$\{nodeGroupId\}|查询节点分组数据包量分时统计报表。|
|ListGatewayOnlineRecords|linkwan:ListGatewayOnlineRecords|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:gateway/$\{gwEui\}|查询网关在离线记录。|
|ListActiveGateways|linkwan:ListActiveGateways|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:gateway/\*|查询今日活跃网关列表。|
|GetGatewayStatusStat|linkwan:GetGatewayStatusStat|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:gateway/$\{gwEui\}|查询网关运行状态。|
|GetGatewayPacketStat|linkwan:GetGatewayPacketStat|acs:linkwan:\*:\*:diagram 与 acs:linkwan:\*:\*:gateway/$\{gwEui\}|查询网关数据包的分类统计。|

## 事件（通知）

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|ListNotifications|linkwan:ListNotifications|acs:linkwan:\*:\*:event/\*|查询通知列表。|
|CountNotifications|linkwan:CountNotifications|acs:linkwan:\*:\*:event/\*|获取通知数量。|
|GetNotification|linkwan:GetNotification|acs:linkwan:\*:\*:event/$\{eventId\}|获取通知信息。|
|UpdateNotificationsHandleState|linkwan:UpdateNotificationsHandleState|acs:linkwan:\*:\*:event/$\{eventId\}|更新通知的处理状态。|

## 用户

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|GetUserDescription|linkwan:GetUserDescription|acs:linkwan:\*:\*:user-license/\*|获取当前用户的描述信息。|
|GetUserLicense|linkwan:GetUserLicense|acs:linkwan:\*:\*:user-license/\*|获取当前用户的合约信息。|
|ListActivatedFeatures|linkwan:ListActivatedFeatures|acs:linkwan:\*:\*:feature/\*|获取当前用户已经开通的功能列表。|

## 数据流转

**说明：** 如果希望RAM用户能够在物联网络管理平台的控制台配置节点分组的数据流转，请务必授权本节的操作与资源。

|API 方法|操作名称（Action）|资源名称（Resource）|说明|
|------|------------|--------------|--|
|ListIotProducts|linkwan:ListIotProducts|acs:linkwan:\*:\*:data-dispatch/\*|获取阿里云物联网平台的产品列表，用于配置数据流转。|
|ListOnsUplinkTopics|linkwan:ListOnsUplinkTopics|acs:linkwan:\*:\*:data-dispatch/\*|获取阿里云消息队列的Topic列表，用于配置数据流转。|


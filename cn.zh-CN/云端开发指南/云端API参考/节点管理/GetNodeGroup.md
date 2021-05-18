# GetNodeGroup

调用GetNodeGroup获取节点分组信息。

## 限制说明

-   如果在企业版实例中调用该接口，请求参数**IotInstanceId**必须填写。否则，调用接口会失败。
-   单阿里云账号调用该接口的每秒请求数（QPS）最大限制为5。

**说明：** RAM用户共享阿里云账号配额。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=GetNodeGroup&type=RPC&version=2019-03-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetNodeGroup|系统规定参数。取值：**GetNodeGroup**。 |
|NodeGroupId|String|是|123456|节点分组ID，可调用[ListNodeGroups](~~109944~~)接口查询获取。 |
|IotInstanceId|String|否|iot-cn-0pp1n8t\*\*\*\*|实例ID。

 -   企业版实例：必须传入此参数。您可在物联网平台控制台的**实例概览**页面，查看您的企业版实例ID。
-   公共实例：无需传入此参数。 |

调用API时，除了本文介绍的该API的特有请求参数，还需传入公共请求参数。公共请求参数说明，请参见[公共参数文档](~~108601~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |调用成功时返回的节点分组信息列表。 |
|ClassMode|String|A|节点分组中的节点所采用的LoRaWAN Class模式，与分组所关联的入网凭证中指定的一致。 |
|CreateMillis|Long|1514736000000|节点分组的创建时间，格式为UNIX时间戳，以毫秒为单位。 |
|DataDispatchConfig|Struct| |节点分组的数据流转配置。 |
|Destination|String|IOT|数据流转目的地。返回值：

 -   **IOT**：数据流转到物联网平台的产品。
-   **ONS**：数据流转到MQ的Topic。 |
|IotProduct|Struct| |如果流转目的地是物联网平台的产品，该字段存储产品信息。 |
|DebugSwitch|Boolean|true|数据流转目的地为**IOT**的调试开关。返回值：

 -   **true**：打开调试开关。
-   **false**：关闭调试开关。 |
|ProductKey|String|HMyB\*\*\*\*\*\*\*|产品的ProductKey。 |
|ProductName|String|产品名|产品名称。 |
|ProductType|String|IOT\_SUITE|产品类型。返回值：

 -   **IOT\_SUITE**：数据流转到IoT套件基础版。
-   **IOT\_SUITE\_SENIOR**：数据流转到IoT套件高级版。 |
|OnsTopics|Struct| |如果流转目的地是MQ，该字段存储MQ Topic信息。 |
|DownlinkRegionName|String|cn-beijing|MQ下行Region ID。 |
|DownlinkTopic|String|topic1|MQ下行Topic。 |
|UplinkRegionName|String|cn-hangzhou|MQ上行Region ID。 |
|UplinkTopic|String|topic2|MQ上行Topic。 |
|DataDispatchEnabled|Boolean|false|节点分组的数据流转启停状态。返回值：

 -   **true**：启用。
-   **false**：停用。 |
|FreqBandPlanGroupId|Long|102|节点分组中的节点采用的频段ID，与分组所关联的入网凭证中指定的一致。 |
|JoinEui|String|0000000000000000|节点分组中的节点使用的JoinEUI，与分组所关联的入网凭证中指定的JoinEUI一致。 |
|JoinPermissionEnabled|Boolean|true|与节点分组关联的入网凭证的启停状态。返回值：

 -   **true**：启用。
-   **false**：停用。 |
|JoinPermissionId|String|1234569|与节点分组关联的入网凭证的ID。 |
|JoinPermissionName|String|凭证1|与节点分组关联的入网凭证的名称。 |
|JoinPermissionOwnerAliyunId|String|some-user|-   如果关联的是专用凭证，该字段表示入网凭证拥有者的阿里云账号。
-   如果关联的是泛在凭证，该字段值为**AliCloud IoT**。 |
|JoinPermissionType|String|LOCAL|与节点分组关联的入网凭证类型。返回值：

 -   **LOCAL**：专用凭证。
-   **ROAMING**：泛在凭证。 |
|Locks|Array of Locks| |节点分组所关联的操作锁列表。 |
|CreateMillis|Long|1514736000000|锁的创建时间。 |
|Enabled|Boolean|true|锁的启停用状态。 |
|LockId|String|123|锁ID。 |
|LockType|String|WRITE|锁的类型。取值：**WRITE**，表示所有写操作都加锁，包括编辑、删除等。 |
|MulticastEnabled|Boolean|false|节点分组所关联的组播组是否被启用。返回值：

 -   **true**：启用。
-   **false**：停用。 |
|MulticastGroupId|String|1234|节点分组所关联的组播组ID。 |
|MulticastNodeCapacity|Integer|1000|节点分组所关联的组播组能够容纳的节点数量。 |
|MulticastNodeCount|Integer|10|节点分组所关联的组播组当前已经添加的节点数量。 |
|NodeGroupId|String|123456|节点分组ID。 |
|NodeGroupName|String|节点分组名称|节点分组的名称。 |
|NodesCnt|Long|10|节点分组中的节点数量。 |
|RxDailySum|String|0|与节点分组关联的入网凭证的当天上行数据包量。 |
|RxMonthSum|Long|0|与节点分组关联的入网凭证的当月上行数据包量。 |
|TxDailySum|Long|0|与节点分组关联的入网凭证的当天下行数据包量。 |
|TxMonthSum|Long|0|与节点分组关联的入网凭证的当月下行数据包量。 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|阿里云为该请求生成的唯一标识符。 |
|Success|Boolean|true|是否调用成功。返回值：

 -   **true**：调用成功。
-   **false**：调用失败。 |

## 示例

请求示例

```
http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=GetNodeGroup
&NodeGroupId=123456
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
<Data>
    <NodesCnt>10</NodesCnt>
    <RxMonthSum>0</RxMonthSum>
    <ClassMode>A</ClassMode>
    <MulticastNodeCapacity>1000</MulticastNodeCapacity>
    <NodeGroupName>节点分组名称</NodeGroupName>
    <RxDailySum>0</RxDailySum>
    <TxDailySum>0</TxDailySum>
    <TxMonthSum>0</TxMonthSum>
    <MulticastNodeCount>10</MulticastNodeCount>
    <MulticastEnabled>false</MulticastEnabled>
    <JoinPermissionType>LOCAL</JoinPermissionType>
    <JoinPermissionOwnerAliyunId>some-user</JoinPermissionOwnerAliyunId>
    <NodeGroupId>123456</NodeGroupId>
    <MulticastGroupId>1234</MulticastGroupId>
    <CreateMillis>1514736000000</CreateMillis>
    <JoinPermissionId>1234569</JoinPermissionId>
    <JoinPermissionName>凭证1</JoinPermissionName>
    <JoinPermissionEnabled>true</JoinPermissionEnabled>
    <FreqBandPlanGroupId>102</FreqBandPlanGroupId>
    <JoinEui>0</JoinEui>
    <DataDispatchEnabled>false</DataDispatchEnabled>
    <Locks>
        <CreateMillis>1514736000000</CreateMillis>
        <Enabled>true</Enabled>
        <LockType>WRITE</LockType>
        <LockId>123</LockId>
    </Locks>
    <DataDispatchConfig>
        <Destination>IOT</Destination>
        <IotProduct>
            <DebugSwitch>true</DebugSwitch>
            <ProductName>产品名</ProductName>
            <ProductType>IOT_SUITE</ProductType>
            <ProductKey>HMyB*******</ProductKey>
        </IotProduct>
        <OnsTopics/>
    </DataDispatchConfig>
</Data>
<Success>true</Success>
```

`JSON`格式

```
{
    "RequestId": "89EF6CAA-958F-F32C-BE45-FE003C6DE097",
    "Data": {
        "NodesCnt": 10,
        "RxMonthSum": 0,
        "ClassMode": "A",
        "MulticastNodeCapacity": 1000,
        "NodeGroupName": "节点分组名称",
        "RxDailySum": 0,
        "TxDailySum": 0,
        "TxMonthSum": 0,
        "MulticastNodeCount": 10,
        "MulticastEnabled": false,
        "JoinPermissionType": "LOCAL",
        "JoinPermissionOwnerAliyunId": "some-user",
        "NodeGroupId": 123456,
        "MulticastGroupId": 1234,
        "CreateMillis": 1514736000000,
        "JoinPermissionId": 1234569,
        "JoinPermissionName": "凭证1",
        "JoinPermissionEnabled": true,
        "FreqBandPlanGroupId": 102,
        "JoinEui": 0,
        "DataDispatchEnabled": false,
        "Locks": {
            "CreateMillis": 1514736000000,
            "Enabled": true,
            "LockType": "WRITE",
            "LockId": 123
        },
        "DataDispatchConfig": {
            "Destination": "IOT",
            "IotProduct": {
                "DebugSwitch": true,
                "ProductName": "产品名",
                "ProductType": "IOT_SUITE",
                "ProductKey": "HMyB*******"
            },
            "OnsTopics": { }
        }
    },
    "Success": true
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ForbiddenByRam|User not authorized to operate on the specified resource, or this API does not support RAM.|用户没有执行该操作所需要的RAM权限。|
|400|ForbiddenByRiskControl|This operation cannot be performed because of security risks.|存在安全风险，无法执行该操作|
|400|NonExistent|The specified resource does not exist.|要操作的资源不存在。|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|NotResourceOwner|You are not authorized to use this resource.|无权访问此资源|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


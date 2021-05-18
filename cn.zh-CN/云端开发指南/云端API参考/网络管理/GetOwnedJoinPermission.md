# GetOwnedJoinPermission

调用GetOwnedJoinPermission获取当前阿里云账号拥有的专用入网凭证信息。

## 限制说明

-   如果在企业版实例中调用该接口，请求参数**IotInstanceId**必须填写。否则，调用接口会失败。
-   单阿里云账号调用该接口的每秒请求数（QPS）最大限制为5。

**说明：** RAM用户共享阿里云账号配额。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=GetOwnedJoinPermission&type=RPC&version=2019-03-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetOwnedJoinPermission|系统规定参数。取值：**GetOwnedJoinPermission**。 |
|JoinPermissionId|String|是|123|要获取的入网凭证的ID，可调用[ListOwnedJoinPermissions](~~109924~~)接口查询获取。 |
|IotInstanceId|String|否|iot\_instc\_pu\*\*\*\*\_c\*-v64\*\*\*\*\*\*\*\*|实例ID。

 -   企业版实例：必须传入此参数。您可在物联网平台控制台的**实例概览**页面，查看您的企业版实例ID。
-   公共实例：无需传入此参数。 |

调用API时，除了本文介绍的该API的特有请求参数，还需传入公共请求参数。公共请求参数说明，请参见[公共参数](~~108601~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |调用成功时返回的入网凭证的信息列表。 |
|AuthState|String|NEW|入网凭证的授权状态。返回值：

 -   **NEW**：未授权。
-   **APPLYING**：授权中。
-   **ACCEPTED**：已授权。 |
|BoundProductName|String|产品名称|流转到物联网平台的具体产品名称。

 **说明：** 当凭证绑定了节点分组，且该分组配置了数据流转到物联网平台的产品时，才会返回此参数。 |
|ClassMode|String|A|入网凭证采用的LoRaWAN Class模式。 |
|CreateMillis|Long|1514736000000|入网凭证的创建时间。格式为UNIX时间戳，单位为毫秒。 |
|DataDispatchDestination|String|IOT|数据流转目的地。返回值：

 -   **IOT**：数据流转到物联网平台的产品。
-   **ONS**：数据流转到MQ的Topic。 |
|DataRate|Long|4|数据速率。 |
|Enabled|Boolean|true|入网凭证的启停用状态。返回值：

 -   **true**：启用。
-   **false**：停用。 |
|FreqBandPlanGroupId|Long|102|入网凭证采用的频段ID。 |
|JoinEui|String|0000000000000000|入网凭证使用的JoinEUI。 |
|JoinPermissionId|String|123|入网凭证ID。 |
|JoinPermissionName|String|凭证1|入网凭证的名称。 |
|MulticastEnabled|Boolean|false|入网凭证组播的启停用状态。返回值：

 -   **true**：启用。
-   **false**：停用。 |
|MulticastNodeCapacity|Integer|1000|入网凭证可接入组播节点容量。 |
|MulticastNodeCount|Integer|10|入网凭证已接入组播节点数量。

 **说明：** 仅当**MulticastEnabled**参数设置为**true**时返回。 |
|NodesCnt|Long|10|使用该入网凭证的节点的数量。 |
|RenterAliyunId|String|some-user|入网凭证租户的阿里云账号。 |
|RxDailySum|Long|0|入网凭证的当天上行数据包量。 |
|RxDelay|Long|1|Class A的接收窗口延迟时间。 |
|RxMonthSum|Long|0|入网凭证的当月上行数据包量。 |
|TxDailySum|Long|0|入网凭证的当天下行数据包量。 |
|TxMonthSum|Long|0|入网凭证的当月下行数据包量。 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|阿里云为该请求生成的唯一标识符。 |
|Success|Boolean|true|是否调用成功。返回值：

 -   **true**：调用成功。
-   **false**：调用失败。 |

## 示例

请求示例

```
http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=GetOwnedJoinPermission
&JoinPermissionId=123
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
    <RxDailySum>0</RxDailySum>
    <TxDailySum>0</TxDailySum>
    <Enabled>true</Enabled>
    <RenterAliyunId>some-user</RenterAliyunId>
    <TxMonthSum>0</TxMonthSum>
    <MulticastNodeCount>10</MulticastNodeCount>
    <MulticastEnabled>false</MulticastEnabled>
    <RxDelay>1</RxDelay>
    <DataDispatchDestination>IOT</DataDispatchDestination>
    <AuthState>NEW</AuthState>
    <DataRate>4</DataRate>
    <BoundProductName>产品名称</BoundProductName>
    <CreateMillis>1514736000000</CreateMillis>
    <JoinPermissionId>123</JoinPermissionId>
    <JoinPermissionName>凭证1</JoinPermissionName>
    <FreqBandPlanGroupId>102</FreqBandPlanGroupId>
    <JoinEui>0000000000000000</JoinEui>
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
        "RxDailySum": 0,
        "TxDailySum": 0,
        "Enabled": true,
        "RenterAliyunId": "some-user",
        "TxMonthSum": 0,
        "MulticastNodeCount": 10,
        "MulticastEnabled": false,
        "RxDelay": 1,
        "DataDispatchDestination": "IOT",
        "AuthState": "NEW",
        "DataRate": 4,
        "BoundProductName": "产品名称",
        "CreateMillis": 1514736000000,
        "JoinPermissionId": 123,
        "JoinPermissionName": "凭证1",
        "FreqBandPlanGroupId": 102,
        "JoinEui": 0
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


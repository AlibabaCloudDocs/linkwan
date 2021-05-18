# ListOwnedJoinPermissions

调用ListOwnedJoinPermissions查询当前阿里云账号拥有的专用入网凭证列表。

## 限制说明

-   如果在企业版实例中调用该接口，请求参数**IotInstanceId**必须填写。否则，调用接口会失败。
-   单阿里云账号调用该接口的每秒请求数（QPS）最大限制为5。

**说明：** RAM用户共享阿里云账号配额。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=ListOwnedJoinPermissions&type=RPC&version=2019-03-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListOwnedJoinPermissions|系统规定参数。取值：**ListOwnedJoinPermissions**。 |
|Limit|Long|是|2|本次查询的入网凭证的数量。 |
|Offset|Long|是|0|本次查询的起始位置，从0开始。 |
|IotInstanceId|String|否|iot\_instc\_pu\*\*\*\*\_c\*-v64\*\*\*\*\*\*\*\*|实例ID。

 -   企业版实例：必须传入此参数。您可在物联网平台控制台的**实例概览**页面，查看您的企业版实例ID。
-   公共实例：无需传入此参数。 |
|FuzzyRenterAliyunId|String|否|some-user|模糊匹配入网凭证租户的阿里云账号。 |
|FuzzyJoinEui|String|否|d896e0|模糊匹配入网凭证所使用的JoinEUI。 |
|Enabled|Boolean|否|false|专用入网凭证的启停用状态。取值：

 -   **true**：启用。
-   **false**：停用。 |
|FuzzyJoinPermissionName|String|否|凭证1|模糊匹配入网凭证的名称。 |
|SortingField|String|否|CREATED\_MILLIS|指定排序字段。取值为**CREATED\_MILLIS**，表示根据创建时间排序。 |
|Ascending|Boolean|否|true|配合**SortingField**参数一起使用，指定字段排序方式。取值：

 -   **true**：升序。
-   **false**：降序。 |

调用API时，除了本文介绍的该API的特有请求参数，还需传入公共请求参数。公共请求参数说明，请参见[公共参数](~~108601~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |调用成功时返回的当前阿里云账号拥有的专用入网凭证列表。 |
|List|Array of JoinPermission| |专用入网凭证列表。 |
|AuthState|String|ACCEPTED|入网凭证的授权状态。返回值：

 -   **NEW**：未授权。
-   **APPLYING**：授权中。
-   **ACCEPTED**：已授权。 |
|ClassMode|String|A|入网凭证采用的LoRaWAN Class模式。 |
|DataRate|Long|4|数据速率。 |
|Enabled|Boolean|true|入网凭证的启停用状态。返回值：

 -   **true**：启用。
-   **false**：停用。 |
|FreqBandPlanGroupId|Long|102|入网凭证采用的频段ID。 |
|JoinEui|String|d896e0efff00\*\*\*\*|入网凭证使用的JoinEUI。 |
|JoinPermissionId|String|50184|入网凭证的ID。 |
|JoinPermissionName|String|凭证1|入网凭证的名称。 |
|RenterAliyunId|String|some-user1|入网凭证租户的阿里云账号。 |
|RxDelay|Long|1|Class A的接收窗口延迟时间。 |
|TotalCount|Long|7|专用入网凭证总数。 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|阿里云为该请求生成的唯一标识符。 |
|Success|Boolean|true|是否调用成功。返回值：

 -   **true**：调用成功。
-   **false**：调用失败。 |

## 示例

请求示例

```
http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=ListOwnedJoinPermissions
&Limit=2
&Offset=0
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
<Data>
    <TotalCount>7</TotalCount>
    <List>
        <ClassMode>A</ClassMode>
        <AuthState>ACCEPTED</AuthState>
        <DataRate>4</DataRate>
        <Enabled>true</Enabled>
        <RenterAliyunId>some-user1</RenterAliyunId>
        <JoinPermissionId>50184</JoinPermissionId>
        <JoinPermissionName>凭证1</JoinPermissionName>
        <FreqBandPlanGroupId>102</FreqBandPlanGroupId>
        <JoinEui>d896e0efff00****</JoinEui>
        <RxDelay>1</RxDelay>
    </List>
</Data>
<Success>true</Success>
```

`JSON`格式

```
{
    "RequestId": "89EF6CAA-958F-F32C-BE45-FE003C6DE097",
    "Data": {
        "TotalCount": 7,
        "List": {
            "ClassMode": "A",
            "AuthState": "ACCEPTED",
            "DataRate": 4,
            "Enabled": true,
            "RenterAliyunId": "some-user1",
            "JoinPermissionId": 50184,
            "JoinPermissionName": "凭证1",
            "FreqBandPlanGroupId": 102,
            "JoinEui": "d896e0efff00****",
            "RxDelay": 1
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
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|CloudProductNotActivated|The Link WAN service has not been activated.|未开通 Link WAN 云产品|
|400|FeatureNotActivated|The feature has not been activated.|功能未开通|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


# UpdateOwnedLocalJoinPermission

调用UpdateOwnedLocalJoinPermission更新当前阿里云账号拥有的专用入网凭证。

## 限制说明

-   如果在企业版实例中调用该接口，请求参数**IotInstanceId**必须填写。否则，调用接口会失败。
-   单阿里云账号调用该接口的每秒请求数（QPS）最大限制为5。

**说明：** RAM用户共享阿里云账号配额。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=UpdateOwnedLocalJoinPermission&type=RPC&version=2019-03-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateOwnedLocalJoinPermission|系统规定参数。取值：**UpdateOwnedLocalJoinPermission**。 |
|JoinPermissionId|String|是|123|专用入网凭证ID，可调用[ListRentedJoinPermissions](~~109924~~)接口查询获取。 |
|IotInstanceId|String|否|iot-cn-0pp1n8t\*\*\*\*|实例ID。

 -   企业版实例：必须传入此参数。您可在物联网平台控制台的**实例概览**页面，查看您的企业版实例ID。
-   公共实例：无需传入此参数。 |
|FreqBandPlanGroupId|Long|否|201|专用入网凭证采用的频段ID，可调用[ListFreqBandPlanGroups](~~108614~~)接口查询获取。 |
|ClassMode|String|否|A|专用入网凭证采用的LoRaWAN Class模式。取值：A、B、C。 |
|JoinPermissionName|String|否|凭证1|自定义入网凭证名称。支持中文、英文字母、数字和下划线（\_），长度限制4～30个字符，一个中文占两个字符。 |
|RxDelay|String|否|1|Class A的接收窗口延时时间，取值范围1s~15s。 |
|DataRate|String|否|4|数据速率，取值范围0~5。 |
|JoinEui|String|否|0000000000000001|凭证使用的JoinEUI，为16位HEX。 |

调用API时，除了本文介绍的该API的特有请求参数，还需传入公共请求参数。公共请求参数说明，请参见[公共参数文档](~~108601~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|阿里云为该请求生成的唯一标识符。 |
|Success|Boolean|true|是否调用成功。返回值：

 -   **true**：调用成功。
-   **false**：调用失败。 |

## 示例

请求示例

```
http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=UpdateOwnedLocalJoinPermission
&JoinPermissionId=123
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateOwnedLocalJoinPermissionResponse>
        <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
        <Success>true</Success>
</UpdateOwnedLocalJoinPermissionResponse>
```

`JSON`格式

```
{
	"RequestId":"89EF6CAA-958F-F32C-BE45-FE003C6DE097",
	"Success":true
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ForbiddenByRam|User not authorized to operate on the specified resource, or this API does not support RAM.|用户没有执行该操作所需要的RAM权限。|
|400|ForbiddenByRiskControl|This operation cannot be performed because of security risks.|存在安全风险，无法执行该操作|
|400|NonExistent|The specified resource does not exist.|要操作的资源不存在。|
|400|CloudProductNotActivated|The Link WAN service has not been activated.|未开通 Link WAN 云产品|
|400|FeatureNotActivated|The feature has not been activated.|功能未开通|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|JoinPermissionAlreadyAuthorized|The specified join permission has already been granted to another renter.|入网凭证已经授权给了其它用户|
|400|NotResourceOwner|You are not authorized to use this resource.|无权访问此资源|
|400|JoinPermissionNameDuplicated|The specified join permission name already exists.|入网凭证名称重复|
|400|InvalidName|The specified name is invalid.|名称不合法|
|400|InvalidFreqBandPlan|The frequency band plan is invalid.|频段计划不可用|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


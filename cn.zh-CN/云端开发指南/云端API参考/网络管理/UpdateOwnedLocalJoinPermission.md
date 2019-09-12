# UpdateOwnedLocalJoinPermission {#doc_api_LinkWAN_UpdateOwnedLocalJoinPermission .reference}

调用UpdateOwnedLocalJoinPermission更新当前用户账号所拥有的专用入网凭证。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=UpdateOwnedLocalJoinPermission&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateOwnedLocalJoinPermission|系统规定参数。取值：**UpdateOwnedLocalJoinPermission**。

 |
|JoinPermissionId|String|是|123|专用入网凭证ID，用来指定要更新的入网凭证。

 |
|ClassMode|String|否|A|专用入网凭证采用的LoRaWAN Class模式，用于更新旧的 Class 模式。可取值：**A**、**B**、**C**。

 |
|FreqBandPlanGroupId|Long|否|201|专用入网凭证所采用的频段的频段ID，用于更新旧频段。

 |
|JoinPermissionName|String|否|凭证1|自定义入网凭证名称，用于更新旧名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=UpdateOwnedLocalJoinPermission
&JoinPermissionId=123
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateOwnedLocalJoinPermissionResponse>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</UpdateOwnedLocalJoinPermissionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"89EF6CAA-958F-F32C-BE45-FE003C6DE097",
	"Success":true
}
```

## 错误码 { .section}

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


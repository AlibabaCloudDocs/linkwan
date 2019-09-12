# CreateLocalJoinPermission {#doc_api_LinkWAN_CreateLocalJoinPermission .reference}

调用CreateLocalJoinPermission创建专用入网凭证。当前用户账号将成为该凭证的拥有者，拥有该凭证。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=CreateLocalJoinPermission&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLocalJoinPermission|系统规定参数。取值：**CreateLocalJoinPermission**。

 |
|ClassMode|String|是|A|专用入网凭证采用的LoRaWAN Class模式。可取值：**A**、**B**、**C**。

 |
|FreqBandPlanGroupId|Long|是|101|专用入网凭证所采用的频段的频段ID。

 |
|JoinPermissionName|String|是|test|自定义专用入网凭证名称。

 |
|UseDefaultJoinEui|Boolean|是|true|专用入网凭证是否使用阿里云统一JoinEUI。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|String|123|所创建的专用入网凭证的ID。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=CreateLocalJoinPermission
&ClassMode=A
&FreqBandPlanGroupId=101
&JoinPermissionName=test
&UseDefaultJoinEui=true
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateLocalJoinPermissionResponse>
      <Data>123</Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</CreateLocalJoinPermissionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":"123",
	"RequestId":"89EF6CAA-958F-F32C-BE45-FE003C6DE097",
	"Success":true
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ForbiddenByRam|User not authorized to operate on the specified resource, or this API does not support RAM.|用户没有执行该操作所需要的RAM权限。|
|400|ForbiddenByRiskControl|This operation cannot be performed because of security risks.|存在安全风险，无法执行该操作|
|400|ExceedLocalJoinPermissionLimit|The maximum number of local join permissions that you can create is exceeded.|超出本地凭证已购买额度|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|JoinPermissionNameDuplicated|The specified join permission name already exists.|入网凭证名称重复|
|400|InvalidName|The specified name is invalid.|名称不合法|
|400|InvalidFreqBandPlan|The frequency band plan is invalid.|频段计划不可用|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


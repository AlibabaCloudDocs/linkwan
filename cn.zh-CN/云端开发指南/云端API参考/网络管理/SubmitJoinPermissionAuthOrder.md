# SubmitJoinPermissionAuthOrder {#doc_api_LinkWAN_SubmitJoinPermissionAuthOrder .reference}

调用SubmitJoinPermissionAuthOrder发起专用入网凭证授权工单。

网络运营者可以通过该接口向开发者（解决方案供应商）授权一个专用入网凭证。不过只是发起了一个授权工单，需待开发者接受该授权后，授权才能完成。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=SubmitJoinPermissionAuthOrder&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SubmitJoinPermissionAuthOrder|系统规定参数。取值：**SubmitJoinPermissionAuthOrder**。

 |
|JoinPermissionId|String|是|123|要授权的专用入网凭证ID。

 |
|RenterAliyunId|String|是|some\_user|要授权的开发者的阿里云账号ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Long|1234|授权工单ID。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=SubmitJoinPermissionAuthOrder
&JoinPermissionId=123
&RenterAliyunId=some_user
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SubmitJoinPermissionAuthOrderResponse>
      <Data>1234</Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</SubmitJoinPermissionAuthOrderResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":"1234",
	"RequestId":"89EF6CAA-958F-F32C-BE45-FE003C6DE097",
	"Success":true
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ForbiddenByRam|User not authorized to operate on the specified resource, or this API does not support RAM.|用户没有执行该操作所需要的RAM权限。|
|400|ForbiddenByRiskControl|This operation cannot be performed because of security risks.|存在安全风险，无法执行该操作|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|CloudProductNotActivated|The Link WAN service has not been activated.|未开通 Link WAN 云产品|
|400|FeatureNotActivated|The feature has not been activated.|功能未开通|
|400|TooManyRenterNonExistentFailures|You have entered invalid renter usernames for several times. Try again later.|被授权者账号名输入错误次数过多，请稍后再试。|
|400|JoinPermissionAlreadyAuthorized|The specified join permission has already been granted to another renter.|入网凭证已经授权给了其它用户|
|400|RenterDoesNotExist|The specified renter does not exist.|被授权的用户不存在|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


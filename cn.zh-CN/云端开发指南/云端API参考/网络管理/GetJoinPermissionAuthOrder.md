# GetJoinPermissionAuthOrder {#doc_api_LinkWAN_GetJoinPermissionAuthOrder .reference}

调用GetJoinPermissionAuthOrder获取专用凭证授权工单的详细信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=GetJoinPermissionAuthOrder&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetJoinPermissionAuthOrder|系统规定参数。取值：**GetJoinPermissionAuthOrder**。

 |
|OrderId|String|是|123|授权工单ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |授权工单的详细信息。

 |
|AcceptedMillis|Long|1514736000000|工单被接受的 UNIX 时间戳，以毫秒为单位。

 |
|ApplyingMillis|Long|1514736000000|发起工单的 UNIX 时间戳，以毫秒为单位。

 |
|CanceledMillis|Long|1514736000000|工单被取消的 UNIX 时间戳，以毫秒为单位。

 |
|JoinPermissionId|String|123456|要授权的专用入网凭证ID。

 |
|OrderId|String|123|授权工单ID。

 |
|OrderState|String|ACCEPTED|工单状态。取值：

 -   **APPLYING**：工单发起，等待目标租户处理。
-   **ACCEPTED**：工单被接受。
-   **REJECTED**：工单被回绝。
-   **CANCELED**：工单被取消。

 |
|OwnerAliyunId|String|some\_user|发起授权的专用入网凭证拥有者的阿里云账号ID。

 |
|RejectedMillis|Long|1514736000000|工单被回绝的 UNIX 时间戳，以毫秒为单位。

 |
|RenterAliyunId|String|some\_user|专用入网凭证的目标租户的阿里云账号ID。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=GetJoinPermissionAuthOrder
&OrderId=123
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetJoinPermissionAuthOrderResponse>
      <Data>
            <OrderId>123</OrderId>
            <CanceledMillis>1514736000000</CanceledMillis>
            <RejectedMillis>1514736000000</RejectedMillis>
            <ApplyingMillis>1514736000000</ApplyingMillis>
            <RenterAliyunId>some_user</RenterAliyunId>
            <OrderState>ACCEPTED</OrderState>
            <OwnerAliyunId>some_user</OwnerAliyunId>
            <JoinPermissionId>123456</JoinPermissionId>
            <AcceptedMillis>1514736000000</AcceptedMillis>
      </Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</GetJoinPermissionAuthOrderResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":{
		"CanceledMillis":1514736000000,
		"JoinPermissionId":"123456",
		"OrderState":"ACCEPTED",
		"RenterAliyunId":"some_user",
		"RejectedMillis":1514736000000,
		"OwnerAliyunId":"some_user",
		"OrderId":"123",
		"ApplyingMillis":1514736000000,
		"AcceptedMillis":1514736000000
	},
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
|400|NonExistent|The specified resource does not exist.|要操作的资源不存在。|
|400|NotResourceOwner|You are not authorized to use this resource.|无权访问此资源|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


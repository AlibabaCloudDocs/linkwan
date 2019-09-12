# GetNotification {#doc_api_LinkWAN_GetNotification .reference}

调用GetNotification获取通知信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=GetNotification&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetNotification|系统规定参数。取值：**GetNotification**。

 |
|NotificationId|String|是|123|通知ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |通知信息列表。

 |
|Category|String|GATEWAY\_OFFLINE|通知分类。取值：

 -   **GATEWAY\_OFFLINE**：网关离线信息。
-   **JOIN\_PERMISSION\_AUTH\_APPLYING**：凭证授权信息。
-   **JOIN\_PERMISSION\_AUTH\_ACCEPTED**：凭证授权信息。
-   **JOIN\_PERMISSION\_AUTH\_CANCELED**：凭证授权信息。
-   **JOIN\_PERMISSION\_AUTH\_REJECTED**：凭证授权信息。

 |
|GatewayOfflineInfo| | |网关离线信息。

 当**Category**为**GATEWAY\_OFFLINE**时该字段有值。

 |
|GwEui|String|0000000000000000|网关唯一标识。

 |
|OfflineMillis|Long|1514736000000|离线时间，毫秒为单位的UNIX时间戳。

 |
|HandleState|String|UNHANDLED|此通知的处理状态。可取值为**HANDLED**\(已处理\)，**UNHANDLED**\(未处理\)。

 |
|HandledMillis|Long|1514736000001|通知被处理的时间，毫秒为单位的UNIX时间戳。

 |
|JoinPermissionAuthInfo| | |凭证授权信息。

 当**Category**为**JOINPERMISSION\_AUTH**时该字段有值。

 |
|AcceptedMillis|Long|1514736000000|工单审批通过的UNIX时间戳 ，毫秒为单位。

 |
|ApplyingMillis|Long|1514736000000|发起工单的UNIX时间戳，毫秒为单位。

 |
|CanceledMillis|Long|1514736000000|工单被取消的UNIX时间戳，毫秒为单位。

 |
|JoinEui|String|d896e0|入网凭证所使用的JoinEUI。

 |
|JoinPermissionId|String|123|唯一标识入网凭证的ID。

 |
|JoinPermissionName|String|凭证1|入网凭证的名称。

 |
|OrderId|String|123|工单ID。

 |
|OrderState|String|ACCEPTED|工单状态。取值：

 -   **APPLYING**：工单发起，等待批准。
-   **ACCEPTED**：工单被批准。
-   **REJECTED**：工单被拒绝。
-   **CANCELED**：工单被取消。

 |
|OwnerAliyunId|String|some-user1|发起授权的入网凭证拥有者的阿里云账号ID。

 |
|RejectedMillis|Long|1514736000000|工单被拒绝的UNIX时间戳，毫秒为单位。

 |
|RenterAliyunId|String|some-user2|入网凭证租户的阿里云账号ID。

 |
|NoticeMillis|Long|1514736000000|通知发出的时间，毫秒为单位的UNIX时间戳。

 |
|NotificationId|String|123|通知ID。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=GetNotification
&NotificationId=123
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetNotificationResponse>
      <Data>
            <Category>GATEWAY_OFFLINE</Category>
            <GatewayOfflineInfo>
                  <GwEui>0000000000000000</GwEui>
                  <OfflineMillis>1514736000000</OfflineMillis>
            </GatewayOfflineInfo>
            <HandleUtcMilli>1514736000001</HandleUtcMilli>
            <HandleState>UNHANDLED</HandleState>
            <NotificationId>123</NotificationId>
            <NoticeUtcMilli>1514736000000</NoticeUtcMilli>
      </Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</GetNotificationResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":{
		"NoticeUtcMilli":1514736000000,
		"HandleUtcMilli":1514736000001,
		"HandleState":"UNHANDLED",
		"Category":"GATEWAY_OFFLINE",
		"GatewayOfflineInfo":{
			"OfflineMillis":1514736000000,
			"GwEui":"0000000000000000"
		},
		"NotificationId":"123"
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


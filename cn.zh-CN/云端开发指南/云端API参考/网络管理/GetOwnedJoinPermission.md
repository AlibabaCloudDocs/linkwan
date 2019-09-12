# GetOwnedJoinPermission {#doc_api_LinkWAN_GetOwnedJoinPermission .reference}

调用GetOwnedJoinPermission根据入网凭证ID获取当前用户账号所拥有的入网凭证。

**说明：** 通过该接口获取的一定是当前用户账号所拥有的某个专用入网凭证。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=GetOwnedJoinPermission&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetOwnedJoinPermission|系统规定参数。取值：**GetOwnedJoinPermission**。

 |
|JoinPermissionId|String|是|123|要获取的入网凭证的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |所拥有入网凭证的信息列表。

 |
|AuthState|String|NEW|入网凭证的授权状态。取值：

 -   **NEW**：未授权
-   **APPLYING**：授权中
-   **ACCEPTED**：已授权

 |
|ClassMode|String|A|入网凭证采用的LoRaWAN Class模式。取值：**A**、**B**、**C**。

 |
|CreateMillis|Long|1514736000000|入网凭证的创建时间。格式为 UNIX 时间戳，单位毫秒。

 |
|DataDispatchDestination|String|IOT|数据流转目的地。取值：

 -   **IOT**：数据流转到IoT的产品。
-   **ONS**：数据流转到MQ的Topic。

 |
|Enabled|Boolean|true|入网凭证的启停用状态。

 |
|FreqBandPlanGroupId|Long|102|入网凭证所采用的频段的频段ID。

 |
|JoinEui|String|0000000000000000|入网凭证所使用的JoinEUI。

 |
|JoinPermissionId|String|123|入网凭证ID。

 |
|JoinPermissionName|String|凭证1|入网凭证的名称。

 |
|NodesCnt|Long|10|使用该入网凭证的节点的数量。

 |
|RenterAliyunId|String|some-user|入网凭证租户的阿里云账号ID。

 |
|RxDailySum|Long|0|入网凭证的当天上行数据包量。

 |
|RxMonthSum|Long|0|入网凭证的当月上行数据包量。

 |
|TxDailySum|Long|0|入网凭证的当天下行数据包量。

 |
|TxMonthSum|Long|0|入网凭证的当月下行数据包量。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=GetOwnedJoinPermission
&JoinPermissionId=123
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetOwnedJoinPermissionResponse>
      <Data>
            <JoinEui>0000000000000000</JoinEui>
            <ClassMode>A</ClassMode>
            <RxDailySum>0</RxDailySum>
            <Enabled>true</Enabled>
            <CreateMillis>1514736000000</CreateMillis>
            <RxMonthSum>0</RxMonthSum>
            <RenterAliyunId>some-user</RenterAliyunId>
            <TxDailySum>0</TxDailySum>
            <NodesCnt>10</NodesCnt>
            <TxMonthSum>0</TxMonthSum>
            <JoinPermissionId>123</JoinPermissionId>
            <DataDispatchDestination>IOT</DataDispatchDestination>
            <JoinPermissionName>凭证1</JoinPermissionName>
            <FreqBandPlanGroupId>102</FreqBandPlanGroupId>
      </Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</GetOwnedJoinPermissionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":{
		"Enabled":true,
		"NodesCnt":10,
		"DataDispatchDestination":"IOT",
		"RenterAliyunId":"some-user",
		"RxDailySum":0,
		"JoinEui":"0000000000000000",
		"ClassMode":"A",
		"JoinPermissionName":"凭证1",
		"JoinPermissionId":"123",
		"FreqBandPlanGroupId":102,
		"TxDailySum":0,
		"TxMonthSum":0,
		"CreateMillis":1514736000000,
		"RxMonthSum":0
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
|400|NonExistent|The specified resource does not exist.|要操作的资源不存在。|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|NotResourceOwner|You are not authorized to use this resource.|无权访问此资源|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


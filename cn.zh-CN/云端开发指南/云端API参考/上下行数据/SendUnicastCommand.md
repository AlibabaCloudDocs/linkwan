# SendUnicastCommand {#doc_api_LinkWAN_SendUnicastCommand .reference}

调用SendUnicastCommand发送单播信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=SendUnicastCommand&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SendUnicastCommand|系统规定参数。取值：**SendUnicastCommand**。

 |
|Content|String|是|xxx|要发送的内容。

 |
|DevEui|String|是|0000000000000000|目标节点。

 |
|FPort|Integer|是|0|fPort。

 |
|CleanUp|Boolean|否|false|是否清空该节点的堆积指令，并下发该指令。默认为**false**。

 |
|Comfirmed|Boolean|否|false|是否是confirmed指令，默认为**false**。

 |
|MaxRetries|Integer|否|1|最大重发次数，默认为**0**。

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

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=SendUnicastCommand
&Content=xxx
&DevEui=0000000000000000
&FPort=0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SendUnicastCommandResponse>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</SendUnicastCommandResponse>
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
|400|Abandoned|An error occurred while processing this request, because the API has been abandoned.|该接口已经被废弃。|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|CloudProductNotActivated|The Link WAN service has not been activated.|未开通 Link WAN 云产品|
|400|FeatureNotActivated|The feature has not been activated.|功能未开通|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


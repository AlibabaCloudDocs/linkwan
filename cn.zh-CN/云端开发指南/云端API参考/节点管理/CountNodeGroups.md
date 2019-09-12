# CountNodeGroups {#doc_api_LinkWAN_CountNodeGroups .reference}

调用CountNodeGroups统计符合过滤条件的节点分组总数。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=CountNodeGroups&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CountNodeGroups|系统规定参数。取值：**CountNodeGroups**。

 |
|FuzzyDevEui|String|否|d896e0|模糊匹配节点分组中节点的 DevEUI。

 |
|FuzzyJoinEui|String|否|d896e0|模糊匹配节点分组中节点所使用的 JoinEUI。

 |
|FuzzyName|String|否|group1|模糊匹配节点分组名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Long|100|满足过滤条件的节点分组总数。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=CountNodeGroups
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CountNodeGroupsResponse>
      <Data>100</Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</CountNodeGroupsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":100,
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

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


# GetFreqBandPlanGroup {#doc_api_LinkWAN_GetFreqBandPlanGroup .reference}

调用GetFreqBandPlanGroup获取频段信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=GetFreqBandPlanGroup&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetFreqBandPlanGroup|系统规定参数。取值：**GetFreqBandPlanGroup**。

 |
|GroupId|Long|是|201|频段ID。

 |
|RegionId|String|否|cn-hangzhou|地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |频段信息。

 |
|BeginFrequency|Long|923|起始频点，单位为MHz。

 |
|EndFrequency|Long|925|结束频点，单位为MHz。

 |
|FrequencyRegionId|String|CN|Region标识。

 |
|FrequencyType|String|SAME\_FREQUENCY|频段类型。取值范围：

 -   **SAME\_FREQUENCY**：同频
-   **DIFF\_FREQUENCY**：异频

 |
|GroupId|Long|201|频段ID。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=GetFreqBandPlanGroup
&GroupId=201
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetFreqBandPlanGroupResponse>
      <Data>
            <BeginFrequency>923</BeginFrequency>
            <EndFrequency>925</EndFrequency>
            <FrequencyRegionId>CN</FrequencyRegionId>
            <GroupId>201</GroupId>
            <FrequencyType>SAME_FREQUENCY</FrequencyType>
      </Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</GetFreqBandPlanGroupResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":{
		"BeginFrequency":923,
		"FrequencyType":"SAME_FREQUENCY",
		"FrequencyRegionId":"CN",
		"GroupId":201,
		"EndFrequency":925
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

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


# GetGateway {#doc_api_LinkWAN_GetGateway .reference}

调用GetGateway获取网关信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=GetGateway&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetGateway|系统规定参数。取值：**GetGateway**。

 |
|GwEui|String|是|0000000000000000|网关唯一标识。

 |
|RegionId|String|是|cn-shanghai|地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |网关信息。

 |
|Address|String|详细地址|网关所在详细地址。

 |
|AddressCode|Long|123|网关所在地区ID，由http://lbs.amap.com/api/javascript-api/download定义。

 |
|City|String|某某市|网关所在城市名称。

 |
|ClassBSupported|Boolean|true|该网关是否支持Class B模式。

 |
|ClassBWorking|Boolean|true|该网关是否正工作在Class B模式下。

 |
|CommunicationMode|String|HALF\_DUPLEX|网关通信模式。可取值为：**FULL\_DUPLEX**\(全双工）、\*\*HALF\_DUPLEX\*\*\(半双工\)。

 |
|Description|String|网关描述|自定义网关描述。

 |
|District|String|某某区|网关所在城区名称。

 |
|Enabled|Boolean|true|该网关是否处于启用状态。

 |
|FreqBandPlanGroupId|Long|123|网关频段ID。

 |
|GisCoordinateSystem|String|GCJ\_02|网关经纬度所采用的坐标系统，可取值：**WGS\_84**, **GCJ\_02**。

 |
|GwEui|String|0000000000000000|网关唯一标识。

 |
|Latitude|Float|23.45678|网关纬度。

 |
|Longitude|Float|123.45678|网关经度。

 |
|Name|String|网关名称|自定义网关名称。

 |
|OnlineState|String|OFFLINE|网关在离线状态。可取值为**ONLINE**, **OFFLINE**。

 |
|OnlineStateChangedMillis|Long|1514736000000|最近一次在离线状态变更的时间。

 格式为UNIX时间戳，以毫秒为单位。

 |
|TimeCorrectable|Boolean|true|该网关是否可以作为时间校准网关。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=GetGateway
&GwEui=0000000000000000
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetGatewayResponse>
      <Data>
            <City>某某市</City>
            <Name>网关名称</Name>
            <District>某某区</District>
            <OnlineState>ONLINE</OnlineState>
            <TimeCorrectable>true</TimeCorrectable>
            <Enabled>true</Enabled>
            <Longitude>123.45678</Longitude>
            <Latitude>23.45678</Latitude>
            <OnlineStateChangedMillis>1514736000000</OnlineStateChangedMillis>
            <ClassBSupported>true</ClassBSupported>
            <Address>详细地址</Address>
            <GwEui>0000000000000000</GwEui>
            <CommunicateMode>HALF_DUPLEX</CommunicateMode>
            <ClassBWorking>true</ClassBWorking>
            <FreqBandPlanGroupId>123</FreqBandPlanGroupId>
            <AddressCode>123</AddressCode>
            <GisCoordinateSystem>GCJ-02</GisCoordinateSystem>
            <Description>网关描述</Description>
      </Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</GetGatewayResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":{
		"TimeCorrectable":true,
		"Enabled":true,
		"Description":"网关描述",
		"OnlineStateChangedMillis":1514736000000,
		"GisCoordinateSystem":"GCJ-02",
		"AddressCode":123,
		"ClassBSupported":true,
		"City":"某某市",
		"Name":"网关名称",
		"FreqBandPlanGroupId":123,
		"District":"某某区",
		"ClassBWorking":true,
		"Address":"详细地址",
		"Latitude":23.45678,
		"Longitude":123.45678,
		"OnlineState":"ONLINE",
		"CommunicateMode":"HALF_DUPLEX",
		"GwEui":"0000000000000000"
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


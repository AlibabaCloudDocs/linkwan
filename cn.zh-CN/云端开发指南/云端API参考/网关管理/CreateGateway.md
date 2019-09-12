# CreateGateway {#doc_api_LinkWAN_CreateGateway .reference}

调用CreateGateway录入网关。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=CreateGateway&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateGateway|系统规定参数。取值：**CreateGateway**。

 |
|Address|String|是|详细地址|网关所在详细地址。

 |
|AddressCode|Long|是|123|网关所在地区ID, 由http://lbs.amap.com/api/javascript-api/download定义。

 |
|City|String|是|杭州|网关所在城市名称。

 |
|CommunicationMode|String|是|HALF\_DUPLEX|网关通信模式。取值：**FULL\_DUPLEX**\(全双工）| \*\*HALF\_DUPLEX\*\*\(半双工\)。

 |
|District|String|是|滨江区|网关所在城区名称。

 |
|FreqBandPlanGroupId|Long|是|123|网关频段ID。

 |
|GisCoordinateSystem|String|是|GCJ-02|网关经纬度所采用的坐标系统，可取值为**WGS\_84**, **GCJ\_02**。

 |
|GwEui|String|是|0000000000000000|网关唯一标识。

 |
|Latitude|Float|是|23.45678|网关纬度。

 |
|Longitude|Float|是|123.45678|网关经度。

 |
|Name|String|是|vme|自定义网关名称。

 |
|PinCode|String|是|000000|网关PinCode, 用于确保录入者拥有该网关。

 |
|Description|String|否|my gateway|自定义网关描述信息。

 |
|RegionId|String|否|cn-hangzhou|地域ID。

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

http(s)://[Endpoint]/?Action=CreateGateway
&Address=详细地址
&AddressCode=123
&City=杭州
&CommunicationMode=HALF_DUPLEX
&District=滨江区
&FreqBandPlanGroupId=123
&GisCoordinateSystem=GCJ-02
&GwEui=0000000000000000
&Latitude=23.45678
&Longitude=123.45678
&Name=vme
&PinCode=000000
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateGatewayResponse>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</CreateGatewayResponse>
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
|400|GwEuiDuplicated|A gateway with the same gwEui already exists.|GwEUI 已存在|
|400|GatewayTupleAlreadyAbandoned|The specified gateway tuple has been abandoned.|网关元组已经废弃|
|400|IotHubTripleMissing|The IoT Platform trituple of this gateway does not exist.|找不到网关的物联网套件三元组|
|400|InvalidPinCode|An error occurred while verifying PinCode.|PinCode校验失败|
|400|GatewayAlreadyBoundToOthers|This gateway has already been bound to another account.|网关已经绑定到其它账号|
|400|ExceedGatewayLimit|The maximum number of gateways is exceeded.|超出网关可使用额度|
|400|InvalidFreqBandPlan|The frequency band plan is invalid.|频段计划不可用|
|400|InvalidName|The specified name is invalid.|名称不合法|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


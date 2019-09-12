# ListGateways {#doc_api_LinkWAN_ListGateways .reference}

调用ListGateways根据过滤条件查询当前用户账号名下的网关信息列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=ListGateways&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListGateways|系统规定参数。取值：**ListGateways**。

 |
|Limit|Long|是|2|本次查询的网关数量上限，大于等于1。

 |
|Offset|Long|是|0|本次查询的起始位置，从0开始。

 |
|Ascending|Boolean|否|true|配合**SortingField**参数一起使用，**true**表示升序，**false**表示降序。

 |
|FreqBandPlanGroupId|Long|否|123|网关频段ID过滤。

 |
|FuzzyCity|String|否|CityName|城市名模糊过滤。

 |
|FuzzyGwEui|String|否|123456|GwEUI模糊过滤。

 |
|FuzzyName|String|否|GatewayName|网关名称模糊过滤。

 |
|IsEnabled|Boolean|否|true|网关启停用状态过滤。

 如未传入此参数，则不限制启停状态。

 |
|OnlineState|String|否|ONLINE|网关在离线状态过滤。

 如未传入此参数，则不限制在线状态。可取值为：**ONLINE**, **OFFLINE**。

 |
|SortingField|String|否|ONLINE\_STATE\_CHANGED\_MILLIS|指定排序字段，可取值为**ONLINE\_STATE\_CHANGED\_MILLIS**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |返回的结果。

 |
|List| | |查询到的网关信息列表。

 |
|Address|String|详细地址|网关所在详细地址。

 |
|AddressCode|Long|123|网关所在地区ID，由http://lbs.amap.com/api/javascript-api/download定义。

 |
|City|String|某某市|网关所在城市名称。

 |
|ClassBSupported|Boolean|true|该网关是否支持 Class B 模式。

 |
|ClassBWorking|Boolean|true|该网关是否正工作在 Class B 模式下。

 |
|CommunicationMode|String|HALF\_DUPLEX|网关通信模式。可取值为**FULL\_DUPLEX**\(全双工）、\*\*HALF\_DUPLEX\*\*\(半双工\)。

 |
|Description|String|网关描述|自定义网关描述。

 |
|District|String|某某区|网关所在城区名称。

 |
|Enabled|Boolean|true|该网关是否处于启用状态。

 |
|FreqBandPlanGroupId|Long|123|网关频段ID。

 |
|GisCoordinateSystem|String|GCJ\_02|网关经纬度所采用的坐标系统，可取值为**WGS\_84**，**GCJ\_02**。

 |
|GwEui|String|0000000000000000|网关唯一标识。

 |
|Latitude|Float|23.45678|网关纬度。

 |
|Longitude|Float|123.45678|网关经度。

 |
|Name|String|网关名称|自定义网关名称。

 |
|OnlineState|String|ONLINE|网关在离线状态，可取值为：**ONLINE**，**OFFLINE**。

 |
|OnlineStateChangedMillis|Long|1514736000000|最近一次在离线状态变更的时间。

 格式为UNIX时间戳，以毫秒为单位。

 |
|TimeCorrectable|Boolean|true|该网关是否可以作为时间校准网关。

 |
|TotalCount|Long|2|满足过滤条件的网关总数。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=ListGateways
&Limit=2
&Offset=0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListGatewaysResponse>
      <Data>
            <TotalCount>23</TotalCount>
            <List>
                  <Gateway>
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
                  </Gateway>
                  <Gateway>
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
                  </Gateway>
            </List>
      </Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</ListGatewaysResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":{
		"TotalCount":23,
		"List":[
			{
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
			{
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
			}
		]
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

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


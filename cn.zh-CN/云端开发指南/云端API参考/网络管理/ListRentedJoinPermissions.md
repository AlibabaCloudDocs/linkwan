# ListRentedJoinPermissions {#doc_api_LinkWAN_ListRentedJoinPermissions .reference}

调用ListRentedJoinPermissions根据过滤条件，查询当前用户账号所租用的入网凭证列表（可能是专用入网凭证或泛在入网凭证）。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=ListRentedJoinPermissions&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRentedJoinPermissions|系统规定参数。取值：**ListRentedJoinPermissions**。

 |
|Limit|Long|是|2|本次查询的入网凭证数量的上限，大于等于 1。

 |
|Offset|Long|是|0|本次查询的起始位置，从 0 开始。

 |
|Ascending|Boolean|否|false|配合**SortingField**参数一起使用，**true**表示升序，**false**表示降序。

 |
|BoundNodeGroup|Boolean|否|true|根据入网凭证是否关联到节点分组进行过滤。**true**表示已关联，**false**表示未关联。

 |
|Enabled|Boolean|否|true|按照凭证的启停用状态进行过滤。**true**表示启用，**false**表示停用。

 |
|FuzzyJoinEui|String|否|d896e0|模糊匹配入网凭证使用的JoinEUI。

 |
|FuzzyJoinPermissionName|String|否|凭证1|模糊匹配入网凭证的名称。

 |
|FuzzyOwnerAliyunId|String|否|some-user|模糊匹配入网凭证拥有者的阿里云账号ID。

 |
|SortingField|String|否|CREATED\_MILLIS|指定排序字段，可取值为**CREATED\_MILLIS**, 表示根据创建时间排序。

 |
|Type|String|否|LOCAL|按照入网凭证的类型进行过滤，取值：

 -   **LOCAL**：专用凭证
-   **ROAMING**：泛在凭证

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data| | |返回的结果。

 |
|List| | |符合过滤条件的入网凭证列表。

 |
|BoundNodeGroup|Boolean|false|入网凭证是否已关联到节点分组。

 |
|ClassMode|String|A|入网凭证采用的LoRaWAN Class模式，可取值：**A**、**B**、**C**。

 |
|Enabled|Boolean|true|入网凭证的启停用状态。

 |
|FreqBandPlanGroupId|String|102|入网凭证采用的频段的频段ID。

 |
|JoinEui|String|0000000000000000|入网凭证使用的的JoinEUI。

 |
|JoinPermissionId|String|123|入网凭证ID。

 |
|JoinPermissionName|String|凭证1|入网凭证的名称。

 |
|OwnerAliyunId|String|some-user1|-   如果该入网凭证是**专用入网凭证**，该字段表示拥有者的阿里云账号ID。
-   如果该入网凭证是**泛在入网凭证**，该字段恒为**AliCloud IoT**。

 |
|Type|String|LOCAL|入网凭证的类型。

 |
|TotalCount|Long|10|符合过滤条件的入网凭证总数。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=ListRentedJoinPermissions
&Limit=2
&Offset=0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListRentedJoinPermissionsResponse>
      <Data>
            <TotalCount>10</TotalCount>
            <List>
                  <JoinPermission>
                        <JoinEui>0000000000000000</JoinEui>
                        <ClassMode>A</ClassMode>
                        <Enabled>true</Enabled>
                        <BoundNodeGroup>false</BoundNodeGroup>
                        <JoinPermissionId>123</JoinPermissionId>
                        <OwnerAliyunId>some-user1</OwnerAliyunId>
                        <Type>LOCAL</Type>
                        <JoinPermissionName>凭证1</JoinPermissionName>
                        <FreqBandPlanGroupId>102</FreqBandPlanGroupId>
                  </JoinPermission>
                  <JoinPermission>
                        <JoinEui>0000000000000001</JoinEui>
                        <ClassMode>A</ClassMode>
                        <Enabled>true</Enabled>
                        <BoundNodeGroup>false</BoundNodeGroup>
                        <JoinPermissionId>126</JoinPermissionId>
                        <OwnerAliyunId>some-user2</OwnerAliyunId>
                        <Type>ROAMING</Type>
                        <JoinPermissionName>凭证2</JoinPermissionName>
                        <FreqBandPlanGroupId>102</FreqBandPlanGroupId>
                  </JoinPermission>
            </List>
      </Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</ListRentedJoinPermissionsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Data":{
		"TotalCount":10,
		"List":[
			{
				"Enabled":true,
				"JoinPermissionId":"123",
				"FreqBandPlanGroupId":102,
				"BoundNodeGroup":false,
				"OwnerAliyunId":"some-user1",
				"Type":"LOCAL",
				"ClassMode":"A",
				"JoinEui":"0000000000000000",
				"JoinPermissionName":"凭证1"
			},
			{
				"Enabled":true,
				"JoinPermissionId":"126",
				"FreqBandPlanGroupId":102,
				"BoundNodeGroup":false,
				"OwnerAliyunId":"some-user2",
				"Type":"ROAMING",
				"ClassMode":"A",
				"JoinEui":"0000000000000001",
				"JoinPermissionName":"凭证2"
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
|400|CloudProductNotActivated|The Link WAN service has not been activated.|未开通 Link WAN 云产品|
|400|FeatureNotActivated|The feature has not been activated.|功能未开通|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


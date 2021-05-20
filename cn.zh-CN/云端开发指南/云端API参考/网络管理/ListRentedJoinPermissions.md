# ListRentedJoinPermissions

调用ListRentedJoinPermissions查询当前阿里云账号租用的入网凭证列表（专用凭证或泛在凭证）。

## 限制说明

-   如果在企业版实例中调用该接口，请求参数**IotInstanceId**必须填写。否则，调用接口会失败。
-   单阿里云账号调用该接口的每秒请求数（QPS）最大限制为5。

**说明：** RAM用户共享阿里云账号配额。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=ListRentedJoinPermissions&type=RPC&version=2019-03-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRentedJoinPermissions|系统规定参数。取值：**ListRentedJoinPermissions**。 |
|Limit|Long|是|2|本次查询的入网凭证数量。 |
|Offset|Long|是|0|本次查询的起始位置，从0开始。 |
|IotInstanceId|String|否|iot\_instc\_pu\*\*\*\*\_c\*-v64\*\*\*\*\*\*\*\*|实例ID。

 -   企业版实例：必须传入此参数。您可在物联网平台控制台的**实例概览**页面，查看您的企业版实例ID。
-   公共实例：无需传入此参数。 |
|FuzzyOwnerAliyunId|String|否|some-user|模糊匹配入网凭证拥有者的阿里云账号。 |
|FuzzyJoinEui|String|否|d896e0|模糊匹配入网凭证使用的JoinEUI。 |
|Enabled|Boolean|否|false|专用入网凭证的启停用状态。取值：

 -   **true**：启用。
-   **false**：停用。 |
|BoundNodeGroup|Boolean|否|false|入网凭证是否已关联到节点分组。取值：

 -   **true**：已关联。
-   **false**：未关联。 |
|Type|String|否|LOCAL|入网凭证的类型。取值：

 -   **LOCAL**：专用凭证。
-   **ROAMING**：泛在凭证。 |
|FuzzyJoinPermissionName|String|否|凭证1|模糊匹配入网凭证的名称。 |
|SortingField|String|否|CREATED\_MILLIS|指定排序字段，取值为**CREATED\_MILLIS**，表示根据创建时间排序。 |
|Ascending|Boolean|否|false|配合**SortingField**参数一起使用，指定字段排序方式。取值：

 -   **true**：升序。
-   **false**：降序。 |

调用API时，除了本文介绍的该API的特有请求参数，还需传入公共请求参数。公共请求参数说明，请参见[公共参数文档](~~108601~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |调用成功时返回的当前阿里云账号租用的入网凭证列表。 |
|List|Array of JoinPermission| |入网凭证列表。 |
|BoundNodeGroup|Boolean|false|入网凭证是否已关联到节点分组。返回值：

 -   **true**：已关联。
-   **false**：未关联。 |
|BoundNodeGroupId|String|123|入网凭证绑定的节点组ID。 |
|BoundNodeGroupName|String|123|入网凭证绑定的节点组名称。 |
|ClassMode|String|A|入网凭证采用的LoRaWAN Class模式。 |
|DataDispatchConfig|Struct| |节点分组的数据流转配置。 |
|Destination|String|IOT|数据流转目的地。返回值：

 -   **IOT**：数据流转到物联网平台的产品。
-   **ONS**：数据流转到MQ的Topic。 |
|IotProduct|Struct| |如果流转目的地是物联网平台的产品，该字段存储产品信息。 |
|DebugSwitch|Boolean|false|数据流转目的地为**IOT**的调试开关。返回值：

 -   **true**：打开调试开关。
-   **false**：关闭调试开关。 |
|ProductKey|String|a1fyXVF\*\*\*\*|产品的**ProductKey**。 |
|ProductName|String|test|产品名称。 |
|ProductType|String|IOT\_SUITE|产品类型。返回值：

 -   **IOT\_SUITE**：数据流转到IoT套件基础版。
-   **IOT\_SUITE\_SENIOR**：数据流转到IoT套件高级版。 |
|OnsTopics|Struct| |如果流转目的地是MQ，该字段存储MQ Topic信息。 |
|DownlinkRegionName|String|cn-beijing|MQ下行Region ID。 |
|DownlinkTopic|String|topic1|MQ下行Topic。 |
|UplinkRegionName|String|cn-shanghai|MQ上行Region ID。 |
|UplinkTopic|String|topic2|MQ上行Topic。 |
|DataRate|String|4|数据速率。 |
|Enabled|Boolean|true|入网凭证的启停用状态。返回值：

 -   **true**：启用。
-   **false**：停用。 |
|FreqBandPlanGroupId|String|102|入网凭证采用的频段ID。 |
|JoinEui|String|0000000000000000|入网凭证使用的JoinEUI。 |
|JoinPermissionId|String|123|入网凭证的ID。 |
|JoinPermissionName|String|凭证1|入网凭证的名称。 |
|OwnerAliyunId|String|some-user1|-   如果该入网凭证是**专用凭证**，该字段表示凭证拥有者的阿里云账号。
-   如果该入网凭证是**泛在凭证**，该字段值为**AliCloud IoT**。 |
|RxDelay|String|1|Class A的接收窗口延迟时间。 |
|Type|String|LOCAL|入网凭证的类型。返回值：

 -   **LOCAL**：专用凭证。
-   **ROAMING**：泛在凭证。 |
|TotalCount|Long|10|入网凭证总数。 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|阿里云为该请求生成的唯一标识符。 |
|Success|Boolean|true|是否调用成功。返回值：

 -   **true**：调用成功。
-   **false**：调用失败。 |

## 示例

请求示例

```
http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=ListRentedJoinPermissions
&Limit=2
&Offset=0
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
<Data>
    <TotalCount>10</TotalCount>
    <List>
        <BoundNodeGroupId>123</BoundNodeGroupId>
        <ClassMode>A</ClassMode>
        <Type>LOCAL</Type>
        <DataRate>4</DataRate>
        <OwnerAliyunId>some-user1</OwnerAliyunId>
        <BoundNodeGroup>false</BoundNodeGroup>
        <Enabled>true</Enabled>
        <JoinPermissionId>123</JoinPermissionId>
        <JoinPermissionName>凭证1</JoinPermissionName>
        <FreqBandPlanGroupId>102</FreqBandPlanGroupId>
        <JoinEui>0</JoinEui>
        <RxDelay>1</RxDelay>
        <BoundNodeGroupName>123</BoundNodeGroupName>
        <DataDispatchConfig>
            <Destination>IOT</Destination>
            <IotProduct>
                <DebugSwitch>false</DebugSwitch>
                <ProductName>test</ProductName>
                <ProductType>IOT_SUITE</ProductType>
                <ProductKey>a1fyXVF****</ProductKey>
            </IotProduct>
            <OnsTopics><OnsTopics/>
        </DataDispatchConfig>
    </List>
</Data>
<Success>true</Success>
```

`JSON`格式

```
{
    "RequestId": "89EF6CAA-958F-F32C-BE45-FE003C6DE097",
    "Data": {
        "TotalCount": 10,
        "List": {
            "BoundNodeGroupId": 123,
            "ClassMode": "A",
            "Type": "LOCAL",
            "DataRate": 4,
            "OwnerAliyunId": "some-user1",
            "BoundNodeGroup": false,
            "Enabled": true,
            "JoinPermissionId": 123,
            "JoinPermissionName": "凭证1",
            "FreqBandPlanGroupId": 102,
            "JoinEui": 0,
            "RxDelay": 1,
            "BoundNodeGroupName": 123,
            "DataDispatchConfig": {
                "Destination": "IOT",
                "IotProduct": {
                    "DebugSwitch": false,
                    "ProductName": "test",
                    "ProductType": "IOT_SUITE",
                    "ProductKey": "a1fyXVF****"
                },
                "OnsTopics": {}
            }
        }
    },
    "Success": true
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ForbiddenByRam|User not authorized to operate on the specified resource, or this API does not support RAM.|用户没有执行该操作所需要的RAM权限。|
|400|ForbiddenByRiskControl|This operation cannot be performed because of security risks.|存在安全风险，无法执行该操作|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|CloudProductNotActivated|The Link WAN service has not been activated.|未开通 Link WAN 云产品|
|400|FeatureNotActivated|The feature has not been activated.|功能未开通|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


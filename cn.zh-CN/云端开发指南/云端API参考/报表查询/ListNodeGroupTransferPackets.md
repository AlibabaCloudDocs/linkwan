# ListNodeGroupTransferPackets

调用ListNodeGroupTransferPackets获取节点分组上下行数据包的统计信息。

## 限制说明

-   如果在企业版实例中调用该接口，请求参数**IotInstanceId**必须填写。否则，调用接口会失败。
-   单阿里云账号调用该接口的每秒请求数（QPS）最大限制为5。

**说明：** RAM用户共享阿里云账号配额。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=ListNodeGroupTransferPackets&type=RPC&version=2019-03-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListNodeGroupTransferPackets|系统规定参数。取值：**ListNodeGroupTransferPackets**。 |
|BeginMillis|Long|是|1514736000000|查询开始时间，格式为毫秒级的13位时间戳。 |
|Category|String|是|UPLINK\_PACKET|数据包分类。取值：

 -   **DOWNLINK\_PACKET**：下行包。
-   **UPLINK\_PACKET**：上行包。 |
|EndMillis|Long|是|1514736000000|查询结束时间，格式为毫秒级的13位时间戳。 |
|NodeGroupId|String|是|123|节点分组ID，可调用[ListNodeGroups](~~109944~~)接口查询获取。 |
|PageNumber|Integer|是|1|指定从返回结果中的第几页开始显示。 |
|PageSize|Integer|是|2|返回结果中每页显示的记录数。 |
|IotInstanceId|String|否|iot-cn-0pp1n8t\*\*\*\*|实例ID。

 -   企业版实例：必须传入此参数。您可在物联网平台控制台的**实例概览**页面，查看您的企业版实例ID。
-   公共实例：无需传入此参数。 |
|DevEui|String|否|0000000000000001|根据DevEUI过滤数据包。 |
|SortingField|String|否|LOG\_MILLIS|排序字段，取值：**LOG\_MILLIS**，表示按照时间排序。 |
|Ascending|Boolean|否|true|配合**SortingField**参数一起使用，指定字段排序方式。取值：

 -   **true**：升序。
-   **false**：降序。 |

调用API时，除了本文介绍的该API的特有请求参数，还需传入公共请求参数。公共请求参数说明，请参见[公共参数文档](~~108601~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Struct| |调用成功时返回的节点分组上下行数据包的统计信息。 |
|List|Array of Packet| |节点分组上下行数据包的统计信息列表。 |
|Base64EncodedMacPayload|String|XXX|Base64编码后的MACPayload报文。 |
|ClassMode|String|C|收发此数据包时的LoRaWAN Class模式。 |
|Datr|String|SF12BW125|收发此数据包的数据速率。 |
|DevAddr|String|00000000|收发此数据包的节点的网络地址。 |
|DevEui|String|0000000000000001|收发此数据包的节点的DevEUI。 |
|FPort|Integer|99|收发此数据包时所使用的FPort。 |
|FcntDown|Long|1111|下行帧计数。 |
|FcntUp|Long|1123|上行帧计数。 |
|Freq|Float|470.3|收发此数据包的频点。 |
|FreqBandPlanGroupId|Long|101|数据包所经过的网关所采用的频段ID。 |
|GwEui|String|0000000000000000|收发此数据包所经过的网关的GwEUI。 |
|GwOwnerAliyunId|String|XXX|数据包所经过网关所属用户的阿里云账号。 |
|HasData|Boolean|true|此数据包中是否包含业务数据。返回值：

 -   **true**：包含。
-   **false**：不包含。 |
|HasMacCommand|Boolean|true|此数据包中是否包含MAC指令。返回值：

 -   **true**：包含。
-   **false**：不包含。 |
|LogMillis|Long|1514736000000|数据包传输的UNIX时间戳，以毫秒为单位。 |
|Lsnr|Float|-10.5|收发此数据包的信噪比。 |
|MacCommandCIDs|String|\["0x01","0x02"\]|数据包所携带的MAC指令列表。 |
|MacPayloadSize|Long|15|此数据包的MACPayload报文长度。 |
|MessageType|String|CONFIRMED\_DATA\_UP|消息类型。返回值：

 -   **JOIN\_REQUEST**：Join-request消息。
-   **JOIN\_ACCEPT**：Join-accept消息。
-   **UNCONFIRMED\_UP**：Unconfirmed上行消息。
-   **UNCONFIRMED\_DOWN**：Unconfirmed下行消息。
-   **CONFIRMED\_UP**：Confirmed上行消息。
-   **CONFIRMED\_DOWN**：Confirmed下行消息。
-   **REJOIN\_REQUEST**：Rejoin-request消息。
-   **PROPRIETARY**：Proprietary消息（私有消息）。 |
|ProcessEvent|String|DEVADDR\_ILLEGAL|该报文的处理结果。返回值：

 -   **SUCCESS**：成功。
-   **DEVADDR\_ILLEGAL**：**DevAddr**不合法。
-   **MIC\_FAIL**：MIC校验失败。
-   **DEVEUI\_ILLEGAL**：**DevEui**不合法。
-   **JOINEUI\_ILLEGAL**：**JoinEui**不合法。
-   **STATUS\_INVALID**：节点状态不合法。
-   **REDUPLICATE**：重复包。
-   **ISOLATED**：网间隔离。
-   **APPKEY\_ILLEGAL**：**AppKey**不合法。
-   **UPDATE\_RUNTIME\_CFG\_FAIL**：更新运行时配置失败。
-   **DELAY\_PROCESS**：延迟处理。
-   **GWEUI\_ILLEGAL GwEui**：不合法。
-   **GW\_STATUS\_INVALID**：网关状态不合法。
-   **GW\_FREQ\_NOT\_MATCH**：网关频点不匹配。
-   **其它**：未知错误。 |
|Rssi|Integer|-110|收发此数据包的RSSI。 |
|TotalCount|Long|20|满足过滤条件的数据包总数。 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|阿里云为该请求生成的唯一标识符。 |
|Success|Boolean|true|是否调用成功。返回值：

 -   **true**：调用成功。
-   **false**：调用失败。 |

## 示例

请求示例

```
http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=ListNodeGroupTransferPackets
&BeginMillis=1514736000000
&Category=UPLINK_PACKET
&EndMillis=1514736000000
&NodeGroupId=123
&PageNumber=1
&PageSize=2
&SortingField=LOG_MILLIS
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
<Data>
    <TotalCount>20</TotalCount>
    <List>
        <ClassMode>C</ClassMode>
        <FcntUp>1123</FcntUp>
        <Base64EncodedMacPayload>XXX</Base64EncodedMacPayload>
        <ProcessEvent>DEVADDR_ILLEGAL</ProcessEvent>
        <MacCommandCIDs>["0x01","0x02"]</MacCommandCIDs>
        <FPort>99</FPort>
        <HasMacCommand>true</HasMacCommand>
        <DevEui>0000000000000001</DevEui>
        <Lsnr>-10.5</Lsnr>
        <Rssi>-110</Rssi>
        <MacPayloadSize>15</MacPayloadSize>
        <FcntDown>1111</FcntDown>
        <GwEui>0000000000000000</GwEui>
        <Freq>470.3</Freq>
        <DevAddr>00000000</DevAddr>
        <GwOwnerAliyunId>XXX</GwOwnerAliyunId>
        <Datr>SF12BW125</Datr>
        <MessageType>CONFIRMED_DATA_UP</MessageType>
        <LogMillis>1514736000000</LogMillis>
        <FreqBandPlanGroupId>101</FreqBandPlanGroupId>
        <HasData>true</HasData>
    </List>
</Data>
<Success>true</Success>
```

`JSON`格式

```
{
    "RequestId": "89EF6CAA-958F-F32C-BE45-FE003C6DE097",
    "Data": {
        "TotalCount": 20,
        "List": {
            "ClassMode": "C",
            "FcntUp": 1123,
            "Base64EncodedMacPayload": "XXX",
            "ProcessEvent": "DEVADDR_ILLEGAL",
            "MacCommandCIDs": "[\"0x01\",\"0x02\"]",
            "FPort": 99,
            "HasMacCommand": true,
            "DevEui": 1,
            "Lsnr": -10.5,
            "Rssi": -110,
            "MacPayloadSize": 15,
            "FcntDown": 1111,
            "GwEui": 0,
            "Freq": 470.3,
            "DevAddr": 0,
            "GwOwnerAliyunId": "XXX",
            "Datr": "SF12BW125",
            "MessageType": "CONFIRMED_DATA_UP",
            "LogMillis": 1514736000000,
            "FreqBandPlanGroupId": 101,
            "HasData": true
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
|400|NonExistent|The specified resource does not exist.|要操作的资源不存在。|
|400|InternalError|The request processing has failed due to some unknown error, exception or failure.|内部错误。|
|400|CloudProductNotActivated|The Link WAN service has not been activated.|未开通 Link WAN 云产品|
|400|FeatureNotActivated|The feature has not been activated.|功能未开通|
|400|NotResourceOwner|You are not authorized to use this resource.|无权访问此资源|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


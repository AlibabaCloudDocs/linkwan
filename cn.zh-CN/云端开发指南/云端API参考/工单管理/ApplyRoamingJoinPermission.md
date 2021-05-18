# ApplyRoamingJoinPermission

调用ApplyRoamingJoinPermission申请泛在凭证。

## 限制说明

-   单阿里云账号的泛在凭证数量为一个。
-   单阿里云账号调用该接口的每秒请求数（QPS）最大限制为5。

**说明：** RAM用户共享阿里云账号配额。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=ApplyRoamingJoinPermission&type=RPC&version=2019-03-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ApplyRoamingJoinPermission|系统规定参数。取值：**ApplyRoamingJoinPermission**。 |
|ClassMode|String|是|A|泛在凭证所采用的LoRaWAN Class模式。取值：A、B、C。 |
|FreqBandPlanGroupId|Long|是|102|泛在凭证所采用的频段ID。取值：

 -   **102**：CN470异频。
-   **101**：CN470同频。
-   **201**：AS923同频。 |
|JoinPermissionName|String|是|泛在凭证1|泛在凭证名称，支持中文、英文字母、数字和下划线（\_），长度限制4～30个字符，一个中文占两个字符。 |
|RxDelay|Long|否|1|Class A的接收窗口延迟时间，取值范围1s~15s。 |
|DataRate|Long|否|4|当**ClassMode**取值为**B**时，设置期望下行速率，取值范围0~5。 |

调用API时，除了本文介绍的该API的特有请求参数，还需传入公共请求参数。公共请求参数说明，请参见[公共参数文档](~~108601~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|String|1234|泛在凭证的ID。 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|阿里云为该请求生成的唯一标识符。 |
|Success|Boolean|true|是否调用成功。返回值：

 -   **true**：调用成功。
-   **false**：调用失败。 |

## 示例

请求示例

```
http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=ApplyRoamingJoinPermission
&ClassMode=A
&FreqBandPlanGroupId=102
&JoinPermissionName=泛在凭证1
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
<Success>true</Success>
<Data>123</Data>
```

`JSON`格式

```
{
    "RequestId": "89EF6CAA-958F-F32C-BE45-FE003C6DE097",
    "Success": true,
    "Data": "123"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ForbiddenByRam|User not authorized to operate on the specified resource, or this API does not support RAM.|用户没有执行该操作所需要的RAM权限。|
|400|ForbiddenByRiskControl|This operation cannot be performed because of security risks.|存在安全风险，无法执行该操作|
|400|NonExistent|The specified resource does not exist.|要操作的资源不存在。|
|400|ExceedRoamingJoinPermissionLimit|The maximum number of roaming join permissions is exceeded.|超出漫游凭证系统限额|
|400|JoinPermissionNameDuplicated|The specified join permission name already exists.|入网凭证名称重复|
|400|InvalidName|The specified name is invalid.|名称不合法|
|400|InvalidFreqBandPlan|The frequency band plan is invalid.|频段计划不可用|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


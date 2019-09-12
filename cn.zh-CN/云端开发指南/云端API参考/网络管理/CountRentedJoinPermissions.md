# CountRentedJoinPermissions {#doc_api_LinkWAN_CountRentedJoinPermissions .reference}

调用CountRentedJoinPermissions统计当前用户账号所租用的且符合过滤条件的入网凭证数量。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=CountRentedJoinPermissions&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CountRentedJoinPermissions|系统规定参数。取值：**CountRentedJoinPermissions**。

 |
|BoundNodeGroup|Boolean|否|true|根据入网凭证是否关联到节点分组进行过滤。

 **true**表示已关联，**false**表示未关联。

 |
|Enabled|Boolean|否|true|按照凭证的启停用状态进行过滤。

 |
|FuzzyJoinEui|String|否|d896e0|模糊匹配入网凭证的JoinEUI。

 |
|FuzzyJoinPermissionName|String|否|test|模糊匹配入网凭证的名称。

 |
|FuzzyOwnerAliyunId|String|否|some-user|模糊匹配入网凭证拥有者的阿里云账号ID。

 |
|Type|String|否|LOCAL|按照凭证的类型进行过滤。取值：

 -   **LOCAL**：专用凭证
-   **ROAMING**：泛在凭证

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Data|Long|100|满足过滤条件的入网凭证总数。

 |
|RequestId|String|89EF6CAA-958F-F32C-BE45-FE003C6DE097|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=CountRentedJoinPermissions
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CountRentedJoinPermissionsResponse>
      <Data>100</Data>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</CountRentedJoinPermissionsResponse>
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


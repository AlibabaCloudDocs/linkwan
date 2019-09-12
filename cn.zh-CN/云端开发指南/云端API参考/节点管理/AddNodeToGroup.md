# AddNodeToGroup {#doc_api_LinkWAN_AddNodeToGroup .reference}

调用AddNodeToGroup在节点分组中增加新的节点。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=LinkWAN&api=AddNodeToGroup&type=RPC&version=2018-12-30)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddNodeToGroup|系统规定参数。取值：**AddNodeToGroup**。

 |
|DevEui|String|是|0000000000000000|节点的DevEUI。

 |
|NodeGroupId|String|是|123|节点分组ID。

 |
|PinCode|String|是|123456|节点的PIN Code。

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

http(s)://linkwan.cn-shanghai.aliyuncs.com/?Action=AddNodeToGroup
&DevEui=0000000000000000
&NodeGroupId=123
&PinCode=123456
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddNodeToGroupResponse>
      <RequestId>89EF6CAA-958F-F32C-BE45-FE003C6DE097</RequestId>
      <Success>true</Success>
</AddNodeToGroupResponse>
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
|400|NonExistent|The specified resource does not exist.|要操作的资源不存在。|
|400|ExceedNodeLimit|The maximum number of nodes is exceeded.|超出节点可使用额度|
|400|NodeGroupDoesNotExist|The specified node group does not exist.|节点组不存在|
|400|DevEuiDuplicated|A node with the same devEui already exists.|节点重复添加|
|400|NodeAlreadyAdded|The specified node has already been added to another node group.|节点已经添加到其他分组|
|400|InvalidPinCode|An error occurred while verifying PinCode.|PinCode校验失败|
|400|ResourceLocked|The specified resource has been locked by another product.|资源被其他云产品锁定|
|400|NodeDoesNotExist|The specified node does not exist.|节点不存在|

访问[错误中心](https://error-center.aliyun.com/status/product/LinkWAN)查看更多错误码。


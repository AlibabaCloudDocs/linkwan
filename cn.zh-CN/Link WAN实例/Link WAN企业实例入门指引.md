Link WAN企业实例入门指引 
=====================================



本文档介绍用户在购买Link WAN企业实例后，如何快速搭建企业专用Link WAN网络。

背景信息 
-------------------------

网关获取方式有如下两种方法：

* 移植阿里云Link WAN网关SDK，移植教学可参考[网关SDK](/cn.zh-CN/硬件伙伴指南/获取SDK/网关SDK.md)，版本需选择阿里云Link WAN网关SDK 2.5.0及以上版本，并且[购买Link WAN密钥](https://linkwan.console.aliyun.com/security-tuple-management)，安装后使用。

  




<!-- -->

* 浏览[阿里云IoT技术认证查询](https://iot.aliyun.com/linkcertification)，选择推荐的网关硬件，版本需适配阿里云Link WAN网关SDK 2.5.0及以上版本。

  






节点模组获取方式也有如下两种方法：

* 移植阿里云Link WAN节点SDK，移植教学可参考[节点SDK](/cn.zh-CN/硬件伙伴指南/获取SDK/节点SDK.md)，用户可[购买Link WAN密钥](https://linkwan.console.aliyun.com/security-tuple-management)，也可自定义颁发密钥，安装后使用。

  




<!-- -->

* 浏览[阿里云IoT技术认证查询](https://iot.aliyun.com/linkcertification)，选择推荐的节点硬件。

  






如购买已安装密钥的设备，收到货品时，请检查是否有以下信息。

* 网关设备信息：GwEUI、 PIN Code

  

* 节点设备信息：DevEUI、PIN Code/DevEUI、JoinEUI、AppKEY

  




进入企业实例 
---------------------------

1. 登录[物联网平台](https://iot.console.aliyun.com)。

   

2. 在左侧导航栏上，选择实例管理 \> 切换Link WAN企业实例。

   




![进入企业实例](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p148395.png)

3、进入企业实例

![企业实例界面](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p148396.png)

添加网关 
-------------------------

1、在左侧引导栏上，选择 **Link WAN \> 网关管理** 。

2、在 **网关列表** 页签，单击 **添加网关** 。

![添加网关](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p148397.png)

3、配置信息以激活网关，如下图所示。

![网关详情页](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p148404.png)


|    参数    |                                                                                                    说明                                                                                                     |
|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 基本信息                                                                                                                                                                                                                ||
| 名称       | 填写添加的网关名称，支持中文、英文字母、数字和下划线，长度限制4～30，中文算两位。                                                                                                                                                                |
| PIN Code | Pin Code为6位数字，通常会贴在网关标签上。                                                                                                                                                                                 |
| 通信模式     | 通信模式分为全双工和半双工两种，此处以选择半双工为例。                                                                                                                                                                               |
| GwEUI    | 请在网关标签上查看该参数                                                                                                                                                                                              |
| 频段       | 支持以下三种频段的选择： * CN470 同频   * CN470 异频   * AS923 同频    此处以选择CN470 异频为例。 |
| 网关描述     | 选填，可以填写所添加网关的备注信息。网关描述不多于100字。                                                                                                                                                                            |
| 位置信息                                                                                                                                                                                                                ||
| 所在区域     | 请选择网关的所在区域。                                                                                                                                                                                               |
| 位置详情     | 填写网关的具体的位置信息，您也可于右侧地图单击做定位。                                                                                                                                                                               |



4、完成网关添加后上电网关，确保设备连通互联网（可通过4G或者以太网等方式）。

您可以在网关管理页查看该网关的状态。显示在线表示网关已开始服务，可以开始管理网络，如下图所示。

![网关添加成功](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p161117.png)

添加入网凭证 
---------------------------

1、在左侧引导栏上，选择 **Link WAN \> 入网凭证** 。

2、在 **入网凭证** 页面，单击 **添加入网凭证** ，如下图所示。

![添加入网凭证指引](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p160962.png)

3、在下图中配置参数，配置完成后单击确认即可创建一个凭证。

![添加入网凭证](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p160964.png)


|   参数    |                                                                                                          说明                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| JoinEUI | 应用EUI，16位HEX，默认为d896e0efff000000，用户可修改。                                                                                                                                                                               |
| 凭证名称    | 填写添加的凭证的名称，支持中文、英文字母、数字和下划线，长度限制4～30，中文算两位。                                                                                                                                                                           |
| 频段      | 支持以下三种频段的选择： * CN470 同频   * CN470 异频   * AS923 同频    此处以选择CN470 异频为例。             |
| Class   | 支持以下三种类的选择： * A   * B   * C   * D2D    此处以选择A为例。 |
| RxDelay | 选择Class A可配置 RXDelay，用于配置上行后的接收窗口延迟时间，默认1s，可选范围在1s\~15s。                                                                                                                                                              |



4、创建完成后，可前往创建产品。

![前往创建产品](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5651749951/p148418.png)

创建产品 
-------------------------

1、在左侧引导栏上，选择 **设备管理 \> 产品** 。

2、在 **产品** 子页面，点击 **创建产品** 。

![创建产品引导](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p148419.png)

3、在下图中配置参数，配置完成后单击确认即可创建一个产品。

![创建产品](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p161118.png)


|  参数  |         说明          |
|------|---------------------|
| 产品名称 | 测试--温湿度（用户自定义）      |
| 所属品类 | 选择 **自定义品类**        |
| 节点类型 | 选择 **直连设备**         |
| 连网方式 | 选择 **LoRaWAN**      |
| 入网凭证 | 从清单里选择，或单击 **创建凭证** |
| 数据格式 | 选择 **透传/自定义**       |
| 认证方式 | 选择 **设备密钥**         |





4、创建成功后，可前往创建物模型或者添加设备。

![前往创建物模型/添加设备](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p148421.png)

5、添加物模型（产品功能定义）

1）在左侧导航栏上选择设备管理 \> 产品，单击产品对应操作栏中的查看。

2）选择功能定义 \> 编辑草稿。

![编辑物模型](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p160977.png)

3）可以通过添加属性、事件、服务三类功能完成产品物模型的定位，支持单个添加和批量添加物模型，导入产品下的设备都会集成该模型，具体参考可参考[物模型](https://help.aliyun.com/document_detail/73727.html) **。** 

![物模型1](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6943844061/p179334.png)

6、数据解析脚本

LoRaWAN设备与物联网平台的通信数据格式为透传/自定义，因此需要使用数据解析脚本，解析上下行数据。可参考[LoRaWAN设备数据解析](https://help.aliyun.com/document_detail/120032.html)。

添加设备 
-------------------------

1、在左侧引导栏上，选择 **设备管理 \> 设备** 。

2、在设备子页面，点击 **添加设备** 。

![添加设备引导](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p148426.png)

3、在下图中填写参数，填写完成后单击确认即可添加一个设备。

i. 阿里云颁发导入

![阿里云颁发](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p161124.png)

ii. 用户自定义导入

![自定义导入](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p161125.png)


|    参数    |                说明                |
|----------|----------------------------------|
| 产品       | 选择对应产品                           |
| 颁发归属     | 密钥颁发归属，分为 **阿里云颁发** 和 **用户自定义**  |
| Deveui   | 设备唯一ID，为16位HEX，小写                |
| PIN Code | 6位十进制数字（ **阿里云颁发** 的参数）          |
| JoinEUI  | 应用EUI，为16位HEX（ **用户自定义** 的参数），小写 |
| AppKEY   | 密钥EUI，为32位HEX（ **用户自定义** 的参数），小写 |



\*批量添加当前版本暂不支持

查看上下行数据 
----------------------------

1、添加成功后，可前往 **Link WAN** **\> 节点分组** **\> 查看/节点** 

![查看节点](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p161126.png)

2、选择 **节点** **\>** **查看** ，可以查询设备三要素信息。若为自定义密钥，允许用户编辑，编辑后，需将新的三要素烧入到设备中，并重新触发Join入网，成功后才能正常通信。

![查看密钥](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6651749951/p161230.png)

3、查看LoRaWAN链路层数据通信上下行

![上下行数据](//static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7651749951/p161235.png)

规则引擎 
-------------------------

企业实例中的Link WAN数据流转采用物联网平台的[规则引擎](https://help.aliyun.com/document_detail/146382.html?spm=a2c4g.11186623.6.616.341831b4VbhkxU)。

物联网平台规则引擎包含以下功能：

* 服务端订阅：订阅某产品下所有设备的某个或多个类型消息，您的服务端可以通过AMQP客户端或消息服务（MNS）客户端获取订阅的消息。

  

* 云产品流转：物联网平台根据您配置的数据流转规则，将指定Topic消息的指定字段流转到目的地，进行存储和计算处理。

  




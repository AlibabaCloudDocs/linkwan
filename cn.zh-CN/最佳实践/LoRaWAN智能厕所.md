# LoRaWAN智能厕所

本实践推荐使用阿里云物联网平台一站式完成应用开发，物联网平台可直接调用Link WAN网管服务。

-   应用概述

    为了增加厕所使用效率，减少被味道“熏陶”的等待时间，同时也为了增加厕所的清洁效率，可以做一个非侵入式的智能厕所改造方案。通过红外热释电检测每个坑位有没有人，在web/app上实时显示，方便如厕人员查询。并且可以检测厕所的臭味，达到阈值时通知清洁工进行清扫。

    本文中将使用[物联网平台](https://www.aliyun.com/product/iot-deviceconnect)搭建了一个基于LoRaWAN连接的智能厕所demo。

-   物料清单
    -   慧联无限G200 LoRaWAN网关
    -   慧联无限LoRa红外传感器
    -   一台能联网的电脑

## 配置LoRaWAN网关-自建LoRaWAN网络

1.  选择从[阿里云IoT市场](https://linkmarket.aliyun.com/tms/lora?spm=a2c4g.11186623.2.13.3fb41076LKJpUD)上购买网关并自己组成网络。

    以下是本实践使用的网关

    ![小网关G200](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8488509951/p84052.png)

    ![小网关G200_1](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8488509951/p84054.png)

2.  插上网线与电源，登录[物联网络管理平台控制台](https://linkwan.console.aliyun.com/)注册网关。

    1.  在左侧导航栏上，选择**网络管理** \> **网关管理**。

    2.  在**网关列表**页签，单击**添加网关**。

        ![添加网关](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8488509951/p81990.png)

    3.  配置信息以激活网关，如下图所示。

        ![配置网关信息](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8488509951/p81996.png)

        |参数|说明|
        |--|--|
        |基本信息|
        |名称|填写添加的网关名称，支持中文、英文字母、数字和下划线，长度限制4～30，中文算两位。|
        |PIN Code|Pin Code为6位数字，通常会贴在网关标签上。|
        |通信模式|通信模式分为**全双工**和**半双工**两种，此处以选择**半双工**为例。|
        |GwEUI|请在网关标签上查看该参数。|
        |频段|支持以下三种频段的选择：         -   CN470 同频
        -   CN470 异频
        -   AS923 同频
 此处以选择**CN470 异频**为例。 |
        |网关描述|选填，可以填写所添加网关的备注信息。网关描述不多于100字符。|
        |位置信息 **说明：** 这里需要手动选择网关位置，因G200不带GPS模块，需要手动填写，之后会显示在地图上。带GPS网关的，上报数据后会自动刷新位置。 |
        |所在区域|请选择网关的所在区域。|
        |位置详情|填写网关的具体的位置信息，您也可于右侧地图单击做定位。|

    G200回传网默认是DHCP上网配置，如果您是固定IP或PPPoE，需依照实际环境调整，相关操作请参考G200网关手册。配置成功后可以在**网关列表**下显示**在线**状态。

    ![网关在线状态_智能厕所](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p84076.png)

3.  创建自己的网络凭证，然后把网络分配给自己账号使用。分配后透过入网凭证来取得网络使用权利。

    1.  在左侧导航栏上，选择**网络管理** \> **入网开通**。

    2.  在**入网开通**页面，单击**添加专用凭证**，如下图所示。

        ![添加专用凭证](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p82241.png)

    3.  在下图中配置参数，配置完成后单击**确认**即可创建一个凭证。

        ![配置凭证参数](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p82254.png)

        |参数|说明|
        |--|--|
        |凭证名称|填写添加的凭证的名称，支持中文、英文字母、数字和下划线，长度限制4～30，中文算两位。|
        |频段|支持以下三种频段的选择：         -   CN470 同频
        -   CN470 异频
        -   AS923 同频
 此处以选择**CN470 异频**为例。 |
        |Class|支持以下三种类的选择：         -   A
        -   B
        -   C
 此处以选择**A**为例，按需发送。 |
        |RxDelay|选择Class A可配置 RXDelay，用于配置上行后的接收窗口延迟时间，默认1s，可选范围在1s~15s。|

    4.  单击该凭证**操作**所在列的**凭证授权**，将添加好的凭证授权给自己，如下图所示。

        ![将凭证授权给自己](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p82262.png)

    授权成功之后，新凭证会在出现在**凭证清单**里，如果是别人将凭证授权给您，接受后也会在此清单显示。

    ![查看凭证清单](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p82268.png)


## 拆封LoRaWAN硬件

从网上购买来的认证过的LoRa传感器，拆出来的时候可以看到后面附了一个16位码的贴纸，这个是节点的DevEUI。同时还会有一个6位的PINCODE字段。

按照说明书，默认是5分钟模式，即收到一次警报之后，5分钟之内收到的警报不会再上传。这跟厕所的使用场景不一致，我们需要调成测试模式，即每次收到的警报都会上传。

操作方法：把背部的壳子掰开（不需要螺丝刀）后，调整跳针针帽位置到ON，然后合上盖子，先不拔掉塑料片。

## 在物联网平台上配置LoRa节点

1.  登录[物联网平台控制台](https://iot.console.aliyun.com/)

2.  在左侧导航栏上选择**设备管理** \> **产品**，单击**创建产品**

    ![单击创建产品](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p83853.png)

3.  填写产品信息，然后单击**保存**。

    ![创建LoRa设备的产品](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p83388.png)

    |参数|说明|
    |--|--|
    |产品名称|智能咖啡机（可自定义）|
    |所属品类|选择**自定义品类**|
    |节点类型|选择**直连设备**|
    |连网方式|选择**LoRaWAN**|
    |入网凭证|从清单里选择，或单击**添加专用凭证** **说明：** 请确认已经在Link WAN取得入网凭证。 |
    |数据格式|透传/自定义|
    |产品描述|非必填，用于描述产品的相关信息。|

    如首次使用Link WAN需授权数据权限。

    ![首次授权](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p83873.png)

4.  创建完毕后，单击**管理设备**前往管理。

    ![管理设备](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p83880.png)

5.  单击**添加设备**，即可完成LoRa设备接入。

    ![添加设备](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p83883.png)

6.  输入16位DevEUI作为DeviceName（需小写）。

    ![输入DevEUI](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9488509951/p84123.png)


## 查看上下行数据及数据日志

1.  回到[物联网络管理平台控制台](https://linkwan.console.aliyun.com/?spm=a2c4g.11186623.2.32.3fb41076LKJpUD)，可以查看LoRaWAN链路层数据通信上下行。

    1.  在左侧导航栏上选择**节点管理** \> **节点分组**。

        ![节点分组状态显示](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p83910.png)

        **说明：** 此节点已授权给物联网平台接入使用，这里只提供查看功能。

    2.  单击该节点对应**操作**栏下的**查看**，选择**上行数据**页签，查看上行数据。

        ![查看上行数据](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84153.png)

2.  拔掉LoRa传感器上的塑料片，让传感器上电。

3.  查看物联网平台上收到的上行日志。

    在[物联网平台控制台](https://iot.console.aliyun.com/)左侧导航栏上选择**监控运维** \> **日志服务**，在**上行消息分析**页签查看到如下日志。

    ![上行消息分析](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84164.png)

    此时设备也收到了数据日志，即表示所有通讯链路都打通，下图为原始的上行日志。

    ![原始上行日志](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84167.png)


## 解析设备上传的信息

从传感器的说明文件可以得知，传感器上报的是二进制数据。我们如何把二进制数据转化为可以理解的属性名称呢？具体请看下文的操作步骤。

下图是厂家提供的传感器的二进制配置文件

![传感器二进制配置信息](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84173.png)

1.  定义物模型。

    对于该型号的传感器，`020100`中的第一个BYTE`02`表示协议，`01`对红外传感器表示有人，`00`表示传感器状态正常。我们首先需要在产品里定义**室内人体探测开关**和**传感器属性**两个功能，用于记录这两个属性。

    1.  在[物联网平台控制台](https://iot.console.aliyun.com/)左侧导航栏上选择**设备管理** \> **产品**，单击产品对应的**查看**，进入产品详情页。

    2.  选择**功能定义**页签，单击**编辑草稿** \> **添加自定义功能**。

    3.  在添加自定义功能弹框中，**功能类型**选择**属性**，添加以下两个属性。

        -   添加**传感器属性**

            ![传感器属性](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84187.png)

        -   添加**室内人体探测开关**

            ![室内人体探测开关](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84191.png)

        属性添加完成后，如下图所示。

        ![两个属性参数配置](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84200.png)

        **说明：** 读写类型都选择读写。

2.  使用产品定义里的数据解析，把二进制数据自动转化为Alink-JSON格式，以应对[定义物模型](#step_bfs_6m2_m0p)中的两个属性。

    **说明：**

    -   转化规则可以[参考文档](https://help.aliyun.com/document_detail/68702.html?spm=a2c4g.11186623.2.42.3fb41076LKJpUD)，这里只提供最后的代码。
    -   数据解析需要产品为**未发布**状态。如果已经发布请单击右上角**撤回发布**。
    1.  在**产品详情**页，单击**数据解析**页签。

        ![数据解析页签](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84218.png)

    2.  在**编辑脚本**下方，输入如下的解析脚本，然后单击页面下方的**保存**。

        ```
        var COMMAND_REPORT = 02;
        var COMMAND_SET = 01;
        var ALINK_PROP_REPORT_METHOD = 'thing.event.property.post'; //标准ALink JSON格式topic， 设备 上传属性数据到 云端
        var ALINK_PROP_SET_METHOD = 'thing.service.property.set';
        function rawDataToProtocol(bytes) {
            var uint8Array = new Uint8Array(bytes.length);
            for (var i = 0; i < bytes.length; i++) {
                uint8Array[i] = bytes[i] & 0xff;
            }
            var dataView = new DataView(uint8Array.buffer, 0);
            var jsonMap = new Object();
            var fHead = uint8Array[0]; // 第0个BYTE为上报协议
            if (fHead == COMMAND_REPORT) {
                jsonMap['method'] = ALINK_PROP_REPORT_METHOD; //ALink JSON格式 - 属性上报topic
                jsonMap['version'] = '1.0'; //ALink JSON格式 - 协议版本号固定字段
                jsonMap['id'] = '' + 12345; //ALink JSON格式 - 标示该次请求id值
                var params = {};
                params['IndoorHumanDetectionSwitch'] = uint8Array[1]; //第1个BYTE为传感器读数判断有没有人
                params['SensorProperty'] = uint8Array[2]; //第2个BYTE为传感器本身的状态，对应产品属性中 prop_float
                jsonMap['params'] = params; //ALink JSON格式 - params标准字段
            }
            return jsonMap;
        ```

    3.  输入原始数据020100进行调试，可以看到右边解析成功，然后单击页面下方的**执行**即可让脚本生效。

        ![脚本生效](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84228.png)

        在日志里可以看到二进制的020100已经转为`{"SensorProperty":0,"IndoorHumanDetectionSwitch":1}`，表示已完成设备接入。

        ![日志服务_二进制转化成功](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0588509951/p84237.png)


## 在IoT Studio上配置智能厕所看板

IoT Studio（原Link Develop）是阿里云针对物联网场景提供的生产力工具，可覆盖各个物联网行业核心应用场景，解决物联网开发领域开发链路长、技术栈复杂、协同成本高、方案移植困难的问题。入口在[物联网平台控制台](https://iot.console.aliyun.com/)左侧导航栏上的**IoT Studio**项。

1.  在IoT Studio上新建一个项目，以项目维度管理我们的智能厕所应用。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430249243/18.gif)

2.  创建项目之后可以看到右边栏多了一项**SmartToilet**，单击**查看**进入项目详情。然后在项目概览页单击右上角**导入产品**，把刚才创建的产品导入到项目内。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430249243/18.gif)

3.  在左侧栏上选择**推荐** \> **Web可视化开发**，单击**新建应用**进入Web可视化开发工作台，然后选择空白模板进行新建。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430267522/19.gif)

4.  进入编辑中，可以改变背景色，添加标题文字等。对最重要的厕所占位状态，可以理解为一个“有人”、“没人”的指示灯，因此把指示灯组件放入画布中，并配置数据源。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430295099/20.gif)

5.  配置数据源时，请选择产品、关联的设备以及关联的布尔型属性。单击**验证数据格式**获得通过，之后单击**确定**完成配置。配置之后可以通过上传图片等修改指示灯开关状态的样式。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430322917/21.gif)

6.  单击**预览**，完成整个Web应用的链路调试。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430349094/22.gif)

7.  假设有7个坑位，只需要重复上述步骤即可（可以使用上传excel格式批量添加设备）。另外GUI配置的部分与之前的版本操作一致，在此不再赘述。最终效果如下图所示。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430382260/23.png)


## 在IoT Studio上配置智能厕所状态推送&转储

服务开发（原服务编排）可以通过可视化拖拽的方式快速完成所需业务逻辑的设计，例如，设备联动、可视化搭建数据联动、云服务连接、API 生成、数据处理与转储、生成App的后端服务。在本文中，我们要使用服务开发完成智能厕所坑位状态的推送，以及把厕所使用状况转储到表格存储Table Store上。

1.  在IoT Studio上新建一个服务。

    从项目概览页选择**推荐** \> **服务开发**，单击**新建服务**即可进入服务开发工作台的新建页面，选择空白模板进行新建。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430406143/24.gif)

2.  把厕所的占用时间推送到钉钉机器人上。

    首先配置一个**设备触发**节点作为输入，选择之前创建好的产品，**设备选择**选择**所有设备**，以监听所有设备上报的信息。**上报类型**选择**属性上报**，最后配置一个钉钉机器人节点作为消息推送节点。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430440767/25.gif)

3.  在要推送的钉钉群内添加机器人，获得webhook，如下图所示。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430459048/26.gif)

4.  配置webhook以后可以配置推送的信息。钉钉机器人节点目前支持多种消息推送类型，并且支持动态调用设备数据。

    框内配置项如下：

    ```
    {
      "msgtype": "text", 
      "text": {
        "content":"在{{query.props.IndoorHumanDetectionSwitch.time}}时候有{{query.props.IndoorHumanDetectionSwitch.value}}人进坑！"
     }, 
      "at": {
          "isAtAll": true
      }
    }
    						
    ```

5.  配置完成之后，单击**部署**对服务进行部署。然后单击**启动**让服务生效。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430532355/28.gif)

    如果设备已经上线，则可以直接看到机器人的消息推送，实现厕所使用状态的实时推送了，如下图所示。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430550743/29.gif)

6.  如果需要把厕所的使用状况使用TableStore，云数据库MySQL等云产品存储起来，可以使用存储节点。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430580669/30.gif)

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430599694/31.png)

    最终结果如图：

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430632714/32.png)


## 结语

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/107069/cn_zh/1551430687620/33.jpeg)


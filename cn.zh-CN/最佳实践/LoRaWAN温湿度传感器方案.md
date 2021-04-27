# LoRaWAN温湿度传感器方案

本文提供LoRaWAN温湿度传感器通过**Link WAN**接入，同时采用**阿里云物联网平台**实现端到端应用的方案。

-   开通物联网络管理平台

    完成账号的注册之后，使用账号登录[Link WAN](https://linkwan.console.aliyun.com/) 开通服务。

    ![开通后首页](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1408891851/p83370.png)

-   LoRa节点设备接入
-   搭建与管理网络

    参见[搭建与管理网络](/cn.zh-CN/快速入门/搭建与管理网络.md)搭建和管理网络、创建节点组并添加节点。

-   配置数据流转

    目前数据流转支持阿里云物联网平台、消息队列MQ两种方式，这里选择将数据流转至阿里云物联网平台，详情请参见[数据接入物联网平台-1对1](/cn.zh-CN/云端开发指南/数据接入物联网平台-1对1.md)。

-   物联网平台LoRa节点设备接入

    本章介绍如何在物联网平台开发平台上进行设备接入的开发。主要的开发内容包括：

    -   创建产品和设备
    -   产品功能定义
    -   平台脚本开发

本文以一个空气温湿度传感器为例，同时可以配置温湿度的阈值，在温湿度超出阈值时上报事件。

## 创建产品和设备

1.  登录[物联网平台控制台](https://iot.console.aliyun.com/)。

2.  在**实例概览**页面，找到对应的实例，单击实例进入**实例详情**页面。

3.  在左侧导航栏上选择**设备管理** \> **产品**，单击**创建产品**， 填写产品信息后单击**确认**。详情请参见[数据接入物联网平台-1对1](/cn.zh-CN/云端开发指南/数据接入物联网平台-1对1.md)。

    ![创建LoRa设备的产品](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6086059161/p83388.png)

    |参数|描诉|
    |--|--|
    |产品名称|可填写任意名称|
    |所属品类|自定义品类|
    |节点类型|直连设备|
    |连网方式|LoRaWAN|
    |入网凭证|从表单选择。如无，可单击**创建凭证**|
    |数据格式|透传/自定义|

4.  为产品添加LoRa设备。

    在左侧导航栏上单击**设备**，参见[单个创建设备](/cn.zh-CN/设备接入/创建设备/单个创建设备.md)添加设备。

    ![添加LoRa设备](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6086059161/p83431.png)

    **说明：** 使用LoRaWAN设备的DevEUI需小写作为DeviceName。

    -   添加完成后，显示如下，此时设备状态为**未激活**。

        ![未激活](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2408891851/p83433.png)

    -   数据流转已自动同步。

        产品创建完成后，可在Link WAN里看到自动同步的数据流转设置。

        ![数据流转自动同步](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7086059161/p83435.png)

        **说明：** 在网管平台只能查阅，新增终端请移步至物联网平台维护。


## 产品功能定义

产品创建完成之后，需要在平台上定义产品有哪些功能。功能定义是为了让平台能够理解设备上下行的数据定义，便于上层应用的读写。

1.  在左侧导航栏上选择**设备管理** \> **产品**，单击产品对应**操作**栏中的**查看**。

2.  选择**功能定义** \> **编辑草稿**，单击**添加自定义功能**。

3.  在添加自定义功能弹框中，**功能类型**选择**属性**，添加温湿度属性。

    -   添加温度属性，配置参数如下图所示。

        ![添加温度属性](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2408891851/p83444.png)

    -   添加湿度属性，配置参数如下图所示。

        ![添加湿度属性](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2408891851/p83445.png)

4.  **功能类型**选择**服务**，添加温度湿度阈值，参数配置如下图所示。

    ![温度湿度阈值](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2408891851/p83446.png)

    其中输入参数设置如下图所示。

    ![输入参数设置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2408891851/p83454.png)

    |参数名称|标志符|数据类型|取值范围|步长|单位|
    |----|---|----|----|--|--|
    |温度过高阈值|MaxTemp|int32（整数型）|-40~55|1|摄氏度/℃|
    |温度过低阈值|MinTemp|int32（整数型）|40~55|1|摄氏度/℃|
    |湿度过高阈值|MaxHumi|int32（整数型）|1~100|1|百分比/%|
    |湿度过低阈值|MinHumi|int32（整数型）|1~100|1|百分比/%|

5.  **功能类型**选择**事件**，添加湿度过高／过低告警事件。告警输出参数为当前湿度。

    ![湿度异常告警事件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3408891851/p83463.png)

    其中输出参数设置如下。

    ![输出参数设置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3408891851/p83469.png)

6.  单击**确认**，单击页面左下方的**发布更新**。

    上述属性、服务、事件添加完成后，在自定义功能一栏下方可确认添加的结果。

    ![功能定义结果](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3408891851/p83481.png)


## 平台脚本开发

1.  进入**产品**的**数据解析**标签页，可以添加解析脚本。由于数据是以自定义格式透传到平台，所以需要添加脚本来解析自定义协议。

    ![产品-数据解析](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7086059161/p181676.png)

2.  将下列代码添加到上图的**脚本编辑区**。

    ```
    var ALINK_ID = "12345";
    var ALINK_VERSION = "1.1";
    var ALINK_PROP_POST_METHOD     = 'thing.event.property.post';
    var ALINK_EVENT_TEMPERR_METHOD = 'thing.event.TempError.post';
    var ALINK_EVENT_HUMIERR_METHOD = 'thing.event.HumiError.post';
    var ALINK_PROP_SET_METHOD      = 'thing.service.property.set';
    var ALINK_SERVICE_THSET_METHOD = 'thing.service.SetTempHumiThreshold';
    /*
     * 示例数据：
     *  传入参数 ->
     *      000102 // 共3个字节
     *  输出结果 ->
     *      {"method":"thing.event.property.post", "id":"12345", "params":{"Temperature":1,"Humidity":2}, "version":"1.1"}
     *  传入参数 ->
     *      0102 // 共2个字节
     *  输出结果 ->
     *      {"method":"thing.event.TempError.post","id":"12345","params":{"Temperature":2},"version":"1.1"}
     *  传入参数 ->
     *      0202 // 共2个字节
     *  输出结果 ->
     *     {"method":"thing.event.HumiError.post","id":"12345","params":{"Humidity":2},"version":"1.1"}
     */
    function rawDataToProtocol(bytes)
    {
        var uint8Array = new Uint8Array(bytes.length);
        for (var i = 0; i < bytes.length; i++)
        {
            uint8Array[i] = bytes[i] & 0xff;
        }
        var params = {};
        var jsonMap = {};
        var dataView = new DataView(uint8Array.buffer, 0);
        var cmd = uint8Array[0]; // command
        if (cmd === 0x00)
        {
            params['Temperature']  = dataView.getInt8(1); 
            params['Humidity']     = dataView.getInt8(2); 
            jsonMap['method']  = ALINK_PROP_POST_METHOD;
        }
        else if (cmd == 0x01)
        {
            params['Temperature']  = dataView.getInt8(1); 
            jsonMap['method']  = ALINK_EVENT_TEMPERR_METHOD;
        }
        else if (cmd == 0x02)
        {
            params['Humidity']  = dataView.getInt8(1); 
            jsonMap['method']  = ALINK_EVENT_HUMIERR_METHOD;
        }
        else
        {
            return null;
        }
        jsonMap['version'] = ALINK_VERSION;
        jsonMap['id']      = ALINK_ID; 
        jsonMap['params']  = params;
        return jsonMap;
    }
    /*
     * 示例数据：
     *  传入参数 ->
     *      {"method":"thing.service.SetTempHumiThreshold", "id":"12345", "version":"1.1", "params":{"MaxTemp":50, "MinTemp":8, "MaxHumi":90, "MinHumi":10}}
     *  输出结果 ->
     *      0x5d0a000332085a0a
     */
    function protocolToRawData(json)
    {
        var id  = json['id'];
        var method  = json['method'];
        var version = json['version'];
        var payloadArray = [];
        // 追加下行帧头部
        payloadArray = payloadArray.concat(0x5d);
        payloadArray = payloadArray.concat(0x0a);
        payloadArray = payloadArray.concat(0x00);
    
        if (method == ALINK_SERVICE_THSET_METHOD)
        {
            var params  = json['params'];
            var maxtemp = params['MaxTemp'];
            var mintemp = params['MinTemp'];
            var maxhumi = params['MaxHumi'];
            var minhumi = params['MinHumi'];
    
            payloadArray = payloadArray.concat(0x03);
            if (maxtemp !== null)
            {
                payloadArray = payloadArray.concat(maxtemp);
            }
            if (mintemp !== null)
            {
                payloadArray = payloadArray.concat(mintemp);
            }
            if (maxhumi !== null)
            {
                payloadArray = payloadArray.concat(maxhumi);
            }
            if (minhumi !== null)
            {
                payloadArray = payloadArray.concat(minhumi);
            }
        }
        return payloadArray;
    }
    // 以下是部分辅助函数
    function buffer_uint8(value)
    {
        var uint8Array = new Uint8Array(1);
        var dv = new DataView(uint8Array.buffer, 0);
        dv.setUint8(0, value);
        return [].slice.call(uint8Array);
    }
    function buffer_int16(value)
    {
        var uint8Array = new Uint8Array(2);
        var dv = new DataView(uint8Array.buffer, 0);
        dv.setInt16(0, value);
        return [].slice.call(uint8Array);
    }
    function buffer_int32(value)
    {
        var uint8Array = new Uint8Array(4);
        var dv = new DataView(uint8Array.buffer, 0);
        dv.setInt32(0, value);
        return [].slice.call(uint8Array);
    }
    function buffer_float32(value)
    {
        var uint8Array = new Uint8Array(4);
        var dv = new DataView(uint8Array.buffer, 0);
        dv.setFloat32(0, value);
        return [].slice.call(uint8Array);
    }
    ```

    脚本解析下行数据的函数protocolToRawData中必须设定输出结果的起始三个字节（用于指定下行的端口号以及下行消息类型），否则系统会丢掉下行帧。另外，节点实际接收到的数据将不会包含起始的三个字节。

    起始三字节的说明如下表所示。

    |Size（bytes）|LoRa Downlink|描述|
    |-----------|-------------|--|
    |1|DFlag|固定为0x5D|
    |1|FPort|下行端口号|
    |1|DHDR|    -   0表示 “Unconfirmed Data Down”数据帧
    -   1表示 “Confirmed Data Down”数据帧 |

    示例：`0x5D 0x0A 0x00`表示：下行帧端口号为10，数据帧为Unconfirmed Data Down。

3.  脚本模拟运行。

    1.  设备上报数据调试。

        在**脚本调试区1**里输入下面数据，**模拟类型**选择**设备上报数据**后，单击**运行**按钮。

        ![设备上报数据](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3408891851/p83487.png)

        **说明：** 000102中的00表示后面的两个字节分别表示温度和湿度，01表示温度为1摄氏度，02表示湿度为2%。

    2.  设备接收数据调试。

        在**脚本调试区1**里输入以下数据，**模拟类型**选择**设备接收数据**后，单击**运行**按钮。

        ```
        {
            "method": "thing.service.SetTempHumiThreshold",
            "id": "12345",
            "version": "1.1",
            "params": {
                "MaxTemp": 50,
                "MinTemp": 8,
                "MaxHumi": 90,
                "MinHumi": 10
            }
        }
        ```

        ![接受数据](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3408891851/p83497.png)

        查看**脚本调试区2**的运行结果如下：

        ![基本调试区结果_接收](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4408891851/p83502.png)

4.  脚本调试无误后，单击**提交**按钮提交脚本。


## 设备在线调试

脚本提交后，可以结合节点测试数据的上下行链路是否打通，LoRa节点如何发送以及接收数据请参考各模组厂商的相关手册。

1.  节点数据上行。

    1.  上报温湿度属性。

        1.  在LoRa节点侧选择输入十六进制的000102后发送数据。
        2.  从左侧导航栏的**设备** \> **设备列表**选择对应节点，单击**查看**。
        3.  在**设备详情**页面选择**物模型数据** \> **运行状态**。

            ![设备运行状态页面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8086059161/p88052.jpg)

        4.  确认节点的湿度与温度信息是否已经上报且设置如下。

            ![温度](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4408891851/p83512.png)

            ![湿度](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4408891851/p83513.png)

    2.  上报温湿度告警事件。

        -   温度告警事件上报
            1.  在LoRa节点侧选择输入十六进制的0102后发送数据。
            2.  在**设备详情** \> **事件管理**中确认温度告警事件是否已经上报。

                ![事件上报](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4408891851/p83515.png)

        -   湿度告警事件上报
            1.  在LoRa节点侧选择输入十六进制的0202后发送数据。
            2.  在**设备详情** \> **事件管理**中确认湿度告警事件是否已经上报。

                ![湿度事件上报](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4408891851/p83518.png)

2.  节点数据下行。

    1.  在**产品详情** \> **设备开发**，单击对应节点的**调试**按钮，进入**在线调试**页面。

    2.  选择调试功能为之前添加的温度湿度阈值，具体格式如下所示，单击发送指令。

        ![在线调试](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4408891851/p83523.png)

        发送完成后在节点侧确认输出是否是16进制的`0332085a0a`。


**说明：** 对于Class A类型的节点，需要先发送数据才能启动接收。

## 固件升级

LoRa节点设备可以通过本地端烧录方式升级固件，目前不支持网络在线升级（FUOTA）。

